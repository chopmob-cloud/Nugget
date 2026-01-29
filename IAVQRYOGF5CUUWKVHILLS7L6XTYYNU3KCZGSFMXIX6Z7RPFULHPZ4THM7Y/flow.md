```mermaid
flowchart LR

%% =========================
%% Wallet nodes
%% =========================
IAVQ[IAVQRYOGF5CUUWKVHILLS7L6XTYYNU3KCZGSFMXIX6Z7RPFULHPZ4THM7Y]
W53[53LJLQATA34TUZRWPYQJXGRDDZIW4T3MXEQ455VFTASI5PSWXMBNN2R424]
ZLMX[ZLMXPKLRYPF6MT3VCI5JRTOG6ADFIWBL5D4MGYYYLKHGW6E333K4P4WTVM]
ZXJP[ZXJPSWVZ2QZUULP2U3YXPA32ZH6FPLXX7FIQBUP3ETF25EMYTCEGO4H7NE]
MNRL[MNRLTC5SO7NCCVCPGGUIUBTWWKUEJEJXMKZFE3UTLB6XZUMGLOXIMYJPPY]
OKRT[OKRT4A5FVHG6PBT7JCFRYRLMC2G6A6UH4PAJH4LUSKKD6H35UIKTFD5OUM]

%% =========================
%% App node
%% =========================
APP2650[APP_2650568591]

%% =========================
%% Application call and inner NUGGET transfer
%% =========================
W53 -->|appl_call| APP2650
ZLMX -->|axfer_100000000_ASA_2699078351_inner| IAVQ

%% =========================
%% ASA NUGGET opt-in
%% =========================
IAVQ -->|axfer_0_ASA_2699078351_optin| IAVQ

%% =========================
%% ASA 1357247143 lifecycle
%% =========================
IAVQ -->|axfer_0_ASA_1357247143_optin| IAVQ
IAVQ -->|axfer_close_ASA_1357247143| OKRT

%% =========================
%% ALGO payments
%% =========================
ZXJP -->|pay_500000| IAVQ
IAVQ -->|pay_250000| MNRL
```
