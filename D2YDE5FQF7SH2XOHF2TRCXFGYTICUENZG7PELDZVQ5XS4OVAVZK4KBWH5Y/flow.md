flowchart TD
  %% Dataset-scoped: only the 5 txns provided in the pasted JSON

  %% Primary wallet
  W_D2Y["WALLET\nD2YDE5...WH5Y"]

  %% Counterparties / other addresses seen in this dataset
  W_53LJ["WALLET\n53LJLQ...R424"]
  W_ZLMX["WALLET\nZLMXPK...TVM"]
  W_X6HS["WALLET\nX6HSGR...VTQ"]
  W_OKRT["WALLET\nOKRT4A...OUM"]

  %% Assets / App nodes (only ids shown, no external enrichment)
  ASA_NUGGET["ASA 2699078351"]
  ASA_1357["ASA 1357247143"]
  APP_2650["APP 2650568591\non-completion: noop"]

  %% --- Txns involving the wallet ---

  %% (1) App call that produced an inner axfer to D2Y of ASA 2699078351
  W_53LJ -->|appl\nid: WDXPKG...\nround: 57864417| APP_2650

  subgraph ITX_WDXPKG["inner-txns exploded\nparent: WDXPKG4... (appl)"]
    direction TB
    W_ZLMX -->|axfer 100,000,000\nASA 2699078351\nround: 57864417| W_D2Y
  end

  %% Show that the inner axfer is about ASA 2699078351
  ASA_NUGGET --- ITX_WDXPKG

  %% (2) Opt-in / self axfer of ASA 2699078351 (amount 0 to self)
  W_D2Y -->|axfer 0 (self)\nASA 2699078351\nid: F4J7GQ...\nround: 57864406| W_D2Y
  ASA_NUGGET --- W_D2Y

  %% (3) Close-out of ASA 1357247143 from D2Y to OKRT (receiver + close-to)
  W_D2Y -->|axfer close-out\nASA 1357247143\namount 0\nclose-to: OKRT...\nid: HJBPDY...\nround: 57711773| W_OKRT
  ASA_1357 --- W_OKRT

  %% (4) Opt-in / self axfer of ASA 1357247143 (amount 0 to self)
  W_D2Y -->|axfer 0 (self)\nASA 1357247143\nid: SWQVME...\nround: 57701775| W_D2Y
  ASA_1357 --- W_D2Y

  %% (5) Payment into D2Y
  W_X6HS -->|pay 500,000\nid: QKERON...\nround: 57701769| W_D2Y
