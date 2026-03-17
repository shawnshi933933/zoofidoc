# 0G AI Alignment Node

## About 0G

0G (Zero Gravity) is the first decentralized AI L1 chain that orchestrates hardware resources (storage, compute) and software assets (data, models) to handle AI workloads at scale. It bridges the gap between Web2 AI capabilities and Web3 decentralization.

## Calculation of aVT（Accrued Vesting Token）

According to the official 0G documentation,  the total number of tokens attributed to one Node License is 854.7 tokens. This means that when a Node License NFT is deposited into the LNT Vault, the maximum aVT value is 854.7.

{% embed url="https://0g.ai/blog/ai-alignment-node-rewards-distribution-schedule-eligibility" %}

This total is divided into two parts: Part 1 and Part 2.

### Part 1:&#xD;

The maximum total reward for Part 1 is 282.05 $0G tokens. To receive the full amount, users must claim it after September 22, 2026. Our LNT Vault will automatically perform the claim after this date, so the aVT contribution from this part is fixed at 282.05.

Considering that users have already claimed a portion of Part 1 rewards before depositing the NFT, users will not immediately receive the corresponding VT upon deposit. Instead, after the LNT Vault queries the remaining unclaimed Part 1 amount from the 0G database, the VT will be airdropped to the user's address, after which the user can manually claim it.

### Part 2:

The maximum total reward for Part 2 is 572.65 $0G tokens. This portion requires the NFT to be delegated, and rewards are claimed daily. The daily reward (DVT) is approximately 0.52 $0G tokens.\
When the user deposits the NFT, they can immediately receive the VT corresponding to Part 2, calculated:

**VT = DVT × remaining days**

This calculation assumes that the user has already fully claimed all previous Part 2 rewards before making a deposit. If the user had not previously delegated the NFT, the missing portion will similarly be queried by the LNT Vault from the 0G database and airdropped to the user's address after detection, after which the user can manually claim it.

## Parameters

<table><thead><tr><th width="145.79998779296875">Symbol</th><th width="351.199951171875">Description</th><th>Data</th></tr></thead><tbody><tr><td>ED</td><td>End Date</td><td>Sep 21, 2028</td></tr><tr><td>DVT</td><td>Daily 0G per Checker Node</td><td>0.522968</td></tr><tr><td>VTC</td><td>VT's commission when depositing</td><td>0%</td></tr><tr><td>VTF</td><td>VT Swap Fees</td><td>0.3%</td></tr><tr><td>R</td><td>Initial Liquidity Rate of VT/T</td><td>3</td></tr></tbody></table>

