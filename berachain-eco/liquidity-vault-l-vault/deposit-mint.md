# Deposit/Mint

Depositing collateral into L-Vault can mint both ZUSD and margin tokens.

The L-Vault operates in two modes, starting initially with the stability mode, when the Vault's AAR deviates below the set lower limit (Safety AAR, AARS) or exceeds the upper limit (Upper AAR, AARU), the protocol enters an adjustment phase.&#x20;

Taking the iBGT vault as an example:

## Stability Mode

When assets are first deposited into the Vault for minting, as the quantities of existing ZUSD and xiBGT are zero, we calculate the minting ratio based on the initial price and then maintain this minting ratio unchanged throughout the stability phase. The protocol records the quantity of ZUSD minted in each Vault, and the total supply of ZUSD is the sum of ZUSD minted across all Vaults.

**When the contract is initially created,** ZUSD and xiBGT are generated in a fixed ratio. The specific quantities and ratios are calculated using the following formula:

$$\Delta ZUSD = \Delta iBGT \times P_{iBGT-i} \times \frac{1}{AART_{iBGT}}$$

$$\Delta xiBGT = \Delta iBGT \times \left(1 - \frac{1}{AART_{iBGT}}\right)$$

Where:

* $$\Delta ZUSD$$ : The quantity of minted ZUSD.
* $$\Delta xiBGT$$: The quantity of minted xiBGT.
* $$\Delta iBGT$$: The quantity of iBGT used for minting.
* $$P_{iBGT}$$: The initial price of iBGT relative to USD (provided by an oracle).&#x20;
* $$AART_{iBGT}$$: The protocol's target AAR (Asset Adequacy Ratio) for the iBGT vault.

**After the initiation, when depositing into the iBGT vault**, users can mint ZUSD and xiBGT in a fixed ratio. The formulas for calculating the minted amounts are as follows:

$$\Delta ZUSD = \Delta iBGT \times \frac{M_{ZUSD}}{M_{iBGT}}$$

$$\Delta xiBGT = \frac{\Delta ZUSD \times M_{xiBGT}}{M_{ZUSD}}$$

{% hint style="info" %}
**Example：**

We assume $$AART_{iBGT}$$=150% when 2 iBGT are first deposited into the Vault, and the real-time market price of iBGT at that time is $20, then:

$$\Delta ZUSD = \Delta iBGT \times P_{iBGT} \times \frac{1}{AART_{iBGT}} = 2 \times 20 \times 0.6667 = 26.67;$$

$$\Delta xiBGT = \Delta iBGT \times \left(1 - \frac{1}{AART_{iBGT}}\right) = 2 \times 0.3333 = 0.67$$&#x20;



If another user deposits 1 iBGT into the Vault, assuming the market price of iBGT is $22, and the protocol is still in the stability phase, the user can obtain $$\Delta ZUSD$$ and  $$\Delta xiBGT$$ as follows:

$$\Delta ZUSD = \Delta iBGT \times \frac{M_{ZUSD}}{M_{iBGT}}=1 \times \frac{26.67}{2}=13.33$$

$$\Delta xiBGT = \frac{\Delta ZUSD \times M_{xiBGT}}{M_{ZUSD}} =\frac{13.34 \times 0.6667}{26.67}=0.33$$&#x20;



In this scenario, with a total of 3 iBGT in the Vault, the Vault has generated a total of 40 ZUSD and 1 xiBGT.
{% endhint %}

From the examples provided above, we can observe that within the protocol's stability phase, the number of ZUSD and xiBGT generated for each iBGT deposited remains constant.



## Adjustment Mode

When the Vault's AAR deviates below the set lower limit (Safety AAR, AARS) or exceeds the upper limit (Upper AAR, AARU), the protocol enters an adjustment phase. During this adjustment phase, the method of asset minting changes.&#x20;

**When AAR rises above AARU,** users can mint ZUSD individually. The corresponding minting formula is as follows:

$$\Delta ZUSD = \Delta iBGT \times P_{iBGT}$$

{% hint style="warning" %}
If users want to mint xiBGT, they still need to mint ZUSD+xiBGT according to the protocol's calculated ratio.
{% endhint %}

**When AAR falls below AARS**, users can mint xiBGT alone using the underlying asset. The minting formula in this case is:

$$\Delta xiBGT = \frac{\Delta iBGT \times P_{iBGT} \times M_{xiBGT}}{M_{iBGT} \times P_{iBGT} - M_{ZUSD}}$$

**When AAR further drops below 101%**, the formula for minting ETHx alone will change to:

$$\Delta xiBGT = \frac{\Delta iBGT \times P_{iBGT} \times M_{xiBGT} \times 100}{M_{ZUSD}}$$

Where:

* $$\Delta ZUSD$$ : The quantity of ZUSD minted.
* $$\Delta xiBGT$$: The quantity of xiBGT minted.
* $$\Delta iBGT$$: The quantity of iBGT used for minting.
* $$P_{iBGT}$$: The real-time price of iBGT relative to USD (provided by the oracle).
* $$M_{iBGT}$$: The quantity of iBGT in the Vault.
* $$M_{xiBGT}$$: The quantity of xiBGT minted in the iBGT Vault.
* $$M_{ZUSD}$$: The quantity of ZUSD already minted in the iBGT Vault.

{% hint style="warning" %}
If users want to mint ZUSD, they still need to mint ZUSD+xiBGT according to the protocol's calculated ratio.
{% endhint %}

When Vault's AAR returns to AART, the protocol returns to the Stability Mode, and the asset minting formula reverts to the calculation used during the stability phase.
