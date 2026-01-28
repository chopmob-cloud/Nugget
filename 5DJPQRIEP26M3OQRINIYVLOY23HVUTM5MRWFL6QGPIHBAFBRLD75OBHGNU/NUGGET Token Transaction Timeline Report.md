# NUGGET Token Transaction Timeline Report

**Asset ID:** 2699078351  
**Tracking Wallet:** `5DJPQRIEP26M3OQRINIYVLOY23HVUTM5MRWFL6QGPIHBAFBRLD75OBHGNU`  
**Period:** January 16 - January 28, 2026  
**Report Generated:** January 28, 2026

---

## 🔍 Key Counterparties

### 1. 🟡 Distribution Wallet (NUGGET Source)
**Address:** `ZVLRVYQSLJNVFMOIOKT35XH5SNQG45IVFMLLRFLHDQJQA5TO5H3SO4TVDQ`
- **Role:** NUGGET daily drop distributor
- **Transactions with tracked wallet:** 1
- **Total sent to tracked wallet:** 128,000,000 NUGGET
- **Pattern:** Sends "daily drop" distributions

### 2. 🟢 First Transfer Recipient
**Address:** `OET33EZEAEYPPKM2M4XGH5QCFROW7Q5PQ74XDSMD54VYM5MNRY6CNPOHZQ`
- **Role:** Received large bulk transfer
- **Transactions with tracked wallet:** 1
- **Total received from tracked wallet:** 128,012,813 NUGGET
- **Pattern:** Single large transfer shortly after daily drop
- **Notable:** Received 12,813 MORE than the daily drop amount

### 3. 🔵 Second Transfer Recipient
**Address:** `M2NKS63BDMEFBE3KHDNTM77TDINPLEO7CF4MTUFB2OEYQOKA74TV7YO34M`
- **Role:** Received smaller transfer later
- **Transactions with tracked wallet:** 1
- **Total received from tracked wallet:** 950,303 NUGGET
- **Pattern:** Single transfer 12 days after initial activity

### 4. 🟠 Authorization Address (Rekey)
**Address:** `YFHM34XLE6IGUCGDQXYPBWFUCNFZQV3FXXEF5HR5WWHE3MLNJJAFXUPSHU`
- **Role:** Authorization/signing address for rekeyed wallet
- **Appears in:** Transactions #2 and #3
- **Pattern:** Wallet is rekeyed to this address for enhanced security

---

## Executive Summary

- **Total Transactions:** 3
- **Total NUGGET Received:** 128,000,000
- **Total NUGGET Sent:** 128,963,116
- **Net Change:** -963,116 NUGGET
- **Current Balance:** 0 NUGGET
- **Special Feature:** Wallet uses rekey mechanism for added security

---

## Transaction Timeline

### Transaction #1: Daily Drop Receipt 💰
**Date:** January 16, 2026 at 21:11:53 UTC

| Detail | Value |
|--------|-------|
| **Type** | 🟢 **INCOMING** |
| **From** | 🟡 **Distribution Wallet**<br>`ZVLRVYQSLJNVFMOIOKT35XH5SNQG45IVFMLLRFLHDQJQA5TO5H3SO4TVDQ` |
| **To** | `5DJPQRIEP26M3OQRINIYVLOY23HVUTM5MRWFL6QGPIHBAFBRLD75OBHGNU` |
| **Amount** | **128,000,000 NUGGET** |
| **Fee** | 0.001000 ALGO |
| **Note** | "NUGGET daily drop" |
| **Block Round** | 57499914 |
| **Transaction ID** | `DLRLQ4QYX5V7OFOV64HEH5LV4IE3QIKOWQ35MQDFGIBATS2FH25A` |

**Summary:** This wallet received a daily drop of 128 million NUGGET tokens from the official distribution wallet. This is the same distribution mechanism as seen in the previous wallet report.

---

### Transaction #2: Large Transfer Out 📤
**Date:** January 16, 2026 at 21:14:29 UTC (2 minutes 36 seconds later)

| Detail | Value |
|--------|-------|
| **Type** | 🔴 **OUTGOING** |
| **From** | `5DJPQRIEP26M3OQRINIYVLOY23HVUTM5MRWFL6QGPIHBAFBRLD75OBHGNU` |
| **To** | 🟢 **First Transfer Recipient**<br>`OET33EZEAEYPPKM2M4XGH5QCFROW7Q5PQ74XDSMD54VYM5MNRY6CNPOHZQ` |
| **Amount** | **128,012,813 NUGGET** |
| **Fee** | 0.001000 ALGO |
| **Auth Address** | 🟠 `YFHM34XLE6IGUCGDQXYPBWFUCNFZQV3FXXEF5HR5WWHE3MLNJJAFXUPSHU` |
| **Block Round** | 57499969 |
| **Transaction ID** | `BRQP2PYMJBK7322UD7HY2YKQTWNSLFITYPK2S6GXOMIESHM55KOQ` |

**Summary:** Almost immediately after receiving the daily drop, the wallet transferred out 128,012,813 NUGGET. This is **12,813 MORE** than was received in the daily drop, indicating there was a prior balance of at least 12,813 NUGGET.

**Security Feature:** This transaction was signed using a rekeyed authorization address, adding an extra layer of security to the wallet operations.

**Pattern Analysis:** The extremely quick turnaround (under 3 minutes) suggests automated forwarding or a pre-planned transfer strategy.

---

### Transaction #3: Final Transfer Out 📤
**Date:** January 28, 2026 at 07:54:10 UTC (12 days later)

| Detail | Value |
|--------|-------|
| **Type** | 🔴 **OUTGOING** |
| **From** | `5DJPQRIEP26M3OQRINIYVLOY23HVUTM5MRWFL6QGPIHBAFBRLD75OBHGNU` |
| **To** | 🔵 **Second Transfer Recipient**<br>`M2NKS63BDMEFBE3KHDNTM77TDINPLEO7CF4MTUFB2OEYQOKA74TV7YO34M` |
| **Amount** | **950,303 NUGGET** |
| **Fee** | 0.001000 ALGO |
| **Auth Address** | 🟠 `YFHM34XLE6IGUCGDQXYPBWFUCNFZQV3FXXEF5HR5WWHE3MLNJJAFXUPSHU` |
| **Block Round** | 57853146 |
| **Transaction ID** | `B3QCRQKA6E3GN27BHRCVTV4SQVK3NY3JKZVHLZSG65J3SHVUEOPQ` |

**Summary:** After 12 days of inactivity, the wallet made a final transfer of 950,303 NUGGET to a different address. This transfer cleared any remaining balance, bringing the wallet to zero NUGGET.

**Timing Note:** The 12-day gap suggests this was not part of the immediate daily drop processing but rather a separate, planned transaction.

---

## Wallet Address Analysis

### Key Addresses Involved

#### 1. 🟡 Distribution Wallet (Source)
**Address:** `ZVLRVYQSLJNVFMOIOKT35XH5SNQG45IVFMLLRFLHDQJQA5TO5H3SO4TVDQ`
- **Role:** NUGGET distributor (daily drops)
- **Transactions:** 1 outgoing to tracked wallet
- **Total Sent:** 128,000,000 NUGGET
- **Pattern:** Consistent distribution mechanism across multiple wallets
- **Note:** Same distribution wallet as in the other tracked address

#### 2. 📍 Tracked Wallet (Main - Your Wallet)
**Address:** `5DJPQRIEP26M3OQRINIYVLOY23HVUTM5MRWFL6QGPIHBAFBRLD75OBHGNU`
- **Role:** Recipient of daily drops, intermediary for transfers
- **Current Balance:** 0 NUGGET
- **Activity Pattern:** Receive then quickly forward
- **Security:** Uses rekey mechanism with separate authorization address
- **Behavior:** Acts as a pass-through wallet for NUGGET distribution

#### 3. 🟢 First Transfer Recipient
**Address:** `OET33EZEAEYPPKM2M4XGH5QCFROW7Q5PQ74XDSMD54VYM5MNRY6CNPOHZQ`
- **Role:** Primary recipient of bulk transfer
- **Net Received:** 128,012,813 NUGGET
- **Timing:** Received within 3 minutes of daily drop
- **Pattern:** Single large transfer
- **Likely:** Trading wallet, exchange hot wallet, or liquidity pool

#### 4. 🔵 Second Transfer Recipient
**Address:** `M2NKS63BDMEFBE3KHDNTM77TDINPLEO7CF4MTUFB2OEYQOKA74TV7YO34M`
- **Role:** Received smaller residual transfer
- **Received:** 950,303 NUGGET
- **Timing:** 12 days after initial activity
- **Pattern:** Clean-up or residual transfer

#### 5. 🟠 Authorization Address (Security)
**Address:** `YFHM34XLE6IGUCGDQXYPBWFUCNFZQV3FXXEF5HR5WWHE3MLNJJAFXUPSHU`
- **Role:** Authorization signer for rekeyed wallet
- **Purpose:** Enhanced security through key separation
- **Usage:** Signs transactions #2 and #3
- **Benefit:** Private keys separated from account address

---

## Transaction Flow Diagram

```
Day 1 (Jan 16, 2026)
┌─────────────────────────────────────────────────────────────────┐
│                                                                   │
│  21:11:53 UTC                                                    │
│  🟡 DISTRIBUTION WALLET → 📍 TRACKED WALLET                     │
│  128,000,000 NUGGET                                             │
│  Note: "NUGGET daily drop"                                      │
│                                                                   │
│  ↓ (2 minutes 36 seconds later)                                 │
│                                                                   │
│  21:14:29 UTC                                                    │
│  📍 TRACKED WALLET → 🟢 FIRST RECIPIENT                          │
│  128,012,813 NUGGET                                             │
│  (12,813 more than received - used prior balance)              │
│  🟠 Signed by: Rekey Auth Address                               │
│                                                                   │
└─────────────────────────────────────────────────────────────────┘

Day 13 (Jan 28, 2026) - 12 days later
┌─────────────────────────────────────────────────────────────────┐
│                                                                   │
│  07:54:10 UTC                                                    │
│  📍 TRACKED WALLET → 🔵 SECOND RECIPIENT                         │
│  950,303 NUGGET                                                 │
│  (Final transfer - balance cleared to zero)                     │
│  🟠 Signed by: Rekey Auth Address                               │
│                                                                   │
└─────────────────────────────────────────────────────────────────┘

LEGEND:
🟡 = Distribution Wallet (NUGGET source)
📍 = Your Tracked Wallet  
🟢 = First Transfer Recipient (bulk)
🔵 = Second Transfer Recipient (residual)
🟠 = Authorization Address (rekey security)
```

---

## Key Observations

### 1. **Rekey Security Mechanism** 🔐
This wallet uses Algorand's rekey feature, which allows transactions to be signed by a different address than the wallet address itself. This provides enhanced security by:
- Separating the account address from the signing keys
- Allowing key rotation without changing the account address
- Adding an extra layer of protection for high-value operations

### 2. **Lightning-Fast Processing** ⚡
The first transfer occurred just 2 minutes and 36 seconds after receiving the daily drop. This suggests:
- Automated processing or bot-driven operations
- Pre-planned transfer strategy
- Minimal human intervention in the process

### 3. **Prior Balance Confirmed** 💰
The wallet sent out 12,813 NUGGET more than it received in the daily drop, proving:
- There was activity before January 16, 2026
- The wallet had accumulated at least 12,813 NUGGET previously
- This report only captures the transactions since Jan 16, not the full history

### 4. **Two-Phase Distribution** 📊
The transactions show a clear two-phase pattern:
- **Phase 1 (Day 1):** Immediate processing of daily drop (within minutes)
- **Phase 2 (Day 13):** Delayed transfer of residual balance
- This suggests different purposes or destinations for different tranches

### 5. **Zero Final Balance** 🎯
The wallet has been completely emptied:
- Current balance: 0 NUGGET
- All received tokens distributed
- Functions as a pure pass-through/distribution wallet

### 6. **Total Transaction Fees** 💸
- All 3 transactions paid identical fees: 0.001 ALGO each
- Total fees: 0.003 ALGO
- Extremely cost-effective on Algorand network

---

## Comparison with Other Tracked Wallet

### Similarities:
- Both receive NUGGET daily drops from the same distribution wallet
- Both immediately forward tokens to other addresses
- Both have zero current balance
- Both operate as intermediary/pass-through wallets

### Differences:
| Aspect | Wallet 1 (2RXI...) | Wallet 2 (5DJPQ...) |
|--------|-------------------|---------------------|
| **Daily Drop Amount** | 198,000,000 NUGGET | 128,000,000 NUGGET |
| **Total Transactions** | 6 | 3 |
| **Security** | Standard | Rekeyed (enhanced) |
| **Processing Pattern** | Multiple back-and-forth | One-way distribution |
| **Counterparties** | 3 addresses | 2 addresses |
| **Activity Duration** | 5 days | 12 days |

---

## Questions & Analysis

### Why different daily drop amounts?
Wallet 1 received 198M NUGGET while Wallet 2 received 128M NUGGET. Possible reasons:
- Different participation tiers or levels
- Different staking amounts or qualifications
- Time-based distribution changes
- Different reward categories

### What is the rekey authorization address?
The auth address (`YFHM34X...`) is used to sign transactions instead of the wallet's main private key. This could be:
- A hardware wallet address
- A multisig signing authority
- A cold storage security key
- An automated signing service

### Why the 12-day delay for the final transfer?
The large gap between transactions suggests:
- Waiting for additional accumulation
- Scheduled distribution event
- Manual intervention required
- Different operational workflow

### Where did the 12,813 NUGGET come from?
Since the wallet sent more than it received in the daily drop:
- Prior daily drops occurred before Jan 16
- Residual from previous distribution cycles
- Unclaimed rewards from earlier periods

---

## Blockchain Explorer Links

**View these transactions on Algorand explorers:**

- **Allo.info:** https://allo.info/account/5DJPQRIEP26M3OQRINIYVLOY23HVUTM5MRWFL6QGPIHBAFBRLD75OBHGNU
- **AlgoExplorer:** https://algoexplorer.io/address/5DJPQRIEP26M3OQRINIYVLOY23HVUTM5MRWFL6QGPIHBAFBRLD75OBHGNU
- **Asset Info:** https://allo.info/asset/2699078351

---

## Summary Statistics

| Metric | Value |
|--------|-------|
| Total Transactions | 3 |
| Incoming Transactions | 1 |
| Outgoing Transactions | 2 |
| Total NUGGET Received | 128,000,000 |
| Total NUGGET Sent | 128,963,116 |
| Net Change | -963,116 |
| Current Balance | 0 |
| Total Fees Paid | 0.003 ALGO |
| Date Range | Jan 16-28, 2026 (12 days) |
| Unique Counterparties | 3 addresses |
| Security Feature | Rekeyed wallet |

---

## Recommendations

### Security
✅ **Good:** Wallet uses rekey mechanism for enhanced security  
✅ **Good:** Consistent authorization address usage  
⚠️ **Consider:** Monitoring the authorization address for any unauthorized changes

### Operations  
✅ **Good:** Efficient processing with minimal fees  
✅ **Good:** Clean balance management (no dust left)  
💡 **Insight:** Consider if both immediate and delayed transfers are necessary

### Tracking
📊 **Suggested:** Monitor for future daily drops to this address  
📊 **Suggested:** Track where transferred NUGGET ultimately flows  
📊 **Suggested:** Compare patterns across multiple daily drop recipients

---

**Report End**

*This wallet demonstrates efficient NUGGET distribution with enhanced security through the use of Algorand's rekey mechanism.*
