#!/usr/bin/env python3
"""
creator_nft_projects.py

Given:
  - NFD names and/or wallet addresses

Do:
  - Resolve NFD -> owner wallet
  - Find ASAs CREATED by that wallet (Indexer)
  - Classify assets as fungible vs NFT-like
  - Group NFTs into probable NFT projects

Requirements:
  pip install py-algorand-sdk requests
"""

from __future__ import annotations

import argparse
import csv
import re
import sys
from collections import defaultdict
from dataclasses import dataclass
from typing import Dict, List, Optional, Tuple

import requests
from algosdk.v2client import indexer as algo_indexer


NFD_API = "https://api.nf.domains"


# -------------------- models --------------------

@dataclass
class CreatedAsset:
    creator: str
    asset_id: int
    name: str
    unit: str
    total: int
    decimals: int
    url: str
    metadata_hash: str
    is_nft: bool
    project_key: str


# -------------------- helpers --------------------

def
