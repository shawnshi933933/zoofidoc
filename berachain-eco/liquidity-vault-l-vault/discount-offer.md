# Discount Offer

**'Discount offer' is a mechanism that is only activated in Adjustment Mode.** In this mechanism, users can purchase margin tokens like xiBGT using ZUSD, and when AAR is lower than AART, the discount for purchases gradually increases over time. It is a Dutch auction-based exchange.

***

**Let's take the xiBGT discount offer as an example:**

* In the Adjustment Mode,  when AAR is between 101% and AART, the formula for trading xiBGT with ZUSD is:

$$\Delta xiBGT = \frac{\Delta ZUSD \times M_{xiBGT}}{M_{iBGT} \times P_{iBGT} - M_{ZUSD}} \times (1 + r)$$

Where ( r ) is the compensation coefficient, which gradually increases over time.&#x20;

{% hint style="warning" %}
Additionally, to prevent extreme volatility risks, when the AAR falls below 110%, the 'Discount offer' will be paused for half an hour, and it will resume after one hour.
{% endhint %}

* When AAR falls below 101%, the formula for trading xiBGT with ZUSD changes to:

$$\Delta xiBGT = \frac{\Delta ZUSD \times M_{xiBGT} \times 100}{M_{ZUSD}}$$

* When AAR rises over AART, it enters Stability Mode, and the discount offer ends.
