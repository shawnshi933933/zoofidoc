# Core Concept

Liquid Node Token (LNT) separates assets into **Vesting Token (VT)** and **Yield Token (YT)**.

Users deposit their Node NFT into the **LNT Vault**. The Vault calculates and issues **VT (Vesting Tokens)** based on the vesting schedule and expected future rewards associated with the Node license. Simultaneously, the Vault generates a **YT (Yield Token)** for the user.



### **VT (Vesting Token):**

**VT** tokenizes the future guaranteed native token (T) rewards (**Deterministic Rewards**)associated with a node license, allowing participants to trade or transfer these rights immediately. Upon maturity, each VT can be redeemed 1:1 for the native token (T). When a user deposits their node license NFT into the **LNT Vault**, they receive the corresponding amount of VT tokens. To reclaim their NFT license, users must burn the requisite number of VT tokens.

### **YT (Yield Token):**

Beyond the guaranteed rewards represented by VT, node licenses often come with _uncertain, variable yields_ — such as transaction fee revenues or airdrops(**Non-Deterministic Rewards**). These unpredictable earnings are captured via **YT** tokens. Each YT represents a claim to one node license NFT. If a user wishes to reclaim their NFT _before maturity_, they must burn a YT along with the required VT amount. After maturity, burning a single YT suffices to retrieve the NFT without additional VT.YT tokens are fully transferable and tradable on DEXs. Yield calculations and reward distributions are handled automatically by the protocol.

### aVT(Accrued Vesting Token):

aVT (Accrued Vesting Token) represents the total number of tokens a node is eligible to receive in the future upon depositing a License into the Vault. The aVT value is tied to the timing of the deposit: earlier deposits result in more VTs, while later deposits obtain fewer VTs. Over time, the aVT gradually decreases, reaching zero upon expiration.

### VT Put Option:&#x20;

VT holders have the right to redeem their VT. Redemption follows a 1:1 principle of one VT for one T, but the protocol charges a certain percentage as a service fee. Depending on the project design, the timing of redemption may vary. The general mechanism is as follows: when holders deposit VT into the redemption contract, the Vault, after receiving the revenue token T from the nodes, converts the user's VT into T. If the amount of VT in the redemption contract exceeds the received T, the distribution will be proportional. If the amount of VT in the redemption contract is less than the received T, any remaining T after distribution will be allocated in the next cycle.

### Optimal Performance Assumption

Node licenses typically require the operator to maintain a certain quality of service, such as remaining online or validating transactions, in order to unlock their full rewards. However, evaluating node performance at scale is complex. In LNT's design, we **assume optimal node performance** — meaning all node obligations are met. This assumption is backed by partnerships with professional node operation service providers (e.g., NodeOps) to ensure the highest industry standards.
