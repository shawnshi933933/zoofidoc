---
hidden: true
---

# Price Curve

To implement a perpetual version of Pendle, YT is not minted initially but is tracked by the contract. To obtain YT, users need to purchase in the contract. The price of YT is determined by a pricing curve set by the contract. This curve fully accounts for changes in supply and demand, as well as price decay over time, and incorporates a Dutch auction mechanism to achieve efficient price discovery.

## Price Decay Line

To achieve efficient price discovery, the price of YT will initially open at a higher level and then decrease at a certain rate until someone is willing to trade at that price. The decay formula is given by          &#x20;

&#x20;                                                                                  $$P(t) = P_a - b\times(t-t_0)$$

Here, ‘Pa’ is the initial set value, and ‘b’ is the decay coefficient, causing the price to decrease gradually. Assuming we want the price to decay to 0 over a while ‘T’, then

$$𝑏=𝑎 / 𝑇$$， So we can combine the formula into

&#x20;                                                                                 $$P(t) = P_a \times\left(1 - \frac{t-t_0}{T}\right)$$

Where ：

* $$P_a$$ is the initial price;
* $$T$$ is the price decay period;
* $$t$$ is the current time;
*   $$t_0$$ is the initial time.



## Price Floor Line

According to this price decay line, if there are no trades for an extended period, the price will eventually drop to zero, which is not our desired outcome. Therefore, we have set a price floor; once the price decays to this floor, it will not decrease further.

The price floor is also a time-dependent process because YT has an intrinsic value at the start of an epoch, which gradually decreases over time until it eventually reaches zero. Thus, we have formulated this price floor accordingly.

&#x20;                                                                          $$P_f (t)=P_i \times(t_e-t)/D$$

Where ：

* $$Pi$$ is the initial floor price;
* $$t_e$$ is expiration time;
* $$t$$ is the current time;
* $$D$$ is the duration of the epoch.

Combining the two price lines above, we can see how the price changes over time in this diagram:

<figure><img src="../../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>

## Price Impact Line

In addition to time affecting the price, changes in the supply and demand of YT will also impact the price. An increase in demand will cause the price to rise, while an increase in supply will cause the price to fall. To address this, we designed a formula to simulate the impact of supply and demand on the price.

We assume that at the beginning of an epoch, the total supply of YT is ‘M’, which increases when someone makes a deposit. Initially, all these YTs are held in the contract. As people buy YT, the amount in the contract decreases, leaving a remaining stock of YT in the contract as ‘S’. We incorporate the changes in ‘M’ and ‘S’ into the above price formula.

&#x20;                                        The original formula is     $$P(t) = P_a \times\left(1 - \frac{t-t_0}{T}\right)$$

The changes in ‘M’ and ‘S’ will affect $$P_a$$, and the impact factor is designed as $$1 + \frac{e_1 \times (M - S)}{M}$$&#x20;

At the same time, the changes in ‘M’ and ‘S’ will also affect T (the decay period). We similarly apply a factor as $$1 + \frac{M - S}{e_2 \times M}$$.

Thus, the final formula becomes:

$$
P{(M,S,t)} = P_a \times \left( \left( 1 + \frac{e_1 \times (M - S)}{M} \right) - \frac{t-t_0}{T \times \left(1 + \frac{M - S}{e_2 \times M}\right)} \right)
$$

Where:

* $$P_a$$ is the initial price;
* $$T$$ is the price decay period;
* $$t$$ is the current time;
* $$t_0$$ is the initial time, at the beginning, it is the start time of Epoch, and after a transaction occurs, the initial time will be updated to the last transaction time;
* $$M$$ is the total supply of YT;
* $$S$$ is the stock of YT in the contract;
* $$e_1$$ is the price impact coefficient;
* $$e_2$$ is the price decay period variation coefficient.

## Calculation Example

Now, let's use the above formula to calculate how much it costs（Y） to purchase number X of YT.

Here, since the price is not fixed, after purchasing number X of YT, the inventory amount of YT, S, will decrease, and the price will change accordingly. We can represent this relationship through a graph.

<figure><img src="../../.gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure>

In the graph, we can see that due to the purchasing action,  ‘S’ decreases, which in turn causes the price to increase. The shaded area in the graph represents the amount ‘Y’ that needs to be spent. We use calculus to calculate the area of the shaded region.

$$
Y = \int_{S}^{S-X} P_{(M,S,t)} \, ds
$$

By substituting the price formula, we can obtain:

$$
Y = \int_{S}^{S-X} \left[ P_a + \frac{e_1 \times P_a \times (M - S)}{M} - \frac{P_a \times (t - t_0)}{T \times \left(1 + \frac{M - St}{e_2 \times M}\right)} \right] ds
$$

The final calculation formula is:



&#x20;                                           $$Y = P_a \times X + e_1 \times P_a \times \left( X - \frac{X^2}{2M} \right) - \frac{P_a \times (t - t_0) \times X}{T \times \left(1 + \frac{M - St}{e_2 \times M}\right)}$$

