#!/usr/bin/env python3
"""
owner_other_asas.py

Given:
  - NFD names (e.g., alice.algo) and/or wallet addresses
Do:
  - Resolve each NFD -> owner address (NFD API)
  - For each owner address, list ALL opted-in ASAs and balances (Indexer)
  - Optionally enrich each ASA with asset params (name/unit/decimals/creator)
Output:
  - Prints to stdout
  - Optionally writes CSV

Requirements:
  pip install py-algorand-sdk requests

Notes:
  - Uses public NFD API: https://api.nf.domains  (GET /nfd/{name})  :contentReference[oaicite:2]{index=2}
  - Uses Algorand Indexer REST via SDK. :contentReference[oaicite:3]{index=3}
"""

from __future__ import annotations

import argparse
import csv
import re
import sys
import time
from dataclasses import dataclass
from typing import Dict, Iterable, List, Optional, Set, Tuple

import requests
from algosdk.v2client import indexer as algo_indexer


NFD_API_BASE = "https://api.nf.domains"

# A lightweight heuristic; for strict validation you can use algosdk.encoding.is_valid_address
ADDR_RE = re.compile(r"^[A-Z2-7]{58}$")


@dataclass(frozen=True)
class HoldingRow:
    input_id: str              # what user provided (nfd or address)
    owner_address: str         # resolved owner address
    asset_id: int
    amount_raw: int            # base units
    amount: float              # human units (raw / 10**decimals)
    decimals: int
    asset_name: str
    unit_name: str
    creator: str
    is_frozen: bool


def is_probably_address(s: str) -> bool:
    return bool(ADDR_RE.match(s.strip().upper()))


def is_probably_nfd(s: str) -> bool:
    s = s.strip().lower()
    return s.endswith(".algo") or s.endswith(".test") or s.endswith(".betanet") or "." in s


def read_lines(path: str) -> List[str]:
    out: List[str] = []
    with open(path, "r", encoding="utf-8") as f:
        for line in f:
            line = line.strip()
            if not line or line.startswith("#"):
                continue
            out.append(line)
    return out


def resolve_nfd_to_owner(nfd_name: str, timeout_s: int = 20) -> str:
    """
    Resolve an NFD name to its owner address using NFD API:
      GET /nfd/{nameOrID}  (we pass the name)
    Returns the 'owner' field. :contentReference[oaicite:4]{index=4}
    """
    url = f"{NFD_API_BASE}/nfd/{nfd_name}"
    r = requests.get(url, timeout=timeout_s)
    if r.status_code == 404:
        raise ValueError(f"NFD not found: {nfd_name}")
    r.raise_for_status()
    data = r.json()
    owner = data.get("owner")
    if not owner or not isinstance(owner, str):
        raise ValueError(f"Could not read owner for NFD {nfd_name}: {data}")
    return owner


def make_indexer_client(indexer_url: str, indexer_token: str = "") -> algo_indexer.IndexerClient:
    # SDK expects token + address. Token often blank for public endpoints. :contentReference[oaicite:5]{index=5}
    headers = {}
    return algo_indexer.IndexerClient(indexer_token=indexer_token, indexer_address=indexer_url, headers=headers)


def iter_account_assets(ix: algo_indexer.IndexerClient, address: str, limit: int = 1000) -> Iterable[dict]:
    """
    Yield asset holding objects from Indexer with pagination.

    Uses lookup_account_assets() which wraps Indexer REST pagination.
    """
    next_token: Optional[str] = None
    while True:
        resp = ix.lookup_account_assets(address, limit=limit, next_page=next_token)
        assets = resp.get("assets", []) or []
        for a in assets:
            yield a
        next_token = resp.get("next-token")
        if not next_token:
            break


def fetch_asset_params(ix: algo_indexer.IndexerClient, asset_id: int) -> dict:
    """
    Fetch asset params (name/unit/decimals/creator) from Indexer.
    """
    resp = ix.lookup_asset_by_id(asset_id)
    asset = resp.get("asset", {}) or {}
    params = asset.get("params", {}) or {}
    return params


def get_holdings_for_owner(
    ix: algo_indexer.IndexerClient,
    input_id: str,
    owner_addr: str,
    exclude_asset_ids: Set[int],
    min_amount_raw: int,
    enrich: bool,
    asset_params_cache: Dict[int, dict],
    sleep_s: float = 0.0,
) -> List[HoldingRow]:
    rows: List[HoldingRow] = []

    for holding in iter_account_assets(ix, owner_addr):
        asset_id = int(holding.get("asset-id"))
        if asset_id in exclude_asset_ids:
            continue

        amount_raw = int(holding.get("amount", 0))
        if amount_raw < min_amount_raw:
            continue

        is_frozen = bool(holding.get("is-frozen", False))

        if enrich:
            if asset_id not in asset_params_cache:
                if sleep_s:
                    time.sleep(sleep_s)
                asset_params_cache[asset_id] = fetch_asset_params(ix, asset_id)
            params = asset_params_cache[asset_id]
            decimals = int(params.get("decimals", 0) or 0)
            asset_name = str(params.get("name", "") or "")
            unit_name = str(params.get("unit-name", "") or "")
            creator = str(params.get("creator", "") or "")
        else:
            decimals = 0
            asset_name = ""
            unit_name = ""
            creator = ""

        amount = amount_raw / (10 ** decimals) if decimals else float(amount_raw)

        rows.append(
            HoldingRow(
                input_id=input_id,
                owner_address=owner_addr,
                asset_id=asset_id,
                amount_raw=amount_raw,
                amount=amount,
                decimals=decimals,
                asset_name=asset_name,
                unit_name=unit_name,
                creator=creator,
                is_frozen=is_frozen,
            )
        )

    return rows


def parse_args() -> argparse.Namespace:
    p = argparse.ArgumentParser(description="List other ASAs held by NFD owners / wallet list.")
    p.add_argument("--indexer", required=True, help="Indexer base URL, e.g. https://mainnet-idx.algonode.cloud")
    p.add_argument("--indexer-token", default="", help="Indexer API token (usually blank for public endpoints)")
    p.add_argument("--wallet", action="append", default=[], help="Wallet address (repeatable)")
    p.add_argument("--wallets-file", help="File with one wallet/NFD per line")
    p.add_argument("--nfd", action="append", default=[], help="NFD name (repeatable), e.g. alice.algo")
    p.add_argument("--exclude", action="append", default=[], help="Asset ID to exclude (repeatable), e.g. 2699078351")
    p.add_argument("--min-raw", type=int, default=1, help="Minimum raw amount (base units) to include (default 1)")
    p.add_argument("--no-enrich", action="store_true", help="Skip fetching asset params (faster, less calls)")
    p.add_argument("--sleep", type=float, default=0.0, help="Sleep seconds between asset param lookups (rate-limit help)")
    p.add_argument("--csv", help="Write output to CSV path")
    return p.parse_args()


def main() -> int:
    args = parse_args()

    exclude_asset_ids: Set[int] = {int(x) for x in args.exclude}

    inputs: List[str] = []
    inputs.extend(args.wallet)
    inputs.extend(args.nfd)
    if args.wallets_file:
        inputs.extend(read_lines(args.wallets_file))

    if not inputs:
        print("No inputs provided. Use --wallet, --nfd, or --wallets-file.", file=sys.stderr)
        return 2

    ix = make_indexer_client(args.indexer, args.indexer_token)

    # Resolve each input -> owner address (if NFD) or itself (if address)
    resolved: List[Tuple[str, str]] = []
    for item in inputs:
        item = item.strip()
        if not item:
            continue

        if is_probably_address(item):
            resolved.append((item, item))
        elif is_probably_nfd(item):
            try:
                owner = resolve_nfd_to_owner(item)
            except Exception as e:
                print(f"[WARN] Could not resolve NFD {item}: {e}", file=sys.stderr)
                continue
            resolved.append((item, owner))
        else:
            print(f"[WARN] Unrecognized input (not address or NFD-ish): {item}", file=sys.stderr)

    if not resolved:
        print("Nothing resolved; exiting.", file=sys.stderr)
        return 1

    enrich = not args.no_enrich
    asset_params_cache: Dict[int, dict] = {}

    all_rows: List[HoldingRow] = []
    for input_id, owner_addr in resolved:
        try:
            rows = get_holdings_for_owner(
                ix=ix,
                input_id=input_id,
                owner_addr=owner_addr,
                exclude_asset_ids=exclude_asset_ids,
                min_amount_raw=args.min_raw,
                enrich=enrich,
                asset_params_cache=asset_params_cache,
                sleep_s=args.sleep,
            )
            all_rows.extend(rows)
        except Exception as e:
            print(f"[WARN] Failed fetching holdings for {owner_addr} (from {input_id}): {e}", file=sys.stderr)

    # Print summary
    print(f"Resolved inputs: {len(resolved)}")
    print(f"Holdings rows:   {len(all_rows)}")
    print()

    # Pretty print (basic)
    for r in sorted(all_rows, key=lambda x: (x.owner_address, x.asset_id)):
        meta = ""
        if enrich:
            meta = f"{r.asset_name} ({r.unit_name}) dec={r.decimals} creator={r.creator}"
        print(f"{r.input_id} -> {r.owner_address} | ASA {r.asset_id} | amt={r.amount} raw={r.amount_raw} frozen={r.is_frozen} {meta}")

    # CSV output
    if args.csv:
        fieldnames = [
            "input_id",
            "owner_address",
            "asset_id",
            "amount",
            "amount_raw",
            "decimals",
            "asset_name",
            "unit_name",
            "creator",
            "is_frozen",
        ]
        with open(args.csv, "w", newline="", encoding="utf-8") as f:
            w = csv.DictWriter(f, fieldnames=fieldnames)
            w.writeheader()
            for r in all_rows:
                w.writerow({
                    "input_id": r.input_id,
                    "owner_address": r.owner_address,
                    "asset_id": r.asset_id,
                    "amount": r.amount,
                    "amount_raw": r.amount_raw,
                    "decimals": r.decimals,
                    "asset_name": r.asset_name,
                    "unit_name": r.unit_name,
                    "creator": r.creator,
                    "is_frozen": r.is_frozen,
                })
        print(f"\nWrote CSV: {args.csv}")

    return 0


if __name__ == "__main__":
    raise SystemExit(main())
