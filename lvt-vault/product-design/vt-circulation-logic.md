# VT Circulation Logic

Core to LVT, differing from LNT's Node NFT deposit-based dynamic VT calculation. LVT mints a VT supply upfront, tied 1:1 to total vesting T, enabling immediate liquidity via discounted sales.

Two exclusive scenarios:

### **Project Token Release Scenario**:

* Project defines vesting plan (e.g., 1M T over 24 months, linear).
* Contract mints VT.
* VT trading: Locked token holders sell VT on secondary markets; buyers lock through cliff for T upside.
* Put Option: As T releases, VT holders exercise VT -->T conversion;
* Redeemption: After the Vault operation ends, all circulating VT can be redeemed 1:1 for T.

### **SAFT Contract Scenario**:

* Early investor uploads notarized SAFT (verified by multi-sig).
* Protocol parses terms (e.g., 1M T with a 6-month cliff, then linear).
* Contract Mints VT.
* VT trading: Investors sell VT on secondary markets; buyers lock through cliff for T upside.
* Put Option: As T releases, VT holders exercise VT -->T conversion;
* Redeemption: After the Vault operation ends, all circulating VT can be redeemed 1:1 for T.

