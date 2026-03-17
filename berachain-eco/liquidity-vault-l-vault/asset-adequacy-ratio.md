# Asset Adequacy Ratio

Asset Adequacy Ratio (AAR) signifies the capability of the protocol vault to cover the ZUSD debt. It is used to assess the vault's health. Below is the calculation for AAR, taking the iBGT vault as an example.

## Calculation of AAR <a href="#calculation-of-aar" id="calculation-of-aar"></a>

The AAR for iBGT vault is calculated as follows:



$$
AAR_{iBGT} = \frac{M_{iBGT} \times P_{iBGT}}{M_{ZUSD}} \times 100\%
$$

Where:

* $$M_{iBGT}$$ is the amount of iBGT in the vault.
* $$P_{iBGT}$$ is the current price of iBGT, obtained from the oracle.
* $$M_{ZUSD}$$ is the amount of ZUSD minted from the iBGT vault.



## Thresholds of AAR

*   **AART**: Target AAR

    Target AAR represents the ideal state of the vault.
*   **AARS**: Safety AAR

    When below the Safety AAR, the pool's ability to repay USB debt is at risk.
*   **AARU**: Upper AAR

    When above the Upper AAR, the leverage ratio of Margin tokens becomes less attractive.&#x20;

The thresholds of AAR for each vault can be set individually.&#x20;



## AAR Rebalancing

Unlike traditional lending protocols, Wand does not enforce liquidations. Instead, it introduces an Adjustment mode, [price-trigger-yield.md](price-trigger-yield.md "mention") and a [discount-offer.md](discount-offer.md "mention") mechanism to dynamically adjust the AAR. This allows anyone to participate and potentially earn arbitrage profits, ensuring the Vault's health.
