# VT Swap

VT liquidity is provided through an Automated Market Maker (AMM) pool with a specially designed price formula, aimed at achieving less gap between the prices of VT and T as the vesting period nears its end.

### Price Formula:

$$
\text{price}(t) = \frac{1}{\text{rateScalar}(t) }\times \ln \left( \frac{p(t)}{(1 - p(t))*R} \right) + \text{rateAnchor}(t)
$$

* **Normalized time ( t )** ranges from 0 (Vesting End) to 1.
* **P(t)** is a metric that measures the proportion of VT in the pool. Calculated by the formula:               **P(t) = Amount of VT / (Amount of VT + Amount of T)**
* **rateScalar:** **rateScalar(t)=ScalarRoot/t**, adjusts dynamically to maintain capital efficiency.
* **rateAnchor:** **rateAnchor(t) = 1 + (InitialAnchor-1) \* t**, adjusts the expected discount between VT and T.
* **R**: Initial Liquidity Rate of VT/T&#x20;

{% hint style="info" %}
Example:

Alice wants to swap 100 T for VT.

Given   $$\text{rateScalar} =100$$, $$\text{rateAnchor} = 1.1$$，R=1  Initial VT proportion $$( p_{\text{before}} = 0.6 )$$

$$
\text{price}_{\text{before}} = \frac{1}{100} \times \ln\left(\frac{0.6}{0.4}\right) + 1.1 = 1.104055
$$

After swapping 100 T for VT, assuming $$p_{\text{after}} = 0.55$$

$$
\text{price}_{\text{after}} = \frac{1}{100} \times \ln\left(\frac{0.55}{0.45}\right) + 1.1 = 1.102007
$$

$$
dVT = 100 \times \frac{1.104055 + 1.102007}{2} = 110.3031
$$

Alice received 110.3031 VT
{% endhint %}

