# Withdraw/Redeem

The protocol's asset redemption mechanism also consists of two modes: the stability phase and the adjustment phase.

## Stability Mode

During the stability phase, users must hold a fixed ratio of ZUSD and xiBGT to redeem the corresponding iBGT from the Vault. For example, if a user wishes to redeem a certain amount of xiBGT, they need to pair it with the corresponding quantity of ZUSD, and vice versa. The calculation formula is as follows:

$$\Delta ZUSD = \frac{\Delta xiBGT \times M_{ZUSD}}{M_{xiBGT}}$$

The amount of iBGT redeemed with the paired $$\Delta xiBGT$$ and $$\Delta ZUSD$$ is:

$$\Delta iBGT = \frac{\Delta xiBGT \times M_{iBGT}}{M_{xiBGT}}$$

{% hint style="info" %}
**Example:**

Based on the data from the previous example, where there are a total of 7 iBGT in the Vault, the protocol has generated 93.33 ZUSD, and 2.33 xiBGT, when a user wishes to redeem 1 xiBGT, they need to accompany it with ZUSD for redemption. The required amount of ZUSD to accompany the redemption is:

$$\Delta ZUSD = \frac{\Delta xiBGT \times M_{ZUSD}}{M_{xiBGT}} = \frac{1 \times 93.33}{2.33} = 40$$



Then, the amount of iBGT to redeem when accompanying 1 xiBGT with 40 ZUSD for redemption (assuming no transaction fees) is:

$$\Delta iBGT = \frac{\Delta xiBGT \times M_{iBGT}}{M_{xiBGT}} = \frac{1 \times 7}{2.33} \times 1 = 3$$
{% endhint %}

***

## Adjustment Mode

When the protocol enters the adjustment phase, the user redemption rules change. If AAR rises above AARU, users can redeem xiBGT alone. The redemption quantity calculation formula is as follows:

$$\Delta iBGT = \frac{\Delta xiBGT \times (M_{iBGT} \times P_{iBGT} - M_{ZUSD})}{M_{xiBGT} \times P_{iBGT}}$$

If AAR falls below AARS, users can redeem ZUSD alone, and the quantity calculation formula is as follows:

$$\Delta iBGT = \frac{\Delta ZUSD}{P_{iBGT}}$$

In the extreme scenario where AAR falls below 100%, the USB redemption mechanism is as follows:

$$\Delta iBGT = \frac{\Delta ZUSD \times M_{iBGT}}{M_{ZUSD}} \quad \text{if AAR} < 100\%$$

Excluding the two situations mentioned above, users still need to pair two assets together for redemption.

{% hint style="warning" %}
The redemption fee is 0.5%
{% endhint %}
