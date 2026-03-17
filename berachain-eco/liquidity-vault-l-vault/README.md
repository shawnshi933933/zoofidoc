# Liquidity Vault (L-Vault)

Liquidity Vault (L-Vault) is a MakerDao-like product where users can deposit assets to receive a stablecoin similar to DAI. The difference is that our innovative Pooled CDP mechanism also releases the liquidity of the over-collateralized portion as a margin token, achieving 100% asset efficiency.

In traditional over-collateralization models, users typically operate individual vaults, each generating its Collateralized Debt Position (CDP). ZOO Finance, however, innovates by aggregating vaults, which harmonizes the assets minted and obviates the necessity for singular liquidations. Within this aggregated structure lies a pooled CDP that encapsulates all circulating margin tokens, with the debt acknowledged as collective. Consequently, every margin token holder assumes a proportional share of this communal debt.

ZOO Finance employs the Asset Adequacy Ratio (AAR) as a metric to gauge the health of the vault. A heightened AAR diminishes the leverage ratio applicable to margin tokens. Conversely, a diminished AAR indicates potential debt repayment risks associated with USB. Thus, maintaining the AAR balance is crucial.

Initially, the L-Vault supports iBGT (a liquid staking derivative of BGT built with Infrared) and Bera, with plans to support more assets in the future.

