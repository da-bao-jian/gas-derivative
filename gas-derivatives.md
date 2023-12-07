# Qi Protocol - A Blockspace(Blobspace) Derivatives Market

# Qi Protocol - A Blockspace(Blobspace) Market

### Intro

On Ethereum, blocks constitute the foundational settlement layer for state transitions. In the pre-Proof of Stake (PoS) era, miners, and in the post-PoS era, validators, are responsible for supplying blockspace, a critical resource necessitated by transactional activities on the blockchain. An increase in on-chain activities invariably escalates network fees, thereby fostering heightened competition for blockspace. This competitive landscape transforms blockspace into a coveted commodity, indispensable to Layer 2 solutions, Maximal Extractable Value (MEV) searchers, and (Account Abstract smart)wallets, rendering it an ideal candidate for financialization—a process akin to the evolution observed in traditional commodity markets. 

Historically, commodity derivatives trading of commodity dates back to the [Dojima Rice Exchange](https://en.wikipedia.org/wiki/D%C5%8Djima_Rice_Exchange), where derivative contracts like forwards and options originated. Rice merchants engaged in the trade of "rice tickets," which represented entitlements to rice stored in their warehouses, rather than dealing with the physical commodity itself. These rice tickets formed the foundation for the development of various derivative contracts, including short sales, forwards, and options, which are prevalent in modern trading. This historical lineage of financial innovation is further exemplified by the establishment of agricultural futures by the Chicago Board of Trade, which significantly contributed to efficient risk management and scalability in operations. The late 20th-century creation of the Volatility Index (VIX) market, despite the non-tradeable nature of the VIX itself, presents a parallel evolution. The thriving derivatives market of the VIX closely mirrors the Ethereum fee market, particularly in the context of the underlying asset—gas—not being directly tradable. The implementation of [EIP-1559](https://eips.ethereum.org/EIPS/eip-1559) marked a pivotal transition for Ethereum, introducing a structured fee market and thereby facilitating the creation of a standardized gas reference price, which is imperative for the settlement of a variety of derivative products.

Looking ahead, the Ethereum blockspace market, having drawn lessons from these historical developments, stands on the cusp of a similar evolutionary trajectory. The Merge and the anticipated [EIP-4844](https://www.eip4844.com/) are set to redefine this landscape, potentially drawing parallels with the traditional oil and natural gas markets where aggregated benchmarks have historically enabled wider market participation and enhanced efficiency in price discovery. In a manner akin to the oil and VIX markets, the burgeoning Ethereum blockspace market is poised for substantial growth through the incorporation of derivative trading, which promises to refine price discovery mechanisms and offer sophisticated tools for the management of digital asset portfolios.


## Dojima - A Physically-settled Blockspace Futures Market for Blockspace

![sec03_img01](https://hackmd.io/_uploads/B1Rj3G1Ia.jpg)<em>The offices of Dojima Rice Exchange built over the Dojima river: upper right depicts a scene where a flag is used to disseminate the price of rice. Painting by Yoshimitsu (1850-1891) </em>

### Overview
Physical settlement under the lens of traditional commodity trading means the actual delivery of the underlying asset upon the expiration of the derivative contract. In this arrangement, the seller of the derivative is obligated to provide the physical commodity, such as crude oil, wheat, or gold, to the buyer. Conversely, the buyer is required to accept and take possession of the commodity. This exchange typically occurs at a predetermined location and involves the transfer of the physical goods. Physical settlement contrasts with cash settlement, where no actual commodity changes hands; instead, the difference between the market price and the contract price is exchanged in cash. In physical settlement, the logistics, storage, and transportation of the commodity play a crucial role and often significantly influence the contract terms and conditions, making it a more complex and operationally intensive process.

Looking at the transaction pipeline of Ethereum, especially in the context of physical delivery of blockspace, validators emerge as the pivotal participants capable of ensuring such delivery. This is because validators have the final say in determining the contents of the canonical block, effectively controlling the inclusion of transactions within the Ethereum blockchain. In this setup, validators can be likened to sellers in a traditional commodity market, with blockspace serving as the asset being traded.
:::info
Note: we are well aware of the construct of PBS. Validators, if so choose , could still propose without MEV-boost; even if when MEV-Boost is chosen, validators retain the ultimate decision-making power regarding which block to select. 

Additionally, we hold the view that a validator's choice of architecture is predominantly profit driven. This is evident in the rate of adoption for MEV-Boost among validators. Should there exist a design that can yield greater revenue, whether through MEV, priority fee, or a combination of both, provided with reasonable ease of use, it is likely to become the preferred architecture.
:::
Drawing a parallel to the physical delivery of commodities, the validator assumes the role of the seller, the blockspace represents the tangible asset, and the buyer is the entity seeking transaction inclusion within a specific block. This dynamic closely mirrors traditional commodity transactions, where a buyer and seller agree upon the delivery of a physical asset at a future date. In the Ethereum context, the "expiration date" of such a contract would correspond to a specific block number, which is the point at which the buyer desires their transaction to be included.

This scenario implies that a buyer, seeking transaction inclusion, enters into an agreement with a validator, where the block number functions as a predetermined deadline for the "delivery" of blockspace. Just as in commodity markets where the delivery date is critical, in Ethereum's blockspace market, the block number signifies the moment of fulfillment of the contract, aligning the concept of physical delivery in traditional commodity trading with the digital realm of blockchain transaction inclusion.

Nevertheless, two significant differences arise, particularly after the introduction of [Proposer-Builder Separation (PBS)](https://ethereum.org/nl/roadmap/pbs/) and [EIP-4844](https://eips.ethereum.org/EIPS/eip-4844), also known as proto-danksharding:

1. Role Shift Post-PBS: With the implementation of PBS, the dynamics of block inclusion undergo a notable change. While validators retain control over which blocks are appended to the Ethereum blockchain, the composition of these blocks is determined by a new entity known as block builders. Validators no longer directly assemble blocks; instead, they receive block proposals from block builders through [relays](https://ethresear.ch/t/relays-in-a-post-epbs-world/16278). In this altered architecture, validators select blocks based on an auction process facilitated by [MEV-Boost](https://github.com/flashbots/mev-boost), where they choose the block that offers the highest bid from block builders. Consequently, validators lose their exclusive influence over block content, effectively positioning block builders as the primary "dealers" of block content to validators.

![image](https://hackmd.io/_uploads/ryMmhSf46.png)


2. Introduction of "Blobs" after EIP-4844: The advent of EIP-4844, or proto-danksharding, brings a novel transaction type into play: "blobs" (Binary Large Objects). This development is aimed at accommodating the data demands of Layer-2 solutions by allowing the posting of "blob" data as an alternative to the costlier calldata utilized by rollups. This innovation not only reduces fees for Layer-2 rollups but also aligns with Ethereum's [rollup-centric scalability roadmap](https://ethereum-magicians.org/t/a-rollup-centric-ethereum-roadmap/4698). In terms of physical block delivery, this results in a dual nature of block content: 
    - regular transactions as defined by EIP-1559
    - the new "blob" transactions introduced by EIP-4844. 

    Block builders will hence be engaged in "dealing" both types of transactions to validators. Moreover, EIP-4844 introduces a distinct fee mechanism compared to the EIP-1559 transaction model.
    
![image](https://hackmd.io/_uploads/SyCdnrMVT.png)


As a consequence of the PBS and EIP-4844, the blockspace futures market in Ethereum is poised to evolve into a more complex and multifaceted domain compared to traditional commodity futures markets. This complexity arises from 
- the introduction of block builders as key market participants, effectively acting as dealers, and 
- the coexistence of two distinct fee structures (EIP-1559 and EIP-4844) within a single delivery vehicle—the blockchain blocks. These developments are anticipated to add novel dimensions to the market dynamics and potential trading strategies within the Ethereum blockspace futures market.

### Market Dynamics

Market behavior fundamentally arises from the interplay of its participants. Within futures markets, this dynamic is shaped by the interactions between buyers and sellers. Historically, commodity producers, such as those in the [crude oil](https://www.cmegroup.com/markets/energy/crude-oil/light-sweet-crude.html) – a market known for its volatility – utilize futures as a hedging mechanism against price fluctuations, facilitating more predictable financial planning. Conversely, buyers engage in futures trading to stabilize their procurement costs amid market uncertainties.

#### Why validators sell blockspace(blobspace) futures

In short, selling blockspace futures could increase the validators' revenue because validators by charging a risk premium. 

Validators, unlike traditional commodity producers burdened with substantial operational overheads, face minimal ongoing expenses; their primary cost is the one-time sunk cost of the 32 ETH deposit required for staking. This unique economic structure influences validators' approach to selling futures – their motivations differ significantly from the producers in traditional commodity markets. It's our opinion that validators are not merely producers of the block, but also the price makers if there exist a futures market for blockspace. As such, validators' primary motivations for selling blockspace futures are driven by profit instead of hedging. 

In markets such like blockspace(blobspace) futures, entities are classified as either price takers or price makers. Within the context of Ethereum, transaction senders would find themselves as price takers, compelled to accept the prevailing price to ensure their transactions are included in a future block. In traditional market, commodity producers are also price takers as they often seek solutions to mitigate the price volatility from commodity trading firms. As such, commodity trading firms such like [Glencore](https://www.glencore.com/), are the price makers that dictate the price in the commodity derivatives market for both supply and demand. As for Ethereum blockspace, validators, unencumbered by the need to hedge their positions, are not not compelled to acquiesce to market-determined pricing. Alternatively, they have great liberty to price the futures given that such market exists. Therefore, validator natually would assume the role of both block production(indirectly through block builders after PBS for validators running MEV-boost) and price maker for blockspace futures. 

Traditionally, being both supply and price maker in the market has tremendous pricing power, which is reminiscent of the influence wielded by major commodity trading firms – the so-called ["Trillion Dollar Club"](https://www.reuters.com/article/us-commodities-houses/corrected-commodity-traders-the-trillion-dollar-club-idUSTRE79R4S320111028/?edition-redirect=uk). These entities, by controlling both production(spot) and trading(derivatives), have historically exerted huge influence over global oil supply with far-reaching political implications. Unlike the ["supermajors" of oil production](https://en.wikipedia.org/wiki/Big_Oil), who only profit when the oil price trends up, commodity trading firms such as [Vitol](https://www.vitol.com/) leverage derivatives to profit in different market conditions. In short, futures provide flexibility for commodity producers to make outsized profit. 


As price makers and block producers, validators possess influence over the content and pricing of the blocks they propose. For every block one proposes, extra profits could be earned by selling blockspace(blobspace) futures with minimum cost to the validator. According to [EIP-1559](https://eips.ethereum.org/EIPS/eip-1559), an average block targets 15M and capped at 30M gas. Theoreticaly, at most of the time the blocks are "half empty". There are always more fees to be earned by including more transactions. 

The validators(or block builders due to PBS) have all the intentions to include as much transactions as possible in their blocks, but the problem is that on average there's only enough transactions willing to pay the current fees to fill up the block at 15M gas. Because of this, blockspace buyers normally have to wait for future blocks when the base fee decreases. This creates a dillemma for entities who want to include their transactions deterministically, such like L2s and bridges. Often times, they have to either wait for longer period of time or overcharge their users. Neither of these are good. Longer wait time means slower finality rate(unless otherwise specified, finality rate means ["hard finality rate"](https://jumpcrypto.com/writing/bridging-and-finality-op-and-arb/)) for L2s, while overcharing is terrible UX. If the validators were to sell blockspace (blobspace) futures, buyers could lock in the transaction fee in advance, thus no more overcharging; and periodic purchase of blockspace futures could allow L2s to have fixed finality rate. To the validator, they are more than happy to include more transactions. Here are how a validator could price the blockspace(blobspace) futures and how the price could be affected by the dynamics between supply and demand: 


##### Pricing the futures

*Note: MEV is ignored for the purpose of pricing as [MEV is roughly only 5% of the revenue per block](https://explore.flashbots.net/) and modeling it would require hyper unrealistic assumptions*

Let's denote the block at which a validator is scheduled to propose as ${B_i}$. The validator's intention to sell blockspace futures in advance hinges on the condition that the futures price($P$) surpasses their expected($E$) gas fee ($BaseFee_{B_i}$ + $PriorityFee_{B_i}$) for that specific block:

$P$ > $E_{Validator}(PriorityFee_{B_i} + BaseFee_{B_i})$

Conversely, a buyer's willingness to purchase these blockspace futures in advance is contingent upon the futures price being lower than their expected gas fee for the same block:


$P$ < $E_{Buyer}(PriorityFee_{B_i} + BaseFee_{B_i})$


If we assume that both the seller (validator) and buyer possess similar levels of sophistication in predicting the $BaseFee$, then the primary variable influencing their decision-making revolves around the $PriorityFee$. For a futures transaction to be mutually agreeable, the buyer's expected priority fee for their transaction must exceed the validator's expectation at ${B_i}$:

$E_{Buyer}(PriorityFee_{B_i})$ > $P$ > $E_{Validator}(PriorityFee_{B_i})$ 

Given that the buyer assumes a long position on volatility and the validator a short position, the buyer should compensate the seller with a risk premium $R$. At an equilibrium state, this relationship can be expressed as:


$E_{Buyer}(PriorityFee_{B_i})$ - $R$ = $P$ = $E_{Validator}(PriorityFee_{B_i})$ + $R$

As price makers, validators have the discretion to determine the magnitude of $R$. However, it is noteworthy that users always retain the option to defer their transaction to a subsequent block if they deem $R$ excessively high. Therefore, a single validator's pricing power is inherently moderated. A reasonable measure of $R$ should be view in the light of expected gas fee volatility in a span of 64 blocks, however, further research is outside of the scope here. 


In a blockspace(blobspace) future market, game-theoretical relationship exists among validators - pricing of one validator might affect the gas price of later blocks. For instance, one tactic validators could employ: 
- To discourage a user from waiting for the next block, a validator could try to sell blockspace futures as much as possible so that the base fee in the next block will be higher. 
    
However, since base fee needs to be burned for every block, streching the future's price too thin will also negatively affect a selling validator's profit. 

Other than transaction volume in preceding blocks, number of futures buyers for a specific block also play critical roles in determining the theoretical price of blockspace futures. To gain a comprehensive understanding of these market dynamics, we propose a framework that takes into account these key factors. This framework is designed to provide a more accurate reflection of the market conditions influencing block space futures pricing.

Suppose we have a function

$d(n, (v_1, v_2, ..., v_k), (m_{v_1},m_{v_2}, ...,m_{v_k}), (p_{v_1},p_{v_2}, ...,p_{v_k})) = (n_1, n_2, n_3, ..., n_k, n_{next}),$ 
where:
- $d$: demand function based on current number of buyers and validators with their pricings. $d$ depends on and may change with time $t$. Max $k$ is $32*2 = 64,$ with reason being that validators are known 2 epoches ahead. Therefore, validators could start selling futures at most 2 epochs ahead, and this give max possible number of validators $k$ is $32 * 2 = 64.$
- $v_i$'s are validators who sell gas future.
- $m_{v_i}$ is the amount of gas futures that have been sold by the validator $v_i$.
- $p_{v_i}$ is the gas future price of validator $v_i$. Future prices will be expectation of real gas fee. If at time $t$ and the future expires at time $t$, the future price is the real gas fee.
- $n$ is the number of people who are willing to buy gas future at current time.
- $n_i$ is the resulting number of gas future bought from validator $v_i$.
- $n_{next}$ is the quantity of individuals choosing to delay their purchase, potentially buying futures during the next block's timeframe.


<ins>Assumptions</ins>

1. Validators hold same expectation of the number of new buyers, $N_t$, at each time $t.$ For those who didn't buy futures, we will also consider them as buyers in the sense that: at time $t$, they buy gas futures which expire at the same time $t$.

2. Validators will start selling blockspace(blobspace) futures as long as they are informed to be a validator 2 epochs later.


The strategy now becomes the determination of future price $p_{v_i}$. These future prices are set in a way that prevents any validator from earning more by changing their prices. This creates a stable situation known as a Nash Equilibrium, where everyone's pricing is in harmony, and no one gains extra by changing their strategy alone.

At time $t_0$, new $32$ validators know that they will become validators $2$ epoches later and begin to sell futures. $t_i$ is the $i$-th block after $t_0$. We will give equations to determine $p_{v_i}$, where $t\in\{0, ... 64\}$:


<ins>Goal</ins>

- Maximize $\sum s_{v(t), t}*(p_{v(t)}-b_t)$, where
    - $v(t)$: The validator responsible for validating the block at the time $t$.
    - $b_{t}$: the expected base fee at time $t$.
    - $s_{v_i, t}$: the expected total number futures sold by validator $v_i$ at time $t$.

<ins>Restrictions</ins>

For each $i$ and $t$,

- $b_{t+1} = b_t * (1+ \max\{\dfrac18, \dfrac{s_{v(t), t}-target}{target}\})$, where
    - $b_{t+1}$: next block's base fee.

- $s_{v_i, t+1} = s_{v_i, t} + d(N_t + n_{next, t-1}, (v(t),v(t+1),...,v(64)),(s_{v(t),t}, s_{v(t+1),t},..., s_{v(64),t}), (p_{v(t)}+b_{t}, p_{v(t+1)}+b_{t+1},..., p_{v(64)}+b_{64}))[v_i],$ where
    - $n_{next,t-1}$: number of buyers who decide to delay their purchases from time $t-1.$
    - $s_{v_i, t+1}$: Total blockspace(blobspace) futures of validator $v_i$ sold at time $t+1$, which corresponds to the time of the upcoming block.

- $\dfrac{d(s_{v(t), t}*(p_{v(t)}-b_t))}{dp_{v(t)}} = 0$
    - Every validator are in local optimal $p_{v(t)}$ such that change of $p_{v(t)}$ won't result in larger profit


<ins>Notes</ins>
- 3rd restriction only claim it is local equilibrium, not global optimization. Possiblly this local condition is enough, but need further check.
- The described process occurs when validators learn they will be responsible for validation. They calculate and set their future prices accordingly. However, with the passage of time, changes in the environment can lead to alterations in the demand function $d$. Consequently, validators might continuously apply the same method, repeatedly solving the previously mentioned optimization problem and adjusting their prices as time progresses and conditions evolve.
- To demonstrate the existence of such an equilibrium, one intuition is to consider its dimensionality. The only unknowns in this scenario are the $p_{v_i}$'s, while the variables $s_{v_i,t}$'s and $b_t$'s are dependent on $p_{v_i}$'s. The third restriction, which involves derivatives equating to zero, represents the actual constraints. Assuming that the optimization problem involves $M$ variables $p_{v_i}$, there would then be $M$ constraints. In a $M$-dimensional space, each constraint could be viewed as a $M-1$ dimensional hypersurface. Generally, the intersection of $M$ such hypersurfaces exists.
- The pricing model is based on a straightforward prediction of the number of buyers $N_t$ at a given time $t$, along with the demand function at that time. It presumes a deterministic model of these values over time. This approach could be extended to probabilistic models, necessitating some alterations to the equations. However, the fundamental concept remains unchanged.



#### Why buyers buy blockspace(blobspace)?
<ins>Roll-ups</ins>
- Overview
    Layer 2 operators have high demands for blockspace(blobspace). As of Nov 2023, L2 operators' smart contracts are some of the most gas consuming contract on Ethereum Mainnet. 

    ![image](https://hackmd.io/_uploads/HJ-euZBSa.png)<ins>Top 20 Gas Consuming Smart Contract from [the Block](https://www.theblock.co/data/on-chain-metrics/ethereum/top-20-gas-consuming-smart-contracts-30d)</ins>

    To understand why roll-ups contracts spend so much on gas, here is primer on how an optmistic roll-up works:
    :::info
    **Lifecycle of a transaction on an Optmistic roll-up**
    
    The lifecycle of a transaction on an optimistic roll-up involves several key steps:

    **Initiation**: A user initiates a transaction through wallets such like MetaMask. MetaMask formats and signs this transaction like a regular Ethereum transaction. Then, MetaMask sends the transaction to the optimistic rollup's RPC endpoint. This endpoint is a rollup node that routes the transaction to the Sequencer.

    **Sequencing**: The Sequencer receives the transaction, validates it, and orders it among other received transactions. 

    **Batch Posting**: Periodically (normally less than 3 minutes), the Sequencer posts batches of transactions to the Ethereum contract. This action canonicalizes the transactions and their order, implicitly determining the Layer 2 (L2) state. Anyone executing these transactions in the specified order would reach the same L2 state.

    **State Validation**: L2 validators read the posted transactions and execute them to update to the new L2 state. They then make an on-chain assertion about the chain's latest state using the Merkle Root of this new state. 

    **State Canonicalization**: If no challenges to the new rollup state are made within a certain period (typically around 7 days), the state is then considered canonicalized and final.
    :::
    
    In the above steps, **batch posting** is particularly expensive. For every batch, [there are two costs associated](https://forum.celestia.org/t/ethereum-rollup-call-data-pricing-analysis/141):

    - Fixed Costs(cheap and fixed):
        - Proof costs (in the case for zk rollups): ranges in gas, typically based on rollup provider
        - State write costs: 20,000 
        - Ethereum base transaction cost: 21,000
    - Variable Costs(expensive and dynamic):
        - `calldata` to Ethereum L1
        - L2 gas fees 
        
    ![image](https://hackmd.io/_uploads/S1VXCEUHT.png)<em>Share of Transaction Fees from [ Optimism: OP Mainnet - L2 Transaction Fees, L1 Data Costs, Sequencer Fees](https://dune.com/optimismfnd/optimism-l1-batch-submission-fees-security-costs). For the *Variable Costs*, on average L2 gas fees are comparatively cheaper. 
</em>
    
    As Ethereum has adopted the [roll-up centric roadmap](https://ethereum-magicians.org/t/a-rollup-centric-ethereum-roadmap/4698), scaling through L2s is the next big challenge. As *L1 data fees* are the major bottleneck for L2s, reducing the *L1 data fees* becomes the utmost important task. 
    
    [EIP-4844: Proto-Danksharding](https://www.eip4844.com/) aims to address the L1 data bottleneck. On a high level, Proto-Danksharding is a "prototype" of full Danksharding. Full Danksharding is a proposal for implementing data sharding in Ethereum. Unlike previous sharding proposals where 64 proposers independently propose shard blobs, Danksharding centralizes this process, assigning block builders the task of processing all shards.  
    
    As a "prototype", EIP-4844 introduces a new transaction format for rollups - "blob" or "binary large object". These blobs, about 128 KB each, are more cost-effective than equivalent calldata(roughly ~16x more efficient by back-of-the-envelope math) and are pruned from nodes after a month, reducing long-term storage demands. This pruning aligns with data availability (DA) security assumptions. Several things to highligh:
    - Blobs are similar to 1559 typed transactions but has an extra field `max_fee_per_data_gas` to specify willingness to pay for data gas;
    - Proto-danksharding introduces a multi-dimensional fee market, where there are two resources, gas and blobs, priced seperately;
    - There will be at most 6 blobs per block initially;
    - Block builders will have to pick up the blobs from the mempool;
    - Blobs do not have to be used for L2 data. JPEGs? Yes! 
    
- Demand for blobspace futures

    The demand for blob space by rollups is contingent upon two primary factors: 
    - the need to maintain positive budget balance
    - the need to maintain a constant finality rate 

    Rollups face a problem to maintain positive budget balance when they quote users for L1 data publication cost. This happens because a L2 user is quoted before a transaction batch is submitted to L1, and only by then the exact L1 blob(calldata pre-4844) gas fee could be known. [Ed Felten had a good talk about this titled "Fair and sustainable fees for L2" at Devconnect 2022](https://www.youtube.com/watch?v=JfaxBythV4Q). 
    
    ![image](https://hackmd.io/_uploads/H1IkgdwST.png)<em>Lifecycle of a Transaction on a Optmistic Rollup from [Fair and sustainable fees for L2](https://www.youtube.com/watch?v=JfaxBythV4Q). User would receive "soft finality" at time T, but data is not posted to L1 until T3. The problem is how to charge L2 users L1 data fees at time T</em>

    The current solutions are either taking a running average of base fees, or overcharge the user. Blobspace futures could solve the problem by locking down the price in advance. 
    
    In addition to the need of positive budget balance maintenance, Rollups need to commit to L1 periodically to gaurantee transaction finality.  In a hypothetical scenario where gas incurs no cost, every L2 entity would aim to post data to L1 in each L1 block so that every L2 transaction is finlized immediately thus "borrows" L1's security. In a way, finality drives L2's continous demand for L1 blobspace. For reference, Optimistic Rollups such as Arbitrum and Optimism, compresse and post L2 transactions in batches as Ethereum calldata at constant intervals ([every 1-3 minutes on Arbitrum](https://arbiscan.io/batches?ref=jumpcrypto.com) and [30 seconds to 1 minute on Optimism](https://optimistic.etherscan.io/batches?p=3&ref=jumpcrypto.com)). Such demand inversely correlates with the level of congestion in a <ins>rollup's blockspace</ins> - high L2 congestion renders the demand for L1 blobspace inelastic. Here, congestion measures the users' demand for a <ins>rollup's blockspace</ins>, which is limited especially in events of high network traffic. Inadequate management of this demand leads to [delayed "hard finality"](https://jumpcrypto.com/writing/bridging-and-finality-op-and-arb/). 
    
    During high-demand periods for blobs, L2s may find themselves competing for the limited availability of 6 blobs per block. If all available blobs are used in a previous block, the cost for next block's blobs is set to [rise exponentially](https://eips.ethereum.org/EIPS/eip-4844#blob-gasprice-update-rule). Blobs will become increasingly scarse if some L2s decide to intentionally buy up the blobs to cause delays in other L2s and jack up the price of blobs in the next blocks . Situations like these force roll-ups, especially those beyond the first 6, to incur higher costs to maintain their finality rates. The longer a rollup waits to make its commitment, the more inelastic its demand for blobspace becomes, as it faces escalating costs. There are leeways 

    Blobspace futures offer a solution to this challenge. By securing blobspace up to 64 blocks in advance, rollups can effectively sidestep the competitive and fluctuating market dynamics similar to a [Priority Gas Auction (PGA)](https://www.mev.wiki/terms-and-concepts/priority-gas-auctions). 
    
    The competition of blobs could become ultra competitive as more use cases of blobs are explored. One of the non-conventional use case of blobs are [on-chain NFTs](https://hackmd.io/@snakajima/HJva6n-Jj) that only need to exsit on-chain momentarily, such like [rental NFTs](https://eips.ethereum.org/EIPS/eip-4907) or [ticket NFT](https://oveit.com/nft-tickets/). By the end of the day, people will try to put data on-chain if the cost is low enough. 
    
    In the medium to long term, we expect that a secondary market for blobspace futures may emerge. This market would likely involve sophisticated market makers acquiring blobspace futures from validators and subsequently selling them to buyers. The rationale for such a market stems from the observation that not every rollup fully utilizes the space provided by a single blob. Economically, it is practical to allow multiple rollups to share a single blob. Market makers that could partition the blob and sell the blobspace to multiple parties could charge a premium for service. The pricing of these "sharded" blobs, requires a high degree of financial acumen. Therefore, this activity is best conducted by entities that specialize in financial engeineering and possess the necessary expertise to navigate such a market effectively. For more economical analysis of blob and cost sharing strategies, please refer to [*EIP-4844 Economics and Rollup Strategies*](https://arxiv.org/abs/2310.01155).

<ins>Bridges</ins>
- Cross-chain bridges, which facilitate messaging or asset transfers between different chains, often use gas estimations to determine the gas fees users must pay upfront. The estimation process is designed to ensure that the amount calculated is always more than sufficient, thus eliminating the need for the system to cover any gas fees. While any excess amount is ultimately returned to the user, this mechanism leads to a suboptimal user experience. Users are consistently required to overpay initially and then endure a waiting period for the reimbursement of the excess fees.
    
    For example, this is how [Axelar](https://axelar.network/) settles gas across different chains:
    :::info
    Deployed on all connected EVM chains, Axelar's the Gas Receiver contract enables users to cover all transaction fees associated with their cross-chain message in a single payment on the source chain, using the native token of that chain. 
    
    First, The Gas Receiver calculates the total gas cost across the source chain, Axelar network, and destination chain. It then converts the source-chain tokens (or any supported token) into AXL, destination-chain tokens, and other necessary currencies to cover these costs. The contract would charge extra on the source chain, and refund any excess gas.
    
    ![image](https://hackmd.io/_uploads/Syc8AFPST.png)<em>From [Axelar gas and executor service](https://docs.axelar.dev/learn/network/flow#gas-and-executor-services)</em>
    :::
    
    To effectively address the issue of overestimating gas fees for users in cross-chain transactions, bridge operators have the option to purchase blockspace futures in advance. By securing these futures, operators can lock in the transaction fees well before the execution of a user's transaction. This preemptive approach eliminates the need to charge users any additional fees beyond the actual cost. Consequently, it ensures a more transparent and predictable fee structure, enhancing the overall user experience by providing clarity and reliability in transactional costs.

    
<ins>Cross-domain MEV</ins>
- Cross-chain MEV typically involves arbitrage across multiple blockchain networks. The primary challenge in this domain is the absence of atomic transactions across different chains, resulting in a non-atomic nature for current cross-domain MEV activities. This non-atomicity introduces execution risks and requires higher capital for operations compared to MEV on a single chain.

    Blockspace futures offer a solution to this challenge by enabling atomic execution of cross-chain transactions. By securing the blockspace on a destination chain, one can guarantee the right to execute transactions at a predetermined time given. This method reduces the execution risk associated with cross-chain MEV. Cosmos pioneered a similar design by leveragring blockspace futures to capture cross-chain MEV:
    :::info
    **Cosmos Interchain Scheduler**
    
    The Scheduler system operates through the following mechanism:

    When a consumer chain activates the Scheduler module, it can engage in a cross-chain contract to allocate a specific portion of its block space, such as one block every minute, for sale in the marketplace. 

    Following the establishment of this contract, the Scheduler generates NFTs that represent reservations for each future block segment on the consumer chain. These reservation tokens, encompassing all participating chains, are then auctioned in batches at regular intervals.

    The tokenized reservations have the option to be traded on secondary markets. Trading can continue until the reservation is redeemed. Redemption involves presenting the token to the designated validator on the partner chain, along with the specific transaction sequence that needs to be executed.

    After the successful execution of a block, a portion of the revenue generated from the Scheduler auction is remitted back to the partner chain. This revenue sharing is a key aspect of the system, creating a mutually beneficial arrangement between the participating chains.
    
    ![image](https://hackmd.io/_uploads/SyBRVowB6.png)<em>From [The Cosmos Hub](https://gateway.pinata.cloud/ipfs/QmWXkzM74FCiERdZ1WrU33cqdStUK9dz1A8oEvYcnBAHeo)</em>
    :::
    A similar design could work for Ethereum, only that the inter-chain communication needs to be handled by the buyers themselves as Ethereum itself does not have native cross-domain communication protocols. However, with [SUAVE](https://writings.flashbots.net/mevm-suave-centauri-and-beyond) on the horizon, multi-chain blockspace futures could be implemented for the purpose of cross-domain atomicity as [SUAVE itself does not guarantee atomic inclusion of cross-chain transactions](https://joncharbonneau.substack.com/p/rollups-arent-real). 


<ins>Wallets & Dapps</ins>
- Wallets and dapps that aim to subsidize all or a portion of their users' gas fees also exhibit a significant interest in blockspace futures.

    For wallets, offering differentiated services to their users is a key business strategy. One approach to achieve this is by covering part or all of their users' gas fees in return for a membership subscription. To effectively handle the financial risks associated with fluctuating gas costs, blockspace futures emerge as an optimal solution. The ideal scenario involves forming a long-term, retainer-like arrangement with a liquid staking protocols that sell blockspace futures. Such an agreement would allow for the advance purchase of blockspace futures, not just 64 blocks ahead but on a more extended timeline—weekly, monthly, or even quarterly. This strategy would facilitate more efficient and convenient management of gas fee liabilities, aligning with the business objectives of wallets and dApps in enhancing user experience and loyalty.
    
    For dapps, similar strategy could also be employed to bootstrap initial users. Moreover, dApps that assure users of transaction execution regardless of fluctuations in gas prices can also benefit from utilizing blockspace futures to stimulate user engagement. For example, for the [Cow Protocol](https://cow.fi/), there exists a time lag between when a user's order is accepted and when it is actually executed on-chain. [The protocol itself bears the burden of any gas price differential during this interval](https://docs.cow.fi/off-chain-services/api/fee-mechanism). However, by employing blockspace futures, the protocol can secure the gas fee in advance, allowing it to potentially transfer the cost of the futures premium to the users.

    Furthermore, in dApps where the involvement of external parties is crucial for system operations, such as in governance processes, blockspace futures can be leveraged to incentivize participation.

### Designing a Blockspace(Blobspace) Futures Market for Ethereum
A well-structured futures trading market demands a clear framework that delineates the roles of buyers and sellers, the means through which they express their transactional intentions, the settlement mechanism, and risk management measures. The essential elements of a functioning futures market for Ethereum blockspace, can be summarized as follows:

- #### Underlying Asset
    - The primary asset in this context is blockspace, which is analogous to a property right allocated every 12 seconds to the most recent block on Ethereum.

        The value and utility of blockspace are not uniform, drawing a parallel to real estate where location significantly influences price. Factors such as proximity to essential services affect real estate value, while in blockspace, the placement within a block is critical, primarily due to the potential for MEV. Typically, the top and bottom positions within a block are considered prime locations due to their higher propensity for MEV opportunities.

        Nevertheless, not all transactions demand specific placement within a block. For instance, 'blobs' may simply require inclusion in a block, regardless of their specific location. This concept is referred to as the *Heterogeneity of Blockspace*, by the authors of ["Opportunities and Considerations of Ethereum’s Blockspace Future"](https://frontier.tech/ethereums-blockspace-future). It highlights a market divide: some participants seek mere transaction inclusion (i.e. for congestion), while others may pay substantially higher rates for specific placements (top or bottom of a block) within the block(i.e. for contention). Analytical data from July 2023 indicates that a predominant portion of users pay for inclusion due to congestion. 
        ![image](https://hackmd.io/_uploads/ryUej_X4p.png)<em>Gas Price (in wei) of the Proposer Payment (Effective gas price - Base gas price) by Location of a Transaction in the Block. From [Congestion vs. Contention](https://github.com/ankitchiplunkar/crypto_charts/blob/master/notebooks/Congestion%20vs%20Contention.ipynb)</em>

        Dojima focuses exclusively on the block inclusion for primarily two reasons:
        1. The demand for transaction inclusion outwights the demand for transaction contention;
        2. More importantly, blockspace futures for transaction contention could make Multi-block MEV(MMEV), especially TWAP-based oracle manipulation much easier even for non-validators, thereby posting a threat to the overall network health.
            :::warning
            imagine one could buy bottom position then top position on two sequenctial blocks and effectively manipulate the price on Uniswap V2 without arbitragers' intervening backruns
            :::
            MMEV is not the central topic of this article. For interested readers, please consider reading ["TWAP Oracle Attacks: Easier Done than Said?"](https://eprint.iacr.org/2022/445.pdf). 
                
- #### Unit of Measurement
        
    - In a manner similar to traditional commodity markets, where standardized units such as "bushels" are employed for settlement purposes, the Ethereum blockspace futures market should utilize the unit of gas as its principal metric. This unit is indicative of the transaction execution cost on the Ethereum network.

        Adopting a unit-based system is advantageous for blockspace (futures) as it provides a convenient and efficient method for accounting. In the context of blockspace futures, gas is the logical choice for the unit of measurement. Meanwhile, for blobspace futures, the appropriate unit would be "blobs." To facilitate ease of transfer and foster a liquid market, we follow the approach of the [Cosmos Interchain Scheduler](https://gateway.pinata.cloud/ipfs/QmWXkzM74FCiERdZ1WrU33cqdStUK9dz1A8oEvYcnBAHeo). In this model, each unit will be represented by a NFT, where "gas credits" could be freely transfered pre-execution.
        

        Another layer of complication comes from the fact that, validators, who assume the role of sellers in this market, must understand the gas limit of each block(up to 30 million gas & maximum 6 blobs for EIP-4844 blobs). This understanding is crucial as it delineates the maximum amount of gas, and by extension, the maximum number of transactions and the gas cost of each transaction, that can be accommodated within a single block. The block gas limit thus becomes a critical factor in determining the quantity of blockspace that validators can feasibly offer for sale, ensuring that commitments made in futures contracts align with the technical and practical constraints of block production on the Ethereum network. 


- #### Initiation, Expiration & Settlement
    - A validator will be able to start selling the blockspace futures as soon as a he/she is notified of his/her duties for an upcoming epoch by calling the Beacon node's [`getProposerDuties` API](https://ethereum.github.io/beacon-APIs/#/Validator/getProposerDuties), or using a service such as [block-proposer-schedule](https://wenmerge.com/block-proposer-schedule/). A validator should have the knowledge of his/her upcoming duty two epochs out, giving maximum 12.8 minutes lookahead into the future, as each epoch has 32 slots and each slot is 12 seconds. 
    
        The Dojima blockspace futures will expire on the block a selling validator successfully propose a block, before the futures settle. 
        
        As for settlment, the blockspace futures are settled only after the block is confirmed to be canonical. The primary reason for canonical block confirmation is because Dojima will leverage [Axiom's zk-coprocessor](https://www.axiom.xyz/) to perform fraud-proof challenge, which requires the queried block to become canonical. 


- #### Pricing 
    -  The pricing mechanism for blockspace futures is expected to be governed by the interplay of demand and supply dynamics, which, in the Ethereum context, presents unique characteristics distinct from traditional commodity futures markets. In conventional commodity markets, futures are typically traded with multiple sellers and buyers engaging simultaneously. However, the structure of blockspace futures in Ethereum deviates from this norm due to the presence of a singular seller—the block proposer—operating in discrete 12-second intervals.

        Drawing an analogy from commercial aviation, the market dynamics of blockspace can be likened to the seating arrangement in an airplane. In this market, certain transactions, notably those consuming more gas, could occupy multiple 'seats', while 'blobs' introduced by EIP-4844 may be deemed as a the first-class where only a limited amount of space is offered per block. 
        
        Refer to ["Pricing the futures"](https://gateway.pinata.cloud/ipfs/QmWXkzM74FCiERdZ1WrU33cqdStUK9dz1A8oEvYcnBAHeo) section for detailed analysis. 
        


- #### Margin Requirements
    -  Traditionally, seller of futures will be required to post margins as a measure of counter-party risk for the futures buyers. When a seller enters into a futures contract, they are required to deposit a margin. This margin acts as a form of security deposit to protect against the risk of loss from adverse market movements and ensures that the seller has a financial stake in the contract. 
    
        In the context of blockspace futures, validators have natural margins since every validator is required to stake 32 ETH. However, the stakers slashing mechanism does not take blockspace futures into consideration. To re-purpose a validator's stake for margin requirement, Dojima will leverage [EigenLayer](https://docs.eigenlayer.xyz/overview/readme/whitepaper) to allow validators re-staking their stakes as futures' margins. In events of non-fullfillment of buyers' transaction, a validator would be slashed. In other words, if a validator wishes to opt into blockspace futures selling, he/she needs to re-stake on EigenLayer first.
        
### Protocol Description
**Note: This section is not meant to be read as technical specs. The technical details are intentionally left out* 

#### Basics
![bidding](https://hackmd.io/_uploads/SJw4djA4T.png)<em>Blockspace Market Timeline</em>

   - **Epoch-Based**: Each trading round in the blockspace(blobspace) futures exchange starts with two [epochs](https://developers.flow.com/references/run-and-secure/staking#epochs), 12.8 minutes out. 
   - **Validator Participation**: Upon the beginning of a new epoch, the 32 designated validators are eligible to start selling their blockspaces(blobspaces).
   - **Blockspace**: Validators can specify the exact amount of blockspace they wish to sell, ensuring the total does not exceed the maximum gas limit per block, set at 30 million;
   - **Blobspace**: Validators also have the option to sell blob space, adhering to the limitation that the total blobs sold must be under (maximum [6 blobs](https://youtu.be/dFjyUY3e53Q?si=PBXcfNT0ZYj-6tMo&t=4670) for EIP-4844 blobs).
   - **Buying Range**: Buyers can purchase blockspace for future blocks, ranging from the immediate next block to up to the last block in the same epoch.
   - **Proposer Commitment**: upon the validator signaling a commitment to include a transaction or blob, he/she will be penalized for violating the commitment.

#### Buying & Selling
In terms of how buying and selling of blockspace are processed, how the information are exchange among different parties, and how buyers and sellers are protected from any adverse actions from counter-parties, there are three design options, each with its own tradeoffs:

- <ins>**Bid commitments through EVM state transition**</ins>: Under this approach, each bid will be reflected as a state update on EVM. In other words, buyers' bids will be recorded on a smart contract to officiate the validator's commitment. 
    
    On the smart contract, the function taking the bid should evaluate the bid according to a seller specified bid evaluation metric and if succeeds, update the mapping of the seller inclusion list. 
    
    If the block a validator will propose is `block n`, then the last block a validator will accept bid is `block n-1`. At `block n`, the block has to include a transaction calling the `merklize` function, which merklize of all of the hashed `Bids` belonged to a validator in the `inclusionList`([same name but should not be confused with the inclusion list in the context of censorship resistance](https://notes.ethereum.org/@fradamt/forward-inclusion-lists)) and update a mapping, `merkleRootList`, which will be used for fraud proof later. 
    
    For reference, a rough smart contract implementation would look like this:
    ```solidity
        contract BlockSpaceAuction{
            struct Bid {
                address sender,
                uint fee,
                // Other fields
            }

              // Modifier to restrict function access to only validators
            modifier onlyValidator() {
                //  logic to determine if msg.sender is a validator
                _;
            }

            // validator address => (block number => array of Bids)
            mapping(address => mapping(uint256 => Bid[])) public inclusionList;
            // validator address => (block number => merkle root)

            mapping(address => mapping(uint256 => bytes32)) public merkleRootList;

            // A simple heuristic for validator to include a bid by calculating the fee per gas used for a transaction. 
            // The gas needs to be simulated off-chain using RPC methods like `eth_call`
            function addBid(Bid bid, uint256 blockNum, uint256 gas, uint256 baseLine) onlyValidator public {
                uint fee = bid.fee;
                uint feePerGas = calculateFeePerGas(fee, gas);
                require(feePerGas>baseLine, "bid too low");
                bids[msg.sender][blockNum].push(newBid);
            }

            // Function to calculate the fee per gas for a given bid
            function calculateFeePerGas(uint256 fee, uint256 gas) public view returns (uint256) {
                return gas / fee;
            }

            // Function to create a Merkle root from Bids in the inclusionList
            function merklize(address validator, uint256 blockNum) public view returns (bytes32) {
                Bid[] memory bids = inclusionList[validator][blockNum];
                require(bids.length > 0, "No bids to merklize");

                bytes32[] memory leafNodes = new bytes32[](bids.length);
                for (uint256 i = 0; i < bids.length; i++) {
                    leafNodes[i] = keccak256(abi.encode(bids[i]));
                }
                bytes32 root = computeMerkleRoot(leafNodes);
                merkleRootList[validator][blockNum] = root;       
                return root
            }

            // Internal function to compute Merkle root from leaf nodes
            function computeMerkleRoot(bytes32[] memory leafNodes) internal pure returns (bytes32) {
                uint256 count = leafNodes.length;
                while (count > 1) {
                    for (uint256 i = 0; i < count / 2; i++) {
                        leafNodes[i] = keccak256(abi.encodePacked(leafNodes[i * 2], leafNodes[i * 2 + 1]));
                    }
                    count = (count + 1) / 2;
                }
                return leafNodes[0];
            }
        }
    ```
    After the block is successfully built, any challenger could query the merkle tree and the `inclusionList` using [Axiom](https://docs.axiom.xyz/introduction/what-is-axiom) to challenge whether the transactions in the transaction list are fully included. 
    
    To ensure the compatbility of this design, it is crucial that block builders need to be cognizant of the transactions specified in the `inclusionList`. The successful implementation of this mechanism requires a structured coordination effort from relays. This coordination presents an opportunity for relays to earn additional fees for providing this integral service.

    On a parallel note, it's worth considering alternative frameworks such as [MEV-Boost+](https://hackmd.io/@layr/SkBRqvdC5) where validators could build blocks fully or partially.
                                                 
- <ins>**Bid commitments through a modified relay**</ins>
        An alternative design is possible with the use of relays to bypass frequent state updates. Currently, validators use [relays](https://beaconcha.in/relays) to outsource block production. 
        
    :::info
    **Primer on Relay**
        Relays play a crucial role in the PBS architecture, functioning as a trusted intermediary between block-builders and validators (block proposers). Within this framework, relays facilitate a competitive auction environment for each block, where multiple block-builders submit bids, consisting of block contents and associated proposer fees. The auction, lasting approximately 12 seconds, determines the winning bid based on the highest proposer fees.

    During the auction, relays receive and validate the block contents from block-builders, ensuring both the validity of the block and the promised proposer fees. Post-validation, bids are activated for consideration in the auction. At its conclusion, validators request the block header with the highest bid from connected relays. It's important to note that the relay must be trusted by the block buiders and validators.

    The chosen block header is then signed by the validator and returned to the relay. The relay, upon verifying the signature, shares the full block contents with the validator and also broadcasts the block over the peer-to-peer network. This process emphasizes the need for trust in relays by both block-builders and validators due to their central role in managing and disseminating critical block information. 
    :::
     
    Due to relay's unique ecological niche, they could facilitate bid expression from the users and enforce validator commitments, most importantly, for profits especially given that relays are operating at a loss currently. 
    
    Relays can function as a middleware between validators and blockspace (or blobspace) buyers, streamlining the bid submission process. In this model, rather than buyers submitting bids directly to validators and committing them to a smart contract, a specialized relay aggregates these bids for the validators. Upon receiving a new bid, the relay forwards it to the validator for consideration. If the validator opts to accept the bid, they would
    1. Send a confirmation message back to the relay, signaling their commitment to include the bid.
    2. Store the buyer's transaction locally.
    ![relay](https://hackmd.io/_uploads/rkcASe24a.png)<em>Relay as Middleware for bid aggregation</em>

    When it's time for the validator to propose a block(if MEV-Boost+), they grant the relay the authority to insert a transaction to the block. This transaction, crafted by the relay, generates a Merkle root off-chain, analogous to the `merklize` Solidity function from aboce, and then invokes a specific function on the smart contract to record this Merkle root. In the same function call, the payout from the buyers to the validator will be transfered in batch. The stored Merkle root can later be accessed, using coprocessor like Axiom, for challenge purposes.
        ![merkle](https://hackmd.io/_uploads/rylbTxhE6.png)<em>Transaction merkle tree</em>
    
    
    ![payout](https://hackmd.io/_uploads/ByMsne2E6.png)<em>Payout to the validator</em>
    
    This design also requires block builders to be aware of what transactions need to be included during block construction. 

    **Advantages**:
    - Reduced Gas Fees for bid submission: By circumventing the need for buyers to submit bids via EVM state transitions, this method remove gas fees for bid submissions.
        - Gas Efficiency for Merkle Root Generation: Generating the Merkle root off-chain enhances gas efficiency, as this computation no longer consumes on-chain resources.

    **Disadvantages**:

    - Centralization: This approach introduces a dependency on a centralized entity – the relay. While relays inherently possess a degree of centralization, their role is expanded to include additional services, potentially justifying a service fee. However, this centralization may raise concerns regarding trust and reliance on a single point of control or failure in the market.

    In summary, using relays as a middleware in the bid submission process presents a trade-off between efficiency and centralization. While it offers gas savings and streamlined operations, it shifts some market dynamics towards reliance on centralized relays. Nonetheless, given that relays are already a central component of the system, this approach can be seen as a pragmatic adaptation to enhance market functionality. 
    
- <ins>**Bid commitments through a customized roll-up**</ins>
        There are functional similarities between a relay based design elaborated above and the architecture of Optimistic rollups. Therefore, a special purpose roll-up could serve as an alternative to the relay based design to mitigate the risk of centralization. The fundamental elements of Optimistic rollups comprise:

    - Transaction Sequencing: This process encompasses the reception, validation, sequencing, and batching of transactions prior to their submission to L1. 

     - State Update: 
        - A contract for posting Layer 2 (L2) transactions (such as the `Inbox` in Arbitrum or `CanonicalTransactionChain` in Optimism).
        - A contract for posting the new L2 state roots after transaction execution (known as the `Outbox` in Arbitrum or `StateCommitmentChain` in Optimism).
        - A contract for managing challenges and fraud proofs (termed `ChallengeManager` in Arbitrum and `BondManager` in Optimism).

    - State Finalization: The rollup state achieves canonical status if no disputes or challenges emerge within a predetermined timeframe, typically spanning approximately 7 days.

    Drawing an analogy, the role of the relay could potentially be substituted by a special purpose rollup. In such a scenario, once a validator confirms a buyer's bid, the transactions are sequentially arranged in a First-In-First-Out (FIFO) order by the sequencer. The sequencer would then commit a Merkle root and transactions to L1 like an optmistic rollup would. The difference is the Merkle root serves one extra purpose: ensuring the validator's inclusion of the buyers' transactions. 
    
    To send the bid, the buyer first submits their bid to the validator; upon acceptance, the bid confirmation is forward to the sequencer. Given the rollup's minimalistic nature, a [based rollup](https://ethresear.ch/t/based-rollups-superpowers-from-l1-sequencing/15016) design is particularly apt. Any re-staked validator might act as the transaction compressor, fetching transactions from dedicated mempool then forwarding transaction data and state root to a block builder or directly to the validator(if not  MEV-boost), thereby earning additional fees. For data availability, [EigenDA](https://www.blog.eigenlayer.xyz/intro-to-eigenda-hyperscale-data-availability-for-rollups/) is a convinient choice. 
    
    Alternatively, light weight rollups such as [Stackr](https://www.stackrlabs.xyz/) are also suitable for the job. 
    
    A more MEV coucious design could introduce further incentives for the sequencer, such as allowing the sequencer to order received bids arbitrarily.
    
    The comprehensive design of such a rollup, however, encompasses complexities that extend beyond the scope of this document. 


#### Challenge Mechanism
To challenge a transaction inclusion, a challenger should 
   - use the [Axiom](https://www.axiom.xyz/) to query the merkle root inside of the `inclusionList` mapping by keying in the validator address and the block number
   - then, generate the merkle root by providing the same block number, with other relevant block info such like transaction index
   - if the merkle roots from step 1 and 2 are the same, challenge failed. Otherwise, challenge succeeds and the validator's [withdraw credential on Eigenlayer](https://docs.inceptionlrt.com/introduction/eigenlayer#slashing-on-eigenlayer) will be negatively affected. 

In summary, the blockspace futures exchange process in Ethereum is structured around epochs, with validators selling blockspace, and state updates managed through a smart contract or an optimistic rollup. Transactions are included by validators directly or via relay-verified block builders, with a challenge mechanism in place to ensure the integrity of the transaction inclusion process.



## GIX(Gas Index) Market - A Cash-settled Derivative Market for Ethereum Gas Fees

![image](https://hackmd.io/_uploads/Synt6GyIp.png)<em>Men working the floor at the Chicago Board of Trade circa 1949. From ["Photos: After 167 years, Chicago Mercantile Exchange closes futures trading pits"](https://fortune.com/2015/07/06/chicago-mercantile-exchange-closes-futures-trading-pits/)</em>



### Cash-Settled Derivatives Market for Ethereum Gas

We aim to design a cash-settled derivatives market for Ethereum gas, where users could hedge and speculate the Ethereum gas much like the commodities in the traditional financial market. 

### Market & Reference Rate Design 

The cash-settled base fee market bears striking resemblance to the derivatives market of [VIX(The Volatility Index)](https://cdn.cboe.com/api/global/us_indices/governance/VIX_Methodology.pdf). The VIX market emerged from late 80s and early 90s financial economics research, suggesting volatility indices as a basis for futures and options. Similar to a market index, a volatility index like the VIX enables speculation on market-wide volatility. Traders use it to bet on future market uncertainty and to hedge against downturns, where volatility rises but equity portfolios may decline. The VIX market structure mirrors the current gas market on Ethereum, where the underlying gas, a measurable attribute of Ethereum blockspace, isn't directly tradable. 

The GAS market is structurally similar to VIX, where a artificial index value is used for reference. Much like VIX, whose traders are mostly speculators and hedgers, cash-settled derivatives will be mostly used for hedging and speculation, where physical delivery is not nocessary. 

Additionally, both the VIX and Ethereum's gas market display a mean-reverting pattern. The VIX is derived from the pricing of out-of-the-money put and call options on the S&P 500 index, reflecting market expectations of future volatility; on the other hand, Ethereum's base fee is determined based on network congestion in previous blocks, mirroring participant expectations of upcoming network traffic as users opt to pay the current fee in anticipation of higher fees in subsequent blocks. These anticipatory behaviors typically self-correct over time, leading to fluctuations around a central value. In essence, both metrics serve as leading indicator for their respective markets—one gauging market volatility and the other network congestion.

Therefore, much like the design of VIX, the creation of a standardized reference rate for gas becomes crucial for the successful operation of cash-settled derivatives. The introduction of EIP-1559 simplifies this process further by providing a reliable "oracle" for assessing block space congestion, thereby facilitating more accurate and efficient settlements.

To reference the base fee and settle options, we'll use [Axiom](https://www.axiom.xyz/) extensively. The benefits of using Axiom zk-coprocessor are
1. keeping the protocol "oracleless": we don't have to trust any oracle to query the historical base fee or any calculations over base fees
2. keeping the protocol stateless: only initial parameters of option contracts need to be "stateful". Any further data inquries are queriable from Axiom to keep the smart contracts light
3. delayed settlement: just-in-time settlement from keepers is not needed since we could always query the historical block data for settlement purposes given a block number


The calculation of the option strike price will be determined using the formula: " $Fee_T$ / $GAS$", where $T$ represend the period over which $Fee$ will be calculated. At the time of settlement, the payout will be calculated as the difference between the Current and Strike values of " $Fee_T$ / $GAS$", with an additional process of "truncation" applied, which will be explained in further detail later.

The decision to take time based calculation over base fee, rather than using the actual base fee for each block, is a strategic one aimed at mitigating the risks associated with potential collusion among validators. In practical scenarios, it's conceivable that validators could collude to manipulate base fee. By taking a calculation of base fee over an extended period, the system increases both the cost of such manipulation. 

Further quantitative research is planned to fine-tune the reference rate's timeframe, striking an optimal balance between minimizing the risk of base fee manipulation and maintaining the tractability of the reference rate.

### Base Currency
*GAS* is an ERC-20 token that maintains a consistent peg to ETH at a index value $I$:



${I}_{GAS}$ = $\frac{1}{T}$ $\int_{t=0}^{T}$ $F(t)$  $dt$


Where:

- ${I}_{GAS}$: Time-Weighted Average Price of the base fee over the time period $T$.
- $T$: The total duration of the time period for which the average is being calculated.
- $F(t)$: The base fee at a specific time $t$ within the time period $T$.
- $\int_{t=0}^{T}$ $F(t)$  $dt$: The integral of the base fee over the time period from $t=0$ to $T$, which calculates the cumulative fee over the entire period.

The GAS will largely based on the design of [Liquity](https://docs.liquity.org/), which in our opinion is the best stable asset design there is. 


### Financial Instruments


#### Truncated-Option (T-Option)(GIX V1)

- Description

    T-Option is like classic option with underling asset as base fee. We do not have a real physical asset which one can hold, buy or sell whose price equal to the current gas price. So one can not really sell such an asset. However, we aima to design a product whose profit curve is like a classic option but for base fees
    :::info
    T-option is an product that mimic the classic option corresponding to a stock whose price $p$ equal to:
    - $p = l$ if $base fee$ $<l$
    - $p =  \ base \ fee$ if $l\leq$ $base fee$ $\leq u$
    - $p = u$ if  $base fee$ $>u$
    
    where $l$ and $u$ represent lower and upper bound resp 

    
    :::
    

    In the following sections, we will provide formal descriptions of T-option. We will see its pricing can be easily derived from classic option pricing, which allow users who familiar with classic option can get on hand quickly. We will also talk about how to recover classic option from t-option.

- Why T-Options?

    The volatility of base fees, which lack a corresponding real asset of equal value, can surge unexpectedly within a brief period. Consequently, if option sellers were required to deposit substantial collateral to cover potential high payouts, it would lead to inefficient capital usage, particularly in scenarios where gas fees skyrocket unexpectedly. By capping the maximum payout at $u−l$, t-options require significantly lower and more predictable collateral amounts. This approach focuses on the more likely outcomes or expected value ranges, enhancing capital efficiency. Notably, t-options can be adapted to function like classic options, as detailed in the following sections. 
    ![basefee](https://hackmd.io/_uploads/SkCtdW0r6.png)<em>Base Fee from Nov 29 2023 to Dec 6 2023. From [Ultrasound Money](https://ultrasound.money/)</em>

    
- Who Buy & Sell T-Options

    <ins>Selling T-Options</ins>:
        Taking the short side of options is typically a domain for professionals due to the inherent risks. In traditional markets, they rely on hedging strategies to manage these risks. Such strategies often involves holding spot assets. However, in the context of Ethereum gas, base fees have no spot market. The GAS token emerges as an ideal hedging instrument. It allows market makers to effectively manage the risk associated with selling these options, similar to how they would in traditional markets but tailored to the crypto environment.
    
    <ins>Buying T-Options</ins>:
    Individuals or entities might purchase T-options to speculate on the fluctuating gas fees of the Ethereum network. The cash-settled nature of these options makes them attractive for speculation. Cash-settled derivatives like T-options are conducive to executing sophisticated strategies that could continuously hedge gamma or delta. Unlike physically settled gas derivatives, t-options can be seamlessly integrated into vaults to execute diverse and complex trading strategies.
    



- Glossary

    - $GAS$: the underling currency.
    - $G_t$: real base fee at time $t$, denominated in $GAS$
    - $T_e$: The time until which the t-option is valid. After $T_e$, the t-option either needs to be exercised or it expires worthless.
    - $l,u$: lower and upper bound of the payoff. At time $T_e$, the holder of the t-option payoff if  $\max\{0,\min\{G_{T_e}, u\} - l\}$ (in the case of a call t-option) or $\max\{0, u - \max\{G_{T_e}, l\}\}$ (in the case of a put t-option.
    - $premium$: The price that the buyer of the t-option pays to the seller for the rights conveyed by the t-option.

- Profit Graph of T-Option

    The profit of a call t-option is:

    $profit(G_{T_e})=\left\{ 
      \begin{array}{ c l }
        -premium & \quad \textrm{if            } G_{T_e} < l \\
        G_{T_e} - l-premium & \quad \textrm{if            } l\leq G_{T_e} \leq u \\
    u - l -   premium               & \quad \textrm{if } G_{T_e} > u
      \end{array}
    \right.$


    ![image](https://hackmd.io/_uploads/B1TL9GJE6.png)

    The graph mimics a classic Euro-style call option, except that when $G_{T_e} > u$, payoff is truncated.

- Pricing of T-Options

    - Notations

        Suppose we have an asset whose price is exactly same as the base fee and there exists an options market. Assume these options all have the same expiratons. 
        
        Now:

        - $C_p$: price of classic call option with strike price $p$
        - $P_p$: price of classic put option with strike price $p$
        - $TC_{l,u}$: price of call t-option with strike range $[l,u]$
        - $TP_{l,u}$: price of put t-option with strike range $[l,u]$


    - Call T-Option

        The profit of longing a call t-option with range $[l,u]$ is same as the profit of longing a call option with strike price $l$ and shorting a call option with strike price $u$.

        Therefore

        $TC_{l,u} = C_l - C_u$

    - Put T-Option

        Similarly, longing a put t-option with range $[l,u]$ is euqivalent to longing a put option with strike price $u$ and shorting a put option with strike price $l$.

        Therefore

        $TP_{l,u} = P_u - P_l$

    - Put-Call Parity of T-Options

        By observing the pricing fomula above, we have:

        $\begin{align}
        TC_{l,u} + TP_{l, u} &= C_l - C_u +             P_u - P_l \\
          &= (C_l - P_l) - (C_u - P_u)\\
          &= (S - PV(l)) - (S - PV(u))\\
          &= PV(u) - PV(l)\\
          &= PV(u-l)
        \end{align}$

        Here,
        - $S$: the spot price of the asset, which is the current base fee
        - $PV(x)$: discounted from the value from the expiration at risk-free rate

        Here, we applied put-call parity of classic Euro-style option. A more direct way to see this put-call parity of t-option is that longing a call t-option with strike range $[l,u]$ and longing a put t-option with same strike range $[l,u]$ is equivalent to longing (u-l) amount of $GAS$.

    - Pricing Model

        When valuing these classic Euro-style options for $GAS$, the approach mirrors that used in conventional stock market option pricing. However, in this context, the underlying asset's price is represented by the $GAS$ instead of a stock's price, with major difference being the price is truncated. The valuation model we will employ here is the [Black-Scholes model](https://en.wikipedia.org/wiki/Black%E2%80%93Scholes_model).

        We take call t-option as example because the Delta and Gamma of a put t-option is just the negative of the Delta and Gamma of its related call t-option, due to the call-put parity in the last section.



        The price of call t-option based on Black-Scholes is:

        $\begin{align}
        TC_{l,u} &= C_l - C_u\\
              &= G(N(d_l)-N(d_u)) - le^{-rT}N(d_l - \sigma\sqrt{T}) + ue^{-rT}N(d_u - \sigma\sqrt{T}),
        \end{align}$

        where:

        - $N(⋅)$: the cumulative distribution function of the standard normal distribution.
        - $d_K$: $\dfrac{\ln(\dfrac{G}{K})+(r+\dfrac{\sigma^2}{2})T}{\sigma\sqrt{T}}$
        - $G$: curent base fee.
        - $[l,u]$: strike range of the call t-option.
        - $r$: the risk-free interest rate.
        - $σ$: the volatility of the underlying asset.
        - $T$: the time to expiration of the option.

        The graph below shows how the Call T-Option's price behaves - the larger the difference $u-l$, the higher possible max profit of this T-Option can generate.

        ![image](https://hackmd.io/_uploads/SknnWw1N6.png)



        1. Delta of T-Option


            $\Delta = N(d_l) - N(d_u)$



            The graph below shows what Call T-Option's Delta looks like - The smaller the ratio $u/l$, the narrower this curve looks like.

            ![image](https://hackmd.io/_uploads/S1ohTLJN6.png)


        2. Gamma of T-Option


            $\Gamma = \dfrac{N'(d_l)}{S\sigma\sqrt{T}} - \dfrac{N'(d_u)}{S\sigma\sqrt{T}},$

            where $N′(d)$ is the probability density function of the standard normal distribution evaluated at d.

            Below shows what does the Gamma looks like. The smaller the ratio $u/l$, the narrower this curve looks like.

            ![image](https://hackmd.io/_uploads/H1TGCUyNp.png)




- Replicate Classic Options from T-Options

    Notice that longing a call t-option with strike range $[a_1,a_3]$ is equivalent to longing a call t-option with strike range $[a_1,a_2]$ and longing a call t-option with strike range $[a_2,a_3]$. We can look at an example to better understand this:

    - Bob is longing two call t-options, $Option_1$ and $Option_2$. These call t-options have same expiration time as 3 days. $Option_1$ has strike range $[30, 50]$, and $Option_2$ has strike range $[50, 70].$ Let the base fee at expiration be $G_e$.

        - If $G_e<30$, 
            Bob get $0$ payoff from both t-options.
        - If $30\leq G_e<50$, 
          Bob get payoff $G_e - 30$ from $Option_1$ and $0$ from $Option_2$. Total payoff is $G_e-30 +0= G_e-30.$
        - If $50\leq G_e<70$, 
          Bob get payoff $\min\{G_e,50\} - 30=50-30=20$ from $Option_1$ and $G_e-50$ from $Option_2$. Total payoff is $20 +G_e-50= G_e-30.$
        - If $G_e\geq 70$, 
          Bob get payoff $\min\{G_e,50\} - 30=50-30=20$ from $Option_1$ and $\min\{G_e,70\} - 50=70-50=20$ from $Option_2$. Total payoff is $20+20= 40 = \min\{G_e,70\}-30.$

     In conclusion, the total payoff of Bob in terms of $G_e$ is $0$ if $G_e<30$, $G_e-30$ if $30 \leq G_e<70$, $70-30=40$ if $G_e\geq 70.$ Or in a more concise manner, the payoff is $\max\{ 0, \min\{G_e, 70\} - 30 \}$, and this is the payyof of a call t-option with straike range $[30,70].$ Similarly longing $n$ call t-options with same expiratoin time and with strike ranges $[a_0,a_1]$, $[a_2,a_3]$, ..., $[a_{n-1},a_n]$ respectively, it is equivalent to longing one call t-option with the same expiration time and with the trike range $[a_0, a_n].$ In short, we can "concatenate" call t-options.

    Using "concatenation", we can approximate a classic call option by longing multiple t-options. At the same time, since the increase rate of base fee is upper bounded by $12.5$% per block (per 12 seconds), so in fact we have a theorectical definite upper bound of the base fee at the expiration time. But this value may still be too large, and many people may have their own beliefs in the upper bound of the base fee. Anyway, by longing multiple t-options or a single t-option with large enough strike range should be good enough and pratical to mimic a classic option.





- Summary

    The T-Option is tailored to:
    - Mimicking Standard Options: T-Options effectively replicate the profit profile of classic options but are based on the Ethereum base fee. This adaptation addresses the absence of a tangible asset equivalent to the gas price, enabling users to speculate or hedge against gas price volatility.

    - High Capital Efficiency: Recognizing the unpredictability and potential spikes in gas fees, T-Options are designed to be capital efficient.

    - Accessibility for Traditional Option Traders: The structure and pricing of T-Options are derived from classic option models, making them easily comprehensible to those familiar with traditional financial instruments. This familiarity ensures a lower barrier to entry for traders and investors accustomed to standard call/put options, facilitating broader adoption.


#### Truncated Exotic Options(GIX V1)

Truncation stratgy can apply to some exotic options. Here, we give truncated Barrier Option, truncated Asian Option, truncated Lookback Option.

##### Barrier T-Option

Barrier options are particularly usedful in highly volatile markets for 
- Developers: They might use barrier options to manage costs associated with smart contract operations. If gas prices reach a certain high threshold (the barrier), the option can be structured to compensate for these higher costs, thus maintaining operational efficiency.

- Traders and Speculators: They might use barrier options to speculate on gas price volatility. If they anticipate significant changes in gas prices within a specific timeframe, barrier options provide a way to profit from these movements while limiting risk exposure.

- Retail Users: For regular users of the Ethereum network, barrier options can act as a form of insurance against fluctuating gas fees. If gas prices exceed a certain level, the barrier option can offset higher transaction costs.


Barrier t-option is the barrier option's of truncated gas price. There are two types of Barrier T-Options:

- Knock in T-Options: These options become active or "knock in" only if the base fee reaches or surpasses the barrier level. We will use an example to illustrate.

    Example:

    Strike Range $[l,u]$: $[100, 120]$
    Barrier Level $H$: 110
    Expiration Time: 3 days
    Current base fee: 95
    Knock-In Feature: The option becomes active if the gas fee reaches to or above 110 at any time before expiration.

    In this scenario, the barrier t-option is an "up-and-in" call t-option. The option will only become active if the gas fee reaches 110. If, in next 3 days, the gas fee never reaches 110, the option will expire worthless. However, if the gas fee reaches or exceeds 110, the t-option becomes active and behaves like a standard call t-option with a strike range of $[100,120]$. If the gas fee at expiration is above 100, the option holder will realize a profit, upper bounded by $120-100=20$.

- Knock out T-Options: These options are initially active but become void or "knock out" if the base fee hits the barrier level. Again, We will use an example to illustrate.

    Strike Range $[l,u]$: $[40, 50]$
    Barrier Level $H$: 30
    Expiration Time: 7 days
    Current base fee: 55
    Knock-Out Feature: The option becomes void if the stock price drops to or below 30 at any time before expiration.

    In this scenario, the barrier t-option is an "down-and-out" put t-option. The option will become void if the gas fee drops to or below 30. If, in next 7 days, the gas fee never goes to or below 30, the option will expire worthless. Otherwise, the t-option stays active and behaves like a standard put t-option with a strike range of $[40,50]$. If the gas fee at expiration is below 50, the option holder will realize a profit, upper bounded by $50-40=10$.

    For a knock out t-option, we require lower strike range $l\geq H$, greater than the barrier level. This is because if the option stays active, the gas fee is above $H$, so lower $l$ doesn't imply possible higher profit. To reduce confusion, we require $l\geq H$.


- Payoff of Barrier T-Options

    1. Knock in T-Options

        - payoff = 0 if gas fee stays lower than the barrier level  until expiration time
        - payoff = $\max\{0,\min\{G_{T_e}, u\} - l\}$ otherwise, which is same as the payoff of a standard call t-option

    2. Knock out T-Options

        - payoff = 0 if gas fee ever drops to lower than the barrier level before expiration time
        - payoff = $\max\{0, u - \max\{G_{T_e}, l\}\}$ otherwise, which is same as the payoff of a standard put t-option


    In the case that a barrier t-option is active at the expiration time, the payoff of a barrier t-options are same as the payoff of a standard call t-option or put t-option. Under this case it has same graph as t-options'. We copy the payoff graph of call t-option from above.

    ![image](https://hackmd.io/_uploads/B1TL9GJE6.png)

- Pricing of Barrier T-Options

    1. Knock in T-Options

        Since payoff of longing a knock in t-option with strike range $[l,u]$ and barrier level $H$ is same as 
        1. longing a standard knock in option with strike price $l$ and barrier level $H$ and same expiration time

        AND

        2. shorting a standard knock in option with strike price $u$ and barrier level $H$ and same expiration time


        Therefore,

        $B_{in,[l,u],H} = B_{in,l,H}$ - $B_{in,u,H}$,

        where:

        - $B_{in,[l,u],H}$: price of knock in t-option with strike range $[l,u]$ and barrier level $H$
        - $B_{in,K,H}$: price of standard knock in option with strike price $K$ and barrier level $H$

    2. Knock out T-Options

        Since payoff of longing a knock out t-option with strike range $[l,u]$ and barrier level $H$ is same as 

        1. longing a standard knock out option with strike price $u$ and barrier level $H$ and same expiration time

        AND

        2. shorting a standard knock out option with strike price $l$ and barrier level $H$ and same expiration time


        $B_{out,[l,u],H} = B_{out,u,H}$ - $B_{in,l,H}$,

        where:

        - $B_{out,[l,u],H}$: price of knock out t-option with strike range $[l,u]$ and barrier level $H$
        - $B_{out,K,H}$: price of standard knock out option with strike price $K$ and barrier level $H$


    Similar like that we derived pricing of call/put t-options from pricing of standard call/put options, we derived pricing of barrier t-options from pricing of standard barrier options. People who are familiar with standard barrier options can get on hand of barrier t-options easily.

    Explicit pricing of barrier t-options depends on the pricing model for a standard barrier option. And the pricing model for a barrier option is complex and often requires numerical methods for accurate calculations. However, we want point out that:

    - The price of knock in t-option tends to the price of standard up-and-in option with strike price equal to $l$ as $u$ increase.
    - The price of knock out t-option tends to the price of standard down-and-out option with strike price equal to $u$ as $l$ decrease.



   **Note: We explained up-and-in options and down-and-out options. If one is looking for Up-and-down and down-and-in options, these two options are just upside down of up-and-in options and down-and-out options. Details are the same.*

##### Asian T-Option




An Asian Option is a type of exotic option where the payoff depends on the average price of the underlying asset over a certain period, rather than its price at a specific point in time. This averaging feature reduces the impact of market volatility. Let's now describe the Average Price T-Options.

Usually,
for a call option:
$Payoff=\max\{Price−Strike Price,0\}$
for a put option:
$Payoff=\max\{Strike Price - Price,0\}$

Asian option also has call/put types, and follows exactly above payoff formulas. The only difference is that for average price truncated asian option, $Price$ is average price followed by a truncation, instead of the spot price at expiration time.

Again, for truncated version, we set strike range $[l,u]$ where $l<u$. Now, we can now describe asian t-options.

Average Price T-Options: 

Same payoff formula for call/put formula above, 

- Price:
    - for call option: $\min\{average\ gas\ base\ fee, u\}$
    - for put option: $\max\{average\ gas\ base\ fee, l\}$
- StrikePrice: predetermined fixed number.

It has call and put types. For this one, we replace the gas fee at expiration time by average gas fee. It may not neccesary to trucate this average gas fee, but we still give this option to users. One reason is the expiration time in gas derivative market may be relatively short, so the deviation of even average gas fee can still be possibaly large.

Example:

Consider an Average Price call t-option, and a strike range of $[50,100]$. The payoff will depend on the average base fee over 7 days compared to 50, and if payoff $>100-50=50$, we still take the payoff as 50 since we truncated it. If the average price is above 50, the investor profits by the difference.



- Payoff of Asian T-Options

    The payoff looks similar as the payoff of call/put t-options. The pattern also looks like:

    ![image](https://hackmd.io/_uploads/SJ1KuCeVp.png)

- Pricing of Asian T-Options

    Again, the pricing of asian t-options is based on standard asian options. We give averaged price call and put t-options seperately.

    1. Average Price Call T-Options:

        Longing a Average Price Call T-Options with  strike range $[l,u]$ is equivalent to

        1.  longing a standard Average Price Call Options with  strike price $l$

        AND

        2. shorting a standard Average Price Call Options with strike price $u$  

        $P = C_{avg\ price, l}-C_{avg\ price, u},$
        where:

        - $P$: Price of wanted asian t-option
        - $C_{avg\ price, K}$: price of standard Average Price Call Options with strike price $K$


   2. Average Price Put T-Options:

        Longing a Average Price Put T-Options with  strike range $[l,u]$ is equivalent to

        1.  longing a standard Average Price Put Options with  strike price $u$

        AND

        2. shorting a standard Average Price Put Options with strike price $l$  

        $P = P_{avg\ price, u}-P_{avg\ price, l},$
        where:

        - $P$: Price of wanted asian t-option
        - $P_{avg\ price, K}$: price of standard Average Price Put Options with strike price $K$

    Again, the pricing of asian t-options is determined by the pricing of  standard average price asian options. These regular pricing of asian options depends on the pricing model for standard asian option. Modified Blach Scholes formula can simplified model for an Asian option, particularly for the geometric average price option:

    $C_{avg\ price,K} = Se^{(r-\dfrac{\sigma_{adj}^2}{2})T}N(d_1) - Ke^{-rT}N(d_2),$

    With this simplified model, the pricing graph, Delta, Gamma looks similar as the ones of call/put t-options.

    ![image](https://hackmd.io/_uploads/ByScPx-4T.png)

    ![image](https://hackmd.io/_uploads/rJx3PxWEp.png)

    ![image](https://hackmd.io/_uploads/B146wg-46.png)








##### Lookback T-Options


Fixed lookback t-option allows buyer to exercise the option at the most favorable price followed by a truncation.

Follow the notation in last section, payoff of the lookback call/put t-option is in the same form as the payoff of a call/put t-option, e.g. call option's payoff pattern is $payoff_{call}=\max\{0, Price-StrikePrice\}$. Only difference is that it has different $Price$. Again the strike range is $[l,u]$.

1. Lookback call t-option:

    - $Price$: $\max\{0, \min\{u,highest \ gas\ fee\ until \ expiration\}\}$

2. Lookback put t-option:

    - $Price$: $\max\{0, \min\{u,lowest \ gas\ fee\ until \ expiration\}\}$


2. PayOff of Lookback T-Options

    Again, it is of the same pattern. For a call t-option:

    ![image](https://hackmd.io/_uploads/SJ1KuCeVp.png)

    For a put t-option:

    ![image](https://hackmd.io/_uploads/rkjoHZbEp.png)



- Pricing of Lookback T-Options

    1. Lookback call t-option:

        Longing a lookback call T-Options with strike range $[l,u]$ is equivalent to

        1.  longing a standard lookback call options with strike price $l$

        AND

        2. shorting a standard lookback call options with strike price $u$  

        $P = C_{lookback, l}-C_{lookback, u},$
        where:

        - $P$: Price of wanted lookback t-option
        - $C_{lookback, K}$: price of standard lookback call options with strike price $K$

    2. Lookback call t-option:

        Longing a lookback put T-Options with strike range $[l,u]$ is equivalent to

        1.  longing a standard lookback put options with strike price $u$

        AND

        2. shorting a standard lookback put options with strike price $l$  

        $P = P_{lookback, u}-P_{lookback, l},$
        where:

        - $P$: Price of wanted lookback t-option
        - $P_{lookback, K}$: price of standard lookback put options with strike price $K$

    The pricing of standard lookback option depends its pricing model. An example of simplified formula of lookback call option is:

    $C_{lookback, K} \approx e^{-rT}(S_{max}-K).$



##### Conclusion

The section discusses three types of exotic truncated options. These options all exhibit the properties:

- Replication of Standard Exotic Options: They are designed to replicate the behavior of traditional exotic options.
- Capital Efficiency: The collateral required for these options is capped and can be agreed upon in advance by the seller and buyer.
- Accessibility for Experienced Users: These options are straightforward for those who are already familiar with standard options.

#### Custom CFMMs(Constant Function Market Makers) to Replicate Option-like Payoffs(GIX V2)


Our team has been exploring the potential of [Uniswap V4](https://github.com/Uniswap/v4-core) for developing specialized systems aimed at base fee trading.

The primary issue with on-chain options is their low liquidity. Truncated options don't address this challenge. However, customized AMMs present a viable solution. Notably, [liquidity positions in Uniswap V3 act like perpetual options](https://lambert-guillaume.medium.com/how-to-create-a-perpetual-options-in-uniswap-v3-3c40007ccf1). This is a concept that could be used to engineer synthetic option-like returns. Protocols like [Panoptics](https://intro.panoptic.xyz/) are examples of its application.

[Uniswap V4 Hooks](https://blog.uniswap.org/v4-twamm-hook) further introduces greater versatility, allowing for the integration of custom swap and liquidity strategies, and even customized CFMMs.

Our research is currently focused on two primary directions:

1. Utilizing hooks to create a virtual pool for GAS/ETH by amplifying the GAS price movements. Since GAS, being a Time-Weighted Average Price (TWAP) of base fees, doesn't precisely mirror base fee fluctuations, A virtual pool would use a scaling factor to magnify the tick spacing for swapping and LPing to closely track the base fee;
2. A custom CFMM on Uniswap V4 for base fee trading that allows close tracking of base fees, through `NoOp`. [An example Uniswap V4 Pool using the Constant Sum as the CFMM has been made](https://github.com/saucepoint?tab=repositories). 



