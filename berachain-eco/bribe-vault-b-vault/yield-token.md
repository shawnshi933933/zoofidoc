# Yield Token

Yield Token(YT) represents all real-time yields from the underlying assets. Each Epoch will generate YTs with different serial numbers, and these YTs can only claim the rewards corresponding to their specific Epoch.

## Buy YT

YT is not initially minted but is tracked by the contract. Users need to purchase YT in the contract to obtain it. The price of YT is determined by a bonding curve and a virtual AMM set by the contract. It fully accounts for supply and demand changes and incorporates a Dutch auction mechanism to achieve efficient price discovery. This is Zoo Finance's innovative mechanism, which we have named [dutch-vamm.md](dutch-vamm.md "mention")

## Harvest Rewards

Due to the Dutch-VAMM mechanism, YT cannot be completely bought out by users, and some will remain in the contract. The YTs remaining in the contract do not participate in the reward distribution. As a result, the rewards earned by the YTs purchased by users are greater than the yield of the corresponding amount of underlying assets.

For example, there are a total of 100 underlying assets, initially generating 100 PTs and 100 YTs. All YTs are initially held in the contract. Throughout the Epoch, 50 YTs are bought by users, leaving 50 YTs in the contract. Since the 50 YTs remaining in the contract do not participate in the reward distribution, each YT held by users represents the yield of 2 underlying assets.

The rewards for YT holders are divided into two types:

* One type is distributed based on the holder's **YT Balance**, which is suitable for regular rewards, such as BGT emissions.
* The other type is distributed based on the holder's **YT Points**, which is suitable for irregular rewards like one-time airdrops and bribes. YT Points are calculated based on the duration of YT holding. Users must click "Claim" to receive their corresponding YT Points.

<figure><img src="../../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>
