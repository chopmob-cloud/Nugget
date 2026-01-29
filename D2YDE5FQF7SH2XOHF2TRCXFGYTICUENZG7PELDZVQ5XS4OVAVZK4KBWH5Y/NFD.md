import json
import requests
from collections import defaultdict

INDEXER_URL = "https://mainnet-idx.algonode.cloud"
NUGGET_ASA_ID = 2699078351

HEADERS = {"User-Agent": "nugget-nfd-analysis"}

# -----------------------------
# STEP 1: extract wallets that touched NUGGET
# -----------------------------
def extract_wallets(tx):
    wallets = set()

    if "sender" in tx:
        wallets.add(tx["sender"])

    if "asset-transfer-transaction" in tx:
        wallets.add(tx["asset-transfer-transaction"].get("receiver"))
        wallets.add(tx["asset-transfer-transaction"].get("close-to"))

    if "payment-transaction" in tx:
        wallets.add(tx["payment-transaction"].get("receiver"))

    for inner in tx.get("inner-txns", []):
        wallets |= extract_wallets(inner)

    return {w for w in wallets if w}


def wallets_that_touched_nugget(transactions):
    wallets = set()

    for tx in transactions:
        axfer = tx.get("asset-transfer-transaction")
        if axfer and axfer.get("asset-id") == NUGGET_ASA_ID:
            wallets |= extract_wallets(tx)

    return wallets


# -----------------------------
# STEP 2: resolve NFDs via Indexer
# -----------------------------
def get_nfds_for_wallet(wallet):
    """
    Returns list of NFD names owned by this wallet
    """
    nfds = []

    url = f"{INDEXER_URL}/v2/accounts/{wallet}/assets"
    r = requests.get(url, headers=HEADERS, timeout=10)
    r.raise_for_status()

    for asset in r.json().get("assets", []):
        asset_id = asset["asset-id"]

        # Fetch asset metadata
        meta_url = f"{INDEXER_URL}/v2/assets/{asset_id}"
        meta = requests.get(meta_url, headers=HEADERS, timeout=10).json()

        params = meta.get("asset", {}).get("params", {})
        name = params.get("name", "")

        # NFD heuristic: ".algo" domain in asset name
        if name.endswith(".algo"):
            nfds.append(name)

    return nfds


# -----------------------------
# MAIN
# -----------------------------
if __name__ == "__main__":
    with open("transactions.json", "r") as f:
        transactions = json.load(f)

    nugget_wallets = wallets_that_touched_nugget(transactions)

    wallet_to_nfds = defaultdict(list)

    for wallet in sorted(nugget_wallets):
        try:
            nfds = get_nfds_for_wallet(wallet)
            if nfds:
                wallet_to_nfds[wallet].extend(nfds)
        except Exception as e:
            print(f"⚠️  Failed to fetch NFDs for {wallet}: {e}")

    print("\nWallets that interacted with NUGGET and own NFDs:\n")
    for wallet, nfds in wallet_to_nfds.items():
        print(wallet)
        for nfd in nfds:
            print(f"  - {nfd}")

