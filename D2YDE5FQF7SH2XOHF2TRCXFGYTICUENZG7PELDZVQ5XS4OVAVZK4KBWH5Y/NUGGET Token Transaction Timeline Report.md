# NUGGET Token Transaction Timeline Report - Wallet 6

**Asset ID:** 2699078351  
**Wallet Address:** `D2YDE5FQF7SH2XOHF2TRCXFGYTICUENZG7PELDZVQ5XS4OVAVZK4KBWH5Y`  
**Period:** January 28, 2026 (Single Day)  
**Batch Position:** 2nd of 3 (Middle)  
**Report Generated:** January 28, 2026

---

## 🔍 Key Counterparties

### 1. 🟢 Smart Contract Address
**Address:** `ZLMXPKLRYPF6MT3VCI5JRTOG6ADFIWBL5D4MGYYYLKHGW6E333K4P4WTVM`
- **Role:** Smart contract that executed the NUGGET transfer
- **Transaction:** 1 inner transaction
- **Total sent:** 100,000,000 NUGGET
- **Pattern:** Automated contract execution (inner transaction)

### 2. 🔵 Contract Caller
**Address:** `53LJLQATA34TUZRWPYQJXGRDDZIW4T3MXEQ455VFTASI5PSWXMBNN2R424`
- **Role:** Initiated the smart contract call
- **Application ID:** 2650568591
- **Fee Paid:** 0.002000 ALGO
- **Pattern:** Triggered the contract that sent NUGGET

---

## Executive Summary

- **Total Transactions:** 2 (1 opt-in + 1 smart contract transfer)
- **Total NUGGET Received:** 100,000,000
- **Total NUGGET Sent:** 0
- **Net Change:** +100,000,000 NUGGET
- **Current Balance:** 100,000,000 NUGGET ✅
- **Distribution Method:** Smart Contract Inner Transaction
- **Batch Position:** **Middle recipient** (2 of 3 in sequential distribution)

---

## Transaction Timeline

### Transaction #1: Asset Opt-In 🔓
**Date:** January 28, 2026 at 16:41:18 UTC

| Detail | Value |
|--------|-------|
| **Type** | **ASSET OPT-IN** |
| **From** | `D2YDE5FQF7SH2XOHF2TRCXFGYTICUENZG7PELDZVQ5XS4OVAVZK4KBWH5Y` |
| **To** | `D2YDE5FQF7SH2XOHF2TRCXFGYTICUENZG7PELDZVQ5XS4OVAVZK4KBWH5Y` (self) |
| **Amount** | **0 NUGGET** |
| **Fee** | 0.001000 ALGO |
| **Block Round** | 57864406 |
| **Transaction ID** | `F4J7GQ3BKSOCBHRI4IWTCCM4TT33JDMQGNZTQWYJGZMWEKHM2UGA` |

**Summary:** The wallet opted into the NUGGET asset to prepare for receiving tokens. This is a mandatory step on Algorand before any wallet can receive an ASA (Algorand Standard Asset).

**Algorand Requirement:** The opt-in creates a holding slot for the asset and signals the wallet's intention to receive this specific token.

---

### Transaction #2: Smart Contract Transfer (Inner Transaction) 💻
**Date:** January 28, 2026 at 16:41:49 UTC (31 seconds later)

| Detail | Value |
|--------|-------|
| **Type** | 🟢 **INCOMING (via Smart Contract)** |
| **From** | 🟢 **Smart Contract**<br>`ZLMXPKLRYPF6MT3VCI5JRTOG6ADFIWBL5D4MGYYYLKHGW6E333K4P4WTVM` |
| **To** | `D2YDE5FQF7SH2XOHF2TRCXFGYTICUENZG7PELDZVQ5XS4OVAVZK4KBWH5Y` |
| **Amount** | **100,000,000 NUGGET** 🎯 |
| **Fee** | 0.000000 ALGO (inner transaction - no fee) |
| **Block Round** | 57864417 |
| **Parent Transaction ID** | `WDXPKG4XI5NTY7BIAIO6XIJXNPBRJQ5JYBV2HFDEXFNREHRKRO4Q` |

**Summary:** The wallet received exactly 100,000,000 NUGGET through a smart contract inner transaction 31 seconds after opting in. This was part of an automated batch distribution campaign.

**Smart Contract Details:**
- **Application ID:** 2650568591
- **Contract Caller:** `53LJLQAT...`
- **Caller Fee:** 0.002000 ALGO
- **Mechanism:** Inner transaction (contract-generated transfer)
- **Batch Position:** 2nd of 3 wallets

---

## Batch Distribution Context

### This Wallet's Position in the Sequence

```
BATCH DISTRIBUTION TIMELINE
═══════════════════════════════════════════════════════════════

16:40:35 UTC                16:41:49 UTC                16:42:41 UTC
     │                           │                           │
     │                           │                           │
  Wallet 5                  WALLET 6 ⭐               Wallet 4
 (X6HSG...)                (D2YDE...)                (MNRLT...)
100,000,000              100,000,000               100,000,047
  NUGGET                    NUGGET                    NUGGET
     │                           │                           │
     └─────── 74 sec ────────────┘                           │
                                 └────── 52 sec ──────────────┘

Total Batch: 300,000,047 NUGGET
Duration: 2 minutes 6 seconds
Recipients: 3 wallets
```

### Timing Analysis

| Metric | Value |
|--------|-------|
| **Opt-In Time** | 16:41:18 UTC |
| **Receipt Time** | 16:41:49 UTC |
| **Opt-In Delay** | 31 seconds |
| **Time After Wallet 5** | 74 seconds |
| **Time Before Wallet 4** | 52 seconds |
| **Batch Position** | 2 of 3 (Middle) |

---

## Wallet Address Analysis

### Key Addresses Involved

#### 1. 📍 This Wallet (Tracked)
**Address:** `D2YDE5FQF7SH2XOHF2TRCXFGYTICUENZG7PELDZVQ5XS4OVAVZK4KBWH5Y`
- **Current Balance:** 100,000,000 NUGGET ✅
- **Activity:** Opted in, then received tokens
- **Total Assets:** 1 (only NUGGET)
- **Apps:** No applications opted into
- **Pattern:** Fresh wallet, second in batch sequence

#### 2. 🟢 Smart Contract Address
**Address:** `ZLMXPKLRYPF6MT3VCI5JRTOG6ADFIWBL5D4MGYYYLKHGW6E333K4P4WTVM`
- **Role:** Smart contract escrow/distribution address
- **Function:** Holds and distributes NUGGET via programmatic logic
- **Type:** Application escrow account
- **Controlled by:** Application ID 2650568591
- **Activity:** Distributed 300M+ NUGGET across multiple wallets

#### 3. 🔵 Contract Caller
**Address:** `53LJLQATA34TUZRWPYQJXGRDDZIW4T3MXEQ455VFTASI5PSWXMBNN2R424`
- **Role:** Triggered the smart contract executions
- **Action:** Called Application 2650568591 multiple times
- **Cost:** 0.002 ALGO per call
- **Likely:** Administrator, automated bot, or authorized distributor

#### 4. 🔗 Related Wallet (Wallet 5)
**Address:** `X6HSGRXUPK4O5E6M3KREDXWODVX7OR7XVLGT2565C4INA7SRUAKFRPYVTQ`
- **Received:** 100,000,000 NUGGET (74 seconds before this wallet)
- **Same pattern:** Opt-in + contract distribution
- **Link:** Received 0.5 ALGO from this wallet on Jan 23

---

## Transaction Flow Diagram

```
January 28, 2026 - 16:41 UTC
┌─────────────────────────────────────────────────────────────────┐
│                                                                   │
│  Step 1: Opt-In (16:41:18 UTC)                                  │
│  📍 WALLET → 📍 WALLET (self)                                    │
│  0 NUGGET (opt-in transaction)                                  │
│  Fee: 0.001 ALGO                                                │
│                                                                   │
│  ↓ (31 seconds later)                                           │
│                                                                   │
│  Step 2: Smart Contract Distribution (16:41:49 UTC)             │
│                                                                   │
│  🔵 Contract Caller → 💻 Smart Contract (Application Call)       │
│  Application ID: 2650568591                                      │
│  Fee: 0.002 ALGO                                                │
│                                                                   │
│  │                                                               │
│  └─→ 🟢 Smart Contract generates Inner Transaction:             │
│      100,000,000 NUGGET → 📍 WALLET                             │
│      (Automated transfer, no additional fee)                    │
│                                                                   │
└─────────────────────────────────────────────────────────────────┘

LEGEND:
📍 = This Wallet (D2YDE...)
🟢 = Smart Contract Address
🔵 = Contract Caller
💻 = Smart Contract Application
```

---

## Key Observations

### 1. **Middle Position in Sequential Batch** 🎯
This wallet was the second of three recipients in a coordinated distribution:
- **74 seconds** after Wallet 5
- **52 seconds** before Wallet 4
- Demonstrates sequential, not parallel, processing
- Controlled rollout with ~1-minute intervals

### 2. **Perfect Round Number: 100,000,000** 💯
Unlike Wallet 4 which received 100,000,047:
- Base amount: 100,000,000 (clean)
- No fractional units
- Suggests: Standard tier vs. Wallet 4's bonus/remainder

### 3. **Automated Precision** ⚡
- Opt-in to receipt: **31 seconds** (consistent with other batch wallets)
- Indicates: Bot monitoring opt-ins and triggering distributions
- Pattern: Pre-programmed execution sequence

### 4. **Pure Holder Pattern** 💎
Like other batch wallets:
- **No outgoing transactions**
- **100% balance retained**
- **No DeFi activity**
- Different from daily drop recipients who forward immediately

### 5. **Fresh Wallet Setup** 🆕
- Received 0.5 ALGO funding on Jan 23 (from Wallet 5)
- Opted into NUGGET on Jan 28
- Immediately received distribution
- Suggests: Pre-planned recipient list

---

## Comparison with Batch Peers

| Aspect | Wallet 5 (1st) | **This Wallet (2nd)** | Wallet 4 (3rd) |
|--------|----------------|----------------------|----------------|
| **Time** | 16:40:35 UTC | **16:41:49 UTC** | 16:42:41 UTC |
| **Amount** | 100,000,000 | **100,000,000** | 100,000,047 |
| **Opt-In Delay** | 26 seconds | **31 seconds** | 26 seconds |
| **Current Balance** | 100,000,000 | **100,000,000** ✅ | 100,000,047 |
| **Funding** | From others | **From Wallet 5** | From caller |
| **Special** | Batch opener | **Middle** | Bonus +47 |

---

## Comparison with All Tracked Wallets

| Wallet | Type | Amount Received | Current Balance | Method |
|--------|------|----------------|-----------------|--------|
| 1 (2RXI...) | Daily Drop | 198,020,003 | 0 | Direct |
| 2 (5DJPQ...) | Daily Drop | 128,000,000 | 0 | Direct |
| 3 (dystopia.algo) | Daily Drop | 132,353,878 | 63,749 | Direct |
| 4 (MNRLT...) | Contract | 100,000,047 | 100,000,047 | Inner Txn |
| 5 (X6HSG...) | Contract | 100,000,000 | 100,000,000 | Inner Txn |
| **6 (D2YDE...)** | **Contract** | **100,000,000** | **100,000,000** | **Inner Txn** |

---

## Smart Contract Analysis

### Application ID: 2650568591

This smart contract is a **batch distribution system** with these characteristics:

**Evidence:**
1. Distributes to multiple recipients sequentially
2. Executes inner transactions for transfers
3. Responds to external triggers (contract calls)
4. Processes ~1 wallet per minute
5. Consistent opt-in detection and response

**Distribution Pattern:**
```
For each recipient:
1. Recipient opts into NUGGET
2. Bot detects opt-in within ~30 seconds
3. Caller triggers contract for that address
4. Contract validates and sends 100M NUGGET
5. Process repeats for next recipient
```

**Batch Characteristics:**
- **Sequential processing** (not parallel)
- **Consistent amounts** (100M base)
- **Automated detection** (monitors opt-ins)
- **Controlled pacing** (~1 min between wallets)

---

## Questions & Analysis

### Why the middle position?
**Possible reasons:**
- Alphabetical or deterministic ordering
- Random selection from eligible list
- Manual queue processing
- No significance to position

### Why exactly 31 seconds vs. 26?
**Theories:**
- Blockchain confirmation times
- Bot polling interval variations
- Network congestion differences
- Small random variation in automation

### Connection to Wallet 5?
**Evidence of pre-planning:**
- Wallet 5 sent this wallet 0.5 ALGO on Jan 23
- Both wallets opted in same day
- Both received same amount
- Suggests: Coordinated setup

### Will this wallet receive more?
**Indicators:**
- Contract still active
- Wallet still opted into NUGGET
- Pattern suggests one-time distribution per wallet
- Unlikely to receive additional drops

### What should the holder do?
**Options:**
1. **Hold** - Wait for potential appreciation
2. **Trade** - Exchange on DEXs (Tinyman, etc.)
3. **Add to LP** - Provide liquidity and earn fees
4. **Use in Ecosystem** - If NUGGET has utility
5. **Monitor** - Watch contract for more distributions

---

## Blockchain Explorer Links

**View this wallet and related contracts:**

- **This Wallet:** https://allo.info/account/D2YDE5FQF7SH2XOHF2TRCXFGYTICUENZG7PELDZVQ5XS4OVAVZK4KBWH5Y
- **Smart Contract:** https://allo.info/application/2650568591
- **Contract Address:** https://allo.info/account/ZLMXPKLRYPF6MT3VCI5JRTOG6ADFIWBL5D4MGYYYLKHGW6E333K4P4WTVM
- **Asset Info:** https://allo.info/asset/2699078351
- **Wallet 5 (prev):** https://allo.info/account/X6HSGRXUPK4O5E6M3KREDXWODVX7OR7XVLGT2565C4INA7SRUAKFRPYVTQ
- **Wallet 4 (next):** https://allo.info/account/MNRLTC5SO7NCCVCPGGUIUBTWWKUEJEJXMKZFE3UTLB6XZUMGLOXIMYJPPY

---

## Summary Statistics

| Metric | Value |
|--------|-------|
| Total Transactions | 2 |
| Incoming Transactions | 1 (+ 1 opt-in) |
| Outgoing Transactions | 0 |
| Total NUGGET Received | 100,000,000 |
| Total NUGGET Sent | 0 |
| Net Change | +100,000,000 |
| Current Balance | 100,000,000 ✅ |
| Total Fees Paid | 0.001 ALGO |
| Transaction Date | Jan 28, 2026 |
| Receive Method | Smart Contract |
| Distribution Type | Batch (2 of 3) |
| Batch Total | 300,000,047 NUGGET |

---

## Unique Position

**This wallet is notable because:**

1. 🎯 **Middle of Batch** - Second in a coordinated 3-wallet distribution
2. 💯 **Perfect Round Number** - Clean 100M (no fractional bonus)
3. 🔗 **Connected to Wallet 5** - Received funding from first batch wallet
4. 💎 **Pure Holder** - Retaining 100% of received NUGGET
5. ⚡ **31-Second Response** - Slightly slower than peers (26 sec)
6. 🆕 **Pre-Planned Recipient** - Funded days before distribution

---

## Strategic Context

### Batch Distribution Campaign
This wallet is part of a **300M NUGGET distribution** across 3 wallets:

**Total Impact:**
- 3 recipients
- 300,000,047 NUGGET distributed
- 100% retention rate
- 2-minute execution window
- Same smart contract mechanism

**Distinguishing Features:**
- Only batch wallet funded by another batch wallet
- Middle timing position
- Round 100M amount (no bonus)
- 31-second processing (slightly slower)

---

## Recommendations

### Short-Term (Next 7 Days)
✅ **Monitor** for any additional smart contract activity  
✅ **Research** NUGGET token utility and ecosystem  
✅ **Check** relationship with Wallet 5 (funding source)  
📊 **Track** the smart contract for more distributions

### Medium-Term (Next 30 Days)
💡 **Consider** registering an NFD for easier transactions  
💡 **Evaluate** DeFi options (LP pools, staking)  
💡 **Compare** with other batch recipients  
📊 **Monitor** market liquidity development

### Long-Term Strategy
🎯 **Determine** NUGGET's role in Algorand ecosystem  
🎯 **Assess** holding vs. trading strategy  
🎯 **Watch** for project roadmap and developments  
🎯 **Consider** diversification approaches

---

## Technical Notes

### Why Inner Transactions Matter
Inner transactions enable:
- Atomic multi-step operations
- No recipient signature required
- Batched efficient distributions
- Clear on-chain audit trails
- Programmatic logic execution

### Application 2650568591 Investigation
To learn more:
1. Examine application parameters on-chain
2. Review all inner transactions
3. Identify total distribution amount
4. Map all recipients
5. Understand eligibility criteria

### Batch Processing Benefits
Sequential distribution allows:
- Controlled rollout
- Rate limiting
- Error detection between wallets
- Manual oversight if needed
- Predictable gas costs

---

**Report End**

*This wallet received 100M NUGGET as the middle recipient in a coordinated smart contract batch distribution, representing part of a 300M NUGGET automated airdrop campaign.*
