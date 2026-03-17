# Aethir Checker Node

## About Aethir

Aethir is best described as distributed cloud compute infrastructure. It aggregates enterprise-grade GPU chips into a single global network to increase the supply of on-demand cloud compute resources for the AI, gaming, and virtualized compute sectors.\
Checker nodes ensure the integrity and service quality of Aethir network by checking the GPU specifications and its service process.

## Calculation of aVT（Accrued Vesting Token）

We use the following method to determine the number of VTs a user can obtain by depositing a Checker Node into the Vault.



* **Total Allocation for Checker Nodes**

According to Aethir's documentation

{% embed url="https://docs.aethir.com/aethir-tokenomics/token-distribution-of-aethir" %}

The tokens allocated to Checker Nodes account for 15% of the total supply, which is **6,300,000,000** ATH.



* **Number of Checker Nodes**

The total cap of Aethir Checker Nodes is 100,000, with the actual number being **91,759**, as verified on Arbiscan.

{% embed url="https://arbiscan.io/token/0xc227e25544edd261a9066932c71a25f4504972f1" %}

Since Aethir Node Sale has been closed, this number will not increase further.



* **Distribution duration**

Start Date: June 12, 2024

End Date:   June 11, 2028

Duration:  1,460 days



* **Final Calculation**

To find the theoretical daily ATH per Checker Node, we divide the total allocated tokens by the number of days and then by the number of nodes:

$$
aDVT = \frac{TA}{TD*N}
$$

Where:

aDVT: Average daily ATH per Checker Node

TA: Total Allocation

TD: Total Days

N: Number of Checker Nodes



Substitute the values:

$$
aDVT= \frac{6,300,000,000}{1,460*91,759} = 47.027
$$

We discard the decimal and get aDVT = 47.&#x20;

And we can get the **aVT = aDVT \* Remaining Days**

Finally, deposits a Node will obtain **VT amount = aVT \* (1 -VTC)**&#x20;

## Parameters

<table><thead><tr><th width="145.79998779296875">Symbol</th><th width="351.199951171875">Description</th><th>Data</th></tr></thead><tbody><tr><td>ED</td><td>End Date</td><td>June 11, 2028</td></tr><tr><td>aDVT</td><td>Average daily ATH per Checker Node</td><td>47</td></tr><tr><td>VTC</td><td>VT's commission when depositing</td><td>5%</td></tr><tr><td>VTF</td><td>VT Swap Fees</td><td>0.3%</td></tr><tr><td>R</td><td>Initial Liquidity Rate of VT/T</td><td>3</td></tr></tbody></table>

