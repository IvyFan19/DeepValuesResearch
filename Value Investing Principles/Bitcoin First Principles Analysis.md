# A First-Principles Analysis of Bitcoin

## I. Introduction

Bitcoin, introduced in 2008 by the pseudonymous Satoshi Nakamoto, represents a novel approach to digital value transfer, often described as a peer-to-peer electronic cash system.<sup>1</sup> Its emergence marked a significant departure from traditional financial systems reliant on trusted intermediaries. Understanding Bitcoin's fundamental nature, capabilities, and limitations requires an analysis grounded in its core design principles - a first-principles approach. This report undertakes such an analysis, dissecting Bitcoin into its foundational components: its original purpose, underlying technologies, consensus mechanism, decentralization model, and economic architecture. By examining these core elements and their interactions, we aim to construct a clear view of Bitcoin's inherent properties, strengths, weaknesses, and potential use cases, independent of market narratives or secondary developments. The objective is to evaluate Bitcoin based purely on its underlying mechanics and codified rules.

## II. Foundational Purpose: The Bitcoin Whitepaper

The foundational document for Bitcoin is the nine-page whitepaper titled "Bitcoin: A Peer-to-Peer Electronic Cash System," published by Satoshi Nakamoto on October 31, 2008.<sup>1</sup> The paper was disseminated via a cryptography mailing list, outlining a system designed to overcome the perceived flaws of the traditional financial system.<sup>1</sup>

Nakamoto's introduction critiques the reliance on trusted third parties, such as banks, for electronic payments.<sup>1</sup> This reliance, Nakamoto argued, introduces inherent weaknesses: transaction costs associated with mediation, the possibility of transaction reversals (limiting non-reversible services), the need for trust, and the collection of sensitive user information.<sup>1</sup> The existing system prevented truly direct peer-to-peer transactions and struggled with micropayments due to mediation costs.<sup>1</sup>

The core problem Nakamoto sought to solve was double-spending - the risk that a digital unit of value could be spent more than once - without resorting to a central authority.<sup>1</sup> Traditional systems solve this through centralized clearinghouses.<sup>1</sup> Nakamoto proposed an alternative: "an electronic payment system based on cryptographic proof instead of trust, allowing any two willing parties to transact directly with each other without the need for a trusted third party".<sup>1</sup>

The proposed solution involved a peer-to-peer network utilizing cryptographic techniques. Transactions would be publicly announced <sup>1</sup>, timestamped by hashing them into an ongoing chain of hash-based proof-of-work, forming a record that is computationally infeasible to change without redoing the work.<sup>6</sup> This public ledger, later known as the blockchain, would allow participants to agree on a single history of transactions, thereby preventing double-spending.<sup>1</sup> The whitepaper laid out the fundamental components: defining electronic coins as chains of digital signatures, using a distributed timestamp server and Proof-of-Work to establish chronological order and consensus, outlining the network operation, and describing the incentive structure for network participants (miners).<sup>1</sup> Nakamoto's vision was for a system where trust is replaced by cryptographic proof, enabling secure, verifiable, and irreversible peer-to-peer electronic cash transactions.<sup>1</sup>

## III. Core Technological Components

Bitcoin's functionality rests on the interplay of several core technologies, primarily the blockchain data structure and cryptographic methods. These components work in concert to enable secure, transparent, and verifiable peer-to-peer transactions without a central intermediary.

### A. Blockchain: The Distributed Ledger

The blockchain is the foundational technology underlying Bitcoin, serving as a decentralized, distributed, and immutable public ledger.<sup>3</sup> It records every Bitcoin transaction ever processed.<sup>13</sup> The ledger is structured as a chronologically ordered chain of blocks, where each block contains a batch of transactions.<sup>1</sup>

1.  **Block Structure:** Each block consists primarily of a block header and a list of transactions confirmed within that block.<sup>15</sup> The block header contains critical metadata, including:

    -   A cryptographic hash of the previous block's header, linking it to the preceding block and forming the chain.<sup>1</sup>

    -   A Merkle root, which is a hash summarizing all transactions included in the current block.<sup>15</sup>

    -   A timestamp, indicating when the block was created.<sup>1</sup>

    -   A nonce (a "number used once") which is adjusted during the mining process.<sup>15</sup>

    -   The difficulty target, defining the required conditions for a valid block hash.<sup>15</sup>

2.  **Merkle Trees:** To efficiently summarize and verify the transactions within a block, Bitcoin utilizes Merkle trees (also known as hash trees).<sup>3</sup> Each transaction in the block is individually hashed (often represented as a Transaction ID or TXID). These transaction hashes form the "leaf" nodes of the tree. Pairs of leaf nodes are then concatenated and hashed together to form the next level of "non-leaf" nodes. This process repeats recursively, hashing pairs of hashes, until only a single hash remains - the Merkle root.<sup>22</sup>

    -   *Efficiency:* Merkle trees allow for efficient verification of whether a specific transaction is included in a block without needing to download or process the entire block's transaction data. Only the Merkle root (stored in the block header) and the "Merkle path" or "Merkle proof" (the intermediate hashes needed to reconstruct the path from the transaction hash to the root) are required.<sup>23</sup> This is crucial for lightweight clients (Simplified Payment Verification - SPV).<sup>4</sup>

    -   *Integrity:* The Merkle root acts as a unique digital fingerprint for the entire set of transactions in the block.<sup>24</sup> Any change to even a single transaction within the block would alter its hash, which would cascade up the tree and result in a different Merkle root.<sup>23</sup> This makes tampering with transaction data easily detectable by comparing the calculated Merkle root with the one stored in the block header.<sup>24</sup>

3.  **Chaining Blocks:** Each new block added to the blockchain contains the hash of the preceding block's header.<sup>1</sup> This creates a cryptographic link, forming an ordered chain. Altering any information in a past block would change its hash, which would invalidate the hash pointer in the subsequent block, and consequently invalidate all following blocks in the chain.<sup>1</sup> Rebuilding the chain from the point of alteration would require redoing the computationally intensive Proof-of-Work for that block and all subsequent blocks, making the ledger effectively immutable.<sup>1</sup>

4.  **Distribution:** The blockchain is not stored in a central location but is distributed across a peer-to-peer network of computers (nodes).<sup>3</sup> Each full node typically maintains a complete copy of the entire blockchain ledger.<sup>4</sup> When a new block is validated, it is broadcast across the network, and participating nodes update their copies of the ledger.<sup>4</sup> This redundancy and distribution enhance the network's resilience and resistance to single points of failure or censorship.<sup>4</sup>

### B. Cryptography: Securing Ownership and Integrity

Cryptography is the cornerstone of Bitcoin's security, used to establish ownership, authorize transactions, and ensure the integrity of the ledger. Key cryptographic primitives employed include public/private key pairs, digital signatures (specifically ECDSA), and cryptographic hash functions (primarily SHA-256).

1.  **Public and Private Keys (Asymmetric Cryptography):** Bitcoin utilizes public-key cryptography, specifically the Elliptic Curve Digital Signature Algorithm (ECDSA), to manage ownership of funds.<sup>3</sup>

    -   *Key Generation:* Each user can generate one or more key pairs, consisting of a private key and a corresponding public key.<sup>40</sup> The private key (d) is essentially a large, randomly generated secret number (a 256-bit integer for Bitcoin).<sup>39</sup> The public key (Q) is derived from the private key using elliptic curve multiplication (Q=d×G), where G is a predefined standard point on the elliptic curve known as the generator point.<sup>39</sup> This is a one-way process; it is computationally infeasible to derive the private key from the public key due to the difficulty of the Elliptic Curve Discrete Logarithm Problem (ECDLP).<sup>39</sup>

    -   *Elliptic Curve (secp256k1):* Bitcoin specifically uses the secp256k1 elliptic curve, defined by the equation y2=x3+7 over a large prime finite field (p=2256-232-29-28-27-26-24-1).<sup>39</sup> Any point (x,y) on this curve represents a potential public key.<sup>39</sup> The choice of secp256k1 offers efficiency benefits compared to other curves and was selected in a non-random, predictable way, reducing concerns about potential backdoors.<sup>46</sup>

    -   *Ownership:* The private key grants control over the bitcoins associated with the corresponding public key (or derived address). It must be kept secret, as anyone possessing it can authorize transactions to spend those funds.<sup>12</sup> The public key (or more commonly, a Bitcoin address derived from it via hashing) is used to receive funds and can be shared publicly without compromising security.<sup>12</sup>

2.  **Digital Signatures (ECDSA):** Digital signatures provide proof of ownership and authorize transactions without revealing the private key.<sup>1</sup>

    -   *Signing Process:* To authorize a transaction, the sender uses their private key (d) and a hash of the transaction data (z) to generate a digital signature. The ECDSA signing process also involves a securely generated random number (k, often called a nonce) specific to that signature.<sup>41</sup> The resulting signature consists of two values, r and s.<sup>41</sup> The value r is derived from the x-coordinate of a point R=k×G on the elliptic curve, and s is calculated using the formula s=k-1×(z+d×r)(modn), where n is the order of the curve.<sup>41</sup> This signature effectively proves knowledge of the private key (d) linked to the message hash (z) and the random point (R).<sup>42</sup> Because the signature depends on the transaction data hash (z), a signature is valid only for that specific transaction and cannot be reused for another.<sup>52</sup>

    -   *Verification Process:* Anyone can verify the signature using the sender's public key (Q), the transaction hash (z), and the signature values (r,s).<sup>39</sup> The verification algorithm essentially uses the public key and message hash to mathematically recover a point R′ from the signature component s. It then checks if the x-coordinate of the recovered point R′ matches the r value from the signature.<sup>41</sup> If they match, the signature is valid, confirming that the transaction was authorized by the owner of the corresponding private key.<sup>1</sup>

3.  **Hashing Functions (SHA-256):** Cryptographic hash functions, particularly SHA-256 (Secure Hash Algorithm 256-bit), are used extensively throughout the Bitcoin protocol.<sup>18</sup> SHA-256 takes an input of any size and produces a fixed-size 256-bit (32-byte) output, often represented as a 64-character hexadecimal string.<sup>18</sup> Key properties include:

    -   *Deterministic:* The same input always produces the same output.<sup>25</sup>

    -   *Pre-image Resistance (One-way):* It is computationally infeasible to determine the original input given only the hash output.<sup>25</sup>

    -   *Collision Resistance:* It is computationally infeasible to find two different inputs that produce the same hash output.<sup>18</sup>

    -   *Avalanche Effect:* A small change in the input results in a drastically different output hash.<sup>18</sup>

    -   *Role in Bitcoin:* SHA-256 (often applied twice, known as double-SHA-256 or hash256) is used for:

        -   *Transaction Hashing:* Creating unique identifiers (TXIDs) for transactions.<sup>22</sup>

        -   *Merkle Trees:* Hashing transactions and intermediate nodes to create the Merkle root.<sup>22</sup>

        -   *Block Hashing:* Generating the hash of a block header during the Proof-of-Work mining process.<sup>1</sup>

        -   *Address Generation:* Hashing public keys (often in combination with RIPEMD-160) to create Bitcoin addresses.<sup>40</sup>

        -   *Ensuring Integrity:* Hashing ensures data integrity throughout the blockchain. Any modification to transaction data or block headers would result in a different hash, making tampering evident.<sup>23</sup>

These cryptographic components form the bedrock of Bitcoin's security model, enabling trustless verification of ownership and transaction integrity within the decentralized network.

## IV. Proof-of-Work (PoW) Consensus Mechanism

The Proof-of-Work (PoW) consensus mechanism is the process by which Bitcoin achieves agreement (consensus) on the state of the ledger across its distributed network, validates transactions, and secures the blockchain against attacks, all without a central authority.<sup>1</sup> It also governs the creation and distribution of new bitcoins.<sup>1</sup>

### A. Transaction Validation and Block Creation

When users broadcast new transactions, these transactions are collected by nodes in the network, typically residing in a temporary holding area called the memory pool (mempool).<sup>20</sup> Special nodes called miners select transactions from the mempool, prioritizing those with higher transaction fees, and assemble them into a candidate block.<sup>15</sup> Before including transactions, miners verify their validity according to the network's consensus rules (e.g., checking digital signatures, ensuring inputs are unspent).<sup>6</sup> The miner also includes a special "coinbase" transaction that creates new bitcoins (the block subsidy) and awards them, along with the collected transaction fees from the included transactions, to themselves.<sup>6</sup>

### B. The Mining Process: Hashing and Nonce

To propose a valid block to the network, a miner must find a "proof-of-work." This involves solving a computationally difficult puzzle tied to the candidate block.<sup>4</sup>

The process works as follows:

1.  **Block Header Assembly:** The miner constructs the block header, including the hash of the previous block, the Merkle root of the transactions in the current block, a timestamp, the difficulty target, and an arbitrary number called a nonce.<sup>15</sup>

2.  **Hashing:** The miner repeatedly hashes the block header using the SHA-256 algorithm (specifically, double-SHA-256).<sup>17</sup>

3.  **Nonce Iteration:** The miner varies the nonce (a 32-bit field in the block header) with each hash attempt.<sup>15</sup> Sometimes, if the nonce space is exhausted, miners also adjust the "extra nonce" located in the coinbase transaction, which alters the Merkle root, providing a larger space for searching.<sup>15</sup>

4.  **Finding a Solution:** This iterative hashing process continues until the miner finds a nonce that results in a block hash value that is numerically less than or equal to the current network difficulty target.<sup>15</sup> This target is a very small number, meaning the valid hash must typically start with a significant number of leading zeros.<sup>20</sup>

Finding such a hash is computationally expensive and requires a massive number of attempts (hashes per second, or hash rate) due to the nature of cryptographic hash functions - there is no known shortcut other than brute-force trial and error.<sup>15</sup> However, verifying a proposed solution is computationally trivial: any node can take the proposed block header (with the winning nonce), perform a single double-SHA-256 hash, and check if the result is below the target.<sup>17</sup> This asymmetry - difficult to find, easy to verify - is the essence of Proof-of-Work.<sup>17</sup>

### C. Difficulty Adjustment

The difficulty of finding a valid hash is not fixed. The Bitcoin protocol includes a difficulty adjustment mechanism to maintain a relatively consistent average block creation time of approximately 10 minutes, regardless of fluctuations in the total network hash rate.<sup>4</sup>

Every 2,016 blocks (roughly every two weeks, assuming a 10-minute block time), every node independently calculates the time it took to mine the previous 2,016 blocks (technically 2,015 due to an off-by-one implementation detail <sup>100</sup>).<sup>18</sup> This actual time is compared to the target time of 20,160 minutes (2,016 blocks \* 10 minutes/block).<sup>99</sup>

The difficulty target is then adjusted proportionally:

-   New Target = Old Target \* (Actual Time of Last 2016 Blocks / 20160 minutes) <sup>102</sup>

-   Equivalently, using difficulty (which is inversely proportional to the target): New Difficulty = Old Difficulty \* (20160 minutes / Actual Time of Last 2016 Blocks) <sup>99</sup>

If blocks were found faster than 10 minutes on average (actual time &lt; 20,160 mins), the difficulty increases (target decreases).<sup>99</sup> If blocks were found slower (actual time &gt; 20,160 mins), the difficulty decreases (target increases).<sup>99</sup> The adjustment is capped at a factor of 4 (difficulty cannot more than quadruple or reduce to less than a quarter in one adjustment period) to prevent extreme volatility.<sup>99</sup> This mechanism ensures that as more mining power joins the network, the difficulty rises to maintain the 10-minute average, and vice versa.<sup>20</sup>

### D. Achieving Consensus: The Longest Chain Rule

Once a miner finds a valid block (i.e., a block header hash below the current target), they broadcast it to the network.<sup>5</sup> Other nodes receive the block, independently verify its validity (checking the PoW, transaction validity, etc.), and if valid, add it to their copy of the blockchain.<sup>5</sup> Nodes then begin working on finding the *next* block, using the hash of this newly accepted block as the "previous block hash" in their new candidate block headers.<sup>6</sup>

Occasionally, two miners might find valid blocks at roughly the same time, leading to a temporary fork where different parts of the network see different valid next blocks.<sup>6</sup> Bitcoin resolves these temporary inconsistencies using the "longest chain rule" (or more accurately, the chain with the most accumulated proof-of-work).<sup>6</sup>

Nodes always consider the chain with the greatest cumulative PoW (which, under normal conditions, corresponds to the longest chain of valid blocks) as the authoritative version of history.<sup>6</sup> When a subsequent block is found extending one of the competing branches, that branch becomes the longest/heaviest chain. Nodes that were working on the shorter branch will abandon it and switch to building upon the now-longer chain.<sup>6</sup> Transactions in the abandoned (orphaned) blocks are typically returned to the mempool to be included in future blocks.<sup>74</sup> This mechanism ensures that the network eventually converges on a single, agreed-upon history of transactions.<sup>6</sup>

### E. Security Implications of PoW

Proof-of-Work secures the blockchain by making it prohibitively expensive for an attacker to alter past transactions.<sup>1</sup> To modify a block, an attacker would need to redo the PoW for that block *and* all subsequent blocks faster than the rest of the network is extending the honest chain.<sup>1</sup> This would require controlling a majority (more than 50%) of the network's total computational power (hash rate) - a "51% attack".<sup>7</sup>

As long as the majority of the hash power is controlled by honest miners who follow the protocol rules (incentivized by block rewards and fees), the honest chain will grow the fastest and outpace any attacker's chain.<sup>6</sup> The cumulative PoW embedded in the longest chain serves as evidence that it originated from the largest pool of computational power.<sup>6</sup> PoW thus transforms computational power ("one-CPU-one-vote" or, more accurately, "one-hash-one-vote") into a mechanism for decentralized consensus and ledger security.<sup>6</sup>

## V. Decentralization in Bitcoin

Decentralization is a core design principle and value proposition of Bitcoin, aiming to distribute control and eliminate single points of failure or censorship.<sup>3</sup> However, the degree of decentralization in practice is multifaceted and subject to various pressures. It manifests across several dimensions: network nodes, mining operations, and software development.

### A. Node Distribution

The Bitcoin network operates as a peer-to-peer (P2P) system where nodes connect directly to each other without a central server.<sup>10</sup> Nodes are responsible for validating transactions and blocks according to consensus rules, maintaining a copy of the blockchain, and propagating information across the network.<sup>4</sup>

-   **Full Nodes:** These nodes download and validate the entire blockchain history, independently enforcing all consensus rules.<sup>14</sup> They provide the highest level of security and autonomy for users running them. Running a full node contributes to the network's overall decentralization and resilience.<sup>14</sup>

-   **Light Nodes (SPV Clients):** These nodes download only block headers and rely on full nodes to provide Merkle proofs for verifying transactions relevant to them.<sup>4</sup> They require significantly fewer resources (storage, bandwidth) but offer lower security guarantees and trust assumptions compared to full nodes.

-   **Node Count and Distribution:** Estimating the exact number of nodes is challenging, as many nodes may operate privately or behind firewalls (unreachable nodes).<sup>158</sup> Services like Bitnodes attempt to estimate the number of *reachable* nodes by crawling the network.<sup>157</sup> As of late April/early May 2025, estimates suggest around 21,000 reachable nodes.<sup>35</sup> A significant portion (around 64-65%) operate over the Tor network, enhancing privacy but potentially concentrating network topology.<sup>35</sup> Geographically, nodes are distributed globally, but concentration exists. Data from late April 2025 indicates the United States hosts the largest share of reachable nodes (around 10.6%), followed by Germany (around 5.7%), France (around 2.7%), Canada (around 1.8%), and Finland (around 1.7%).<sup>159</sup> Considering *all* nodes (reachable and unreachable), estimates suggest a larger total count (around 62,000), with the US (\~30%) and Germany (\~14%) still leading, but also showing significant presence in countries like China (\~2.8%) which have fewer *reachable* nodes.<sup>35</sup> Research identifying "backbone nodes" (highly stable, long-running nodes) found a smaller subset (around 2,700) crucial for network stability, also showing geographic and operator concentration.<sup>157</sup>

-   **Importance:** A geographically and jurisdictionally diverse set of nodes is crucial for censorship resistance and network resilience. If nodes become too concentrated, the network could become more susceptible to localized disruptions, regulations, or attacks.<sup>37</sup>

### B. Miner and Hash Rate Distribution

While nodes validate blocks, miners (using specialized hardware like ASICs) perform the Proof-of-Work to create new blocks.<sup>7</sup> The distribution of mining power (hash rate) is another critical aspect of decentralization.

-   **Mining Pools:** Due to the immense difficulty of finding a block individually, most miners pool their computational resources together in mining pools.<sup>19</sup> Pools distribute block rewards proportionally to the hash rate contributed by each member, providing more predictable income.<sup>19</sup> While pools help individual miners participate, they also concentrate decision-making power (e.g., transaction selection, signaling for upgrades) in the hands of pool operators.<sup>19</sup>

-   **Hash Rate Concentration:** Data consistently shows that a small number of large mining pools control a significant majority of the Bitcoin network's hash rate.<sup>19</sup> For example, recent data suggests that pools like Foundry USA and AntPool (associated with hardware manufacturer Bitmain) have at times collectively controlled over 50% of the network hash rate.<sup>19</sup> Historical data shows similar concentrations, such as GHash.IO briefly exceeding 51% in 2014, raising significant concerns.<sup>127</sup>

-   **Hardware Manufacturing:** The production of efficient mining hardware (ASICs) is dominated by a few large manufacturers, primarily based in China (like Bitmain).<sup>16</sup> This concentration in hardware manufacturing presents another potential centralization vector, influencing who can mine profitably and potentially introducing hardware-level vulnerabilities or control points.<sup>64</sup>

-   **Implications (51% Attack Risk):** The concentration of hash rate in a few pools or under the influence of a few hardware manufacturers raises concerns about the feasibility of a 51% attack.<sup>33</sup> While executing such an attack on Bitcoin is considered extremely expensive and logistically difficult due to the sheer scale of the required hash rate and the likely negative impact on the attacker's own investments <sup>85</sup>, the trend towards centralization warrants ongoing monitoring. The GHash.IO incident demonstrated that even temporary breaches of the 51% threshold can cause significant market disruption and undermine confidence.<sup>165</sup>

### C. Developer Influence and Governance

Bitcoin's core software (primarily Bitcoin Core, but other compatible implementations exist) is open-source, meaning anyone can view, modify, and propose changes to the code.<sup>66</sup> However, the process of developing, maintaining, and upgrading the protocol involves a distinct set of actors and processes.

-   **Core Developers:** A relatively small group of experienced developers, often referred to as "Core developers," are primarily responsible for maintaining the Bitcoin Core software repository.<sup>121</sup> They review code, fix bugs, and merge changes proposed by contributors worldwide. While influential due to their technical expertise and role in maintaining the most widely used client, they do not have unilateral control over the protocol.<sup>140</sup>

-   **Bitcoin Improvement Proposals (BIPs):** Significant changes to the Bitcoin protocol are typically proposed through Bitcoin Improvement Proposals (BIPs).<sup>140</sup> BIPs are formal documents outlining proposed changes, their rationale, and technical specifications.<sup>140</sup> Anyone can submit a BIP, but it must undergo extensive discussion, peer review, and consensus-building within the developer community and broader ecosystem.<sup>140</sup> There are different types of BIPs: Standards Track (protocol changes), Informational, and Process (governance changes).<sup>180</sup>

-   **Activation and Enforcement:** Implementing a BIP, especially one requiring a consensus change (like a soft fork), involves multiple stakeholders.<sup>140</sup> Developers implement the code change.<sup>140</sup> Miners signal their readiness or support for the change, often requiring a high threshold (e.g., 95% signaling over a period) for activation.<sup>140</sup> Crucially, economic nodes (exchanges, businesses, individual users running full nodes) must choose to run the updated software that enforces the new rules.<sup>140</sup> If users and economic nodes reject a change, even one supported by developers and miners, the change will not gain traction, and those attempting to enforce it risk forking themselves off the main network.<sup>121</sup> This multi-stakeholder process acts as a check and balance system, making contentious changes difficult and promoting conservative development.<sup>140</sup>

### D. Implications for Censorship Resistance and Resilience

Bitcoin's decentralized architecture across nodes, mining, and development contributes significantly to its censorship resistance and resilience.<sup>3</sup>

-   **Censorship Resistance:** The lack of a central authority makes it difficult for any single entity (government or corporation) to block specific transactions or freeze funds at the protocol level.<sup>3</sup> Transactions are broadcast across the P2P network and validated by globally distributed nodes and miners.<sup>33</sup> While censorship can occur at centralized choke points like exchanges <sup>190</sup> or potentially through network-level attacks targeting specific nodes (Eclipse attacks) <sup>155</sup>, the core protocol itself is designed to be permissionless and neutral.<sup>8</sup>

-   **Resilience:** The distribution of nodes and miners across different geographies and jurisdictions makes the network resilient to localized failures, attacks, or regulatory actions.<sup>4</sup> If some nodes or miners go offline, the network can continue operating as long as others remain active.<sup>6</sup> The open-source nature of the software and the multi-stakeholder governance model also contribute to resilience against capture by any single group.<sup>140</sup>

However, the practical realities of mining pool concentration, node distribution biases, and the influence of core developers highlight that decentralization is not an absolute state but a dynamic spectrum with ongoing centralizing pressures that require vigilance from the community to maintain.<sup>9</sup>

## VI. Economic Architecture

Bitcoin's design incorporates specific economic principles intended to govern its supply, incentivize network participation, and facilitate a market for transaction processing. These elements are hardcoded into the protocol and enforced by consensus rules.

### A. Fixed Supply Cap (21 Million BTC)

A defining characteristic of Bitcoin is its predetermined maximum supply, capped at 21 million coins.<sup>7</sup> This limit was an intentional design choice by Satoshi Nakamoto, aimed at creating digital scarcity analogous to precious metals like gold, positioning Bitcoin as resistant to inflation often associated with fiat currencies that can be created at will by central authorities.<sup>65</sup>

-   **Enforcement:** The 21 million cap is not explicitly written as a single number in the code but is an emergent property of the interaction between the initial block subsidy amount and the programmed halving schedule.<sup>198</sup> The GetBlockSubsidy() function in the Bitcoin Core codebase defines the initial subsidy (50 BTC, represented as 50 \* COIN where COIN = 100,000,000 satoshis) and implements the halving using a bitwise right shift operator (&gt;&gt;) applied for each halving interval (210,000 blocks) that has passed.<sup>200</sup> This calculation is part of the consensus rules verified by every full node.<sup>66</sup> Any block attempting to claim a subsidy larger than allowed by these rules would be rejected by the network nodes.<sup>35</sup>

-   **Immutability:** Changing this cap would require a hard fork and near-universal consensus among developers, miners, and especially the economically significant nodes (users, exchanges, businesses) who run the software enforcing the rules.<sup>65</sup> Given that the scarcity enforced by the cap is considered a primary driver of Bitcoin's value, there is a strong economic disincentive for existing stakeholders to agree to a change that would inflate the supply and potentially devalue their holdings or rewards.<sup>66</sup>

-   **Actual Limit:** Due to the way the block subsidy is calculated (integer division via bit shift rounds down) and potentially unspendable early coins (like the genesis block reward) or lost coins, the total spendable supply will likely be slightly less than exactly 21 million.<sup>199</sup> Estimates suggest the final mined total might be closer to 20,999,999.9769 BTC, with the actual spendable amount potentially lower.<sup>199</sup>

### B. Predetermined Issuance Schedule (Halving)

New bitcoins are introduced into circulation exclusively through the block subsidy, which is part of the block reward paid to miners for successfully adding a new block to the chain.<sup>6</sup> The rate of this issuance is strictly controlled by the halving mechanism.<sup>65</sup>

-   **Mechanism:** Approximately every four years, or precisely every 210,000 blocks, the block subsidy is cut in half.<sup>76</sup> This event is programmed into the Bitcoin protocol and occurs automatically based on block height.<sup>106</sup>

-   **Impact:** The halving progressively reduces the rate of new supply entering the market, acting as a deflationary pressure or, more accurately, a disinflationary force (reducing the rate of inflation).<sup>91</sup> Historically, halving events have often been associated with subsequent increases in Bitcoin's price, potentially due to the supply shock relative to demand.<sup>91</sup> It also directly impacts miner revenue, forcing less efficient miners to potentially shut down if the price doesn't compensate for the reduced subsidy, although the difficulty adjustment helps mitigate this by lowering difficulty if hash rate drops.<sup>91</sup>

-   **Schedule and Final Coin:** The first block subsidy was 50 BTC. The first halving (Nov 2012) reduced it to 25 BTC, the second (July 2016) to 12.5 BTC, the third (May 2020) to 6.25 BTC, and the fourth (April 2024) to 3.125 BTC.<sup>76</sup> This process will continue until the block subsidy becomes less than one satoshi (the smallest unit of Bitcoin) and effectively reaches zero. The final fraction of a bitcoin is expected to be mined around the year 2140.<sup>65</sup>

**Table VI.1: Bitcoin Halving Schedule and Supply Issuance**

| **Halving \#** | **Estimated Year** | **Block Height** | **Block Subsidy (BTC)** | **Total BTC Mined by End of Epoch** | **% of Total Supply Mined** |
|----------------|--------------------|------------------|-------------------------|-------------------------------------|-----------------------------|
| 0 (Start)      | 2009               | 0                | 50.00000000             | 0                                   | 0.00%                       |
| 1              | 2012               | 210,000          | 25.00000000             | 10,500,000                          | 50.00%                      |
| 2              | 2016               | 420,000          | 12.50000000             | 15,750,000                          | 75.00%                      |
| 3              | 2020               | 630,000          | 6.25000000              | 18,375,000                          | 87.50%                      |
| 4              | 2024               | 840,000          | 3.12500000              | 19,687,500                          | 93.75%                      |
| 5              | 2028               | 1,050,000        | 1.56250000              | 20,343,750                          | 96.88%                      |
| 6              | 2032               | 1,260,000        | 0.78125000              | 20,671,875                          | 98.44%                      |
| 7              | 2036               | 1,470,000        | 0.39062500              | 20,835,937.5                        | 99.22%                      |
| 8              | 2040               | 1,680,000        | 0.19531250              | 20,917,968.75                       | 99.61%                      |
| ...            | ...                | ...              | ...                     | ...                                 | ...                         |
| 32             | \~2136             | 6,720,000        | 0.00000001              | \~20,999,999.9769                   | \~100.00%                   |
| 33             | \~2140             | 6,930,000        | 0.00000000              | \~20,999,999.9769                   | 100.00%                     |

*<sup>108</sup>*

### C. Transaction Fees and the Security Budget

While the block subsidy provides the initial incentive for miners, transaction fees paid by users constitute the second component of the block reward.<sup>8</sup>

-   **Fee Mechanism:** Users voluntarily attach fees to their transactions to incentivize miners to include them in a block.<sup>55</sup> Since block space is limited (by the block weight limit), miners typically prioritize transactions with the highest fee rate (measured in satoshis per virtual byte, or sats/vB) to maximize their revenue.<sup>55</sup> This creates a competitive market for block space, where fees fluctuate based on network congestion (demand for transactions) versus the fixed supply of block space.<sup>55</sup> The fee is calculated as the difference between the sum of transaction inputs and the sum of transaction outputs.<sup>81</sup>

-   **Security Budget:** The total block reward (block subsidy + transaction fees) constitutes the "security budget" of the Bitcoin network.<sup>97</sup> This budget represents the economic incentive for miners to expend energy and computational resources (hash rate) to secure the network via PoW.<sup>97</sup> A higher security budget generally translates to a higher network hash rate, making 51% attacks more costly and thus the network more secure.<sup>97</sup>

-   **Long-Term Transition:** As the block subsidy diminishes with successive halvings, transaction fees are designed to become the primary source of miner revenue and, consequently, the main component of the security budget.<sup>76</sup> This transition, expected to be complete around 2140, raises questions about the long-term sustainability of Bitcoin's security model.<sup>88</sup> Concerns exist that if transaction fee revenue is insufficient or too volatile, the incentive for miners might decrease, leading to a lower hash rate and potentially reduced network security.<sup>89</sup> However, proponents argue that increased adoption and demand for Bitcoin block space (potentially for settling Layer 2 transactions or high-value transfers) could lead to a robust fee market capable of sustaining security.<sup>98</sup> The viability of a purely fee-driven security budget remains a critical long-term consideration dependent on Bitcoin's future utility and adoption.<sup>98</sup>

## VII. Evaluating Core Value Propositions from First Principles

Based on the foundational design elements-digital scarcity, decentralization via P2P networking and PoW consensus, cryptographic security, and limited programmability-several core value propositions have emerged for Bitcoin. Evaluating these from first principles involves assessing their alignment with Bitcoin's inherent properties and the trade-offs involved.

### A. Bitcoin as a Store of Value (SoV)

The argument for Bitcoin as a store of value, often termed "digital gold," rests heavily on its inherent characteristics derived from its protocol rules.<sup>14</sup>

-   **Supporting Properties:**

    -   *Digital Scarcity:* This is arguably Bitcoin's strongest SoV attribute. The supply is strictly capped at 21 million coins, enforced by consensus rules and the halving mechanism, creating predictable and diminishing issuance.<sup>7</sup> Unlike fiat currencies or even gold (whose total mineable supply is unknown), Bitcoin's scarcity is absolute and algorithmically guaranteed.<sup>66</sup>

    -   *Durability:* As a digital asset existing on a globally distributed network, Bitcoin does not physically degrade and can persist as long as the network operates.<sup>7</sup>

    -   *Portability:* Bitcoins can be transferred globally across the internet without requiring physical transport or intermediaries, offering significant advantages over physical assets like gold.<sup>142</sup>

    -   *Divisibility:* Bitcoin is highly divisible, down to one hundred millionth of a coin (a satoshi), facilitating storage and transfer of precise values.<sup>199</sup>

    -   *Verifiability/Authenticity:* Ownership and the validity of coins can be cryptographically verified using public keys and signatures, and the entire transaction history and supply are auditable on the public blockchain by anyone running a node.<sup>1</sup> This contrasts with the difficulty and cost of verifying gold purity and ownership.

    -   *Fungibility:* While each bitcoin has a traceable history on the blockchain, individual units (satoshis) are generally treated as interchangeable in transactions.

    -   *Censorship/Seizure Resistance:* Due to its decentralized nature and reliance on private key control, bitcoins held in self-custody are highly resistant to censorship and confiscation by authorities, a key differentiator from traditional assets held within the banking system or physically.<sup>14</sup>

-   **Comparison to Gold:** Gold has served as a store of value for millennia, valued for its physical scarcity, durability, and societal acceptance.<sup>208</sup> Bitcoin shares the scarcity characteristic, arguably in a more verifiable and absolute digital form.<sup>208</sup> Bitcoin surpasses gold significantly in portability, divisibility, and verifiability.<sup>209</sup> However, gold benefits from a much longer history and established role, resulting in lower price volatility compared to Bitcoin.<sup>208</sup>

**Table VII.1: Bitcoin vs. Gold - Store of Value Attributes Comparison**

| **Attribute**               | **Bitcoin**                                                                                | **Gold**                                                                                                             |
|-----------------------------|--------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------|
| **Scarcity**                | Absolute (21M cap), algorithmically enforced, perfectly predictable issuance <sup>66</sup> | Finite (natural limit), but total mineable amount unknown, ongoing (though slow) extraction <sup>208</sup>           |
| **Durability**              | Digital, persists as long as network exists; keys can be lost <sup>7</sup>                 | Physical, highly durable, does not corrode <sup>230</sup>                                                            |
| **Portability**             | Extremely high; transferable globally via internet <sup>209</sup>                          | Low; physical transport is cumbersome and costly <sup>211</sup>                                                      |
| **Divisibility**            | High (down to 8 decimal places - satoshi) <sup>210</sup>                                   | Low; physical division is difficult and costly <sup>211</sup>                                                        |
| **Verifiability**           | High; authenticity and supply easily verifiable on public ledger via nodes <sup>37</sup>   | Moderate/Low; requires expertise and equipment to verify purity and weight; ownership harder to prove <sup>211</sup> |
| **Fungibility**             | High (generally treated as interchangeable, though transaction history exists)             | High (refined gold is uniform)                                                                                       |
| **Censorship/Seizure Res.** | High (if self-custodied); protocol resistant to external control <sup>132</sup>            | Moderate/Low; physical asset susceptible to confiscation; often held via custodians <sup>211</sup>                   |
| **Established History**     | Low (since 2009); nascent technology <sup>208</sup>                                        | Extremely High (thousands of years); established role in finance and culture <sup>208</sup>                          |
| **Volatility**              | High; significant price fluctuations <sup>208</sup>                                        | Low (relative to Bitcoin); considered more stable <sup>208</sup>                                                     |

-   **Limitations:** The primary challenge to Bitcoin's SoV status, viewed purely from its inherent properties, is its significant price volatility.<sup>212</sup> High volatility makes it difficult to reliably preserve purchasing power over short to medium time horizons, a key expectation for a store of value. Its relatively short history compared to gold also means it lacks the long track record of value preservation through diverse economic conditions.<sup>208</sup> Furthermore, some argue that an asset cannot be a store of value if it lacks significant utility as a medium of exchange, questioning the very premise if practical use remains limited.<sup>233</sup>

### B. Bitcoin as a Medium of Exchange (MoE)

Nakamoto's whitepaper explicitly proposed Bitcoin as a "Peer-to-Peer Electronic Cash System," indicating a primary goal of facilitating payments directly between parties without intermediaries.<sup>1</sup> Several inherent properties support this use case:

-   **Peer-to-Peer Transfer:** The protocol enables direct value transfer between users identified by cryptographic addresses.<sup>10</sup>

-   **Borderless:** Transactions can be sent globally across the internet to any participant on the network.<sup>13</sup>

-   **Divisibility:** High divisibility allows for transactions of varying sizes.<sup>210</sup>

However, fundamental design choices create inherent limitations for Bitcoin as a widespread MoE on its base layer:

-   **Scalability Limits:** The combination of the \~10-minute block interval and the block weight limit restricts the network's transaction processing capacity to approximately 3-7 transactions per second (TPS).<sup>67</sup> This is orders of magnitude lower than traditional payment networks like Visa.<sup>67</sup>

-   **Transaction Fees:** Due to limited block space, users compete to have their transactions included by attaching fees. During periods of high network demand (congestion), fees can rise significantly, making small-value transactions economically impractical.<sup>55</sup> Fee rates are typically measured in sats/vB (satoshis per virtual byte).<sup>55</sup>

-   **Confirmation Times:** A new block is mined approximately every 10 minutes. For a transaction to be considered reasonably secure, multiple confirmations (blocks mined after the one containing the transaction) are typically required (e.g., 6 confirmations for higher security), leading to settlement times ranging from minutes to over an hour.<sup>55</sup> This is unsuitable for point-of-sale or time-sensitive payments.

-   **Volatility:** High price volatility makes it challenging for merchants and consumers to use Bitcoin for pricing goods and services or for everyday payments, as the value can change significantly between the time of transaction and settlement.<sup>208</sup>

These base-layer limitations led to the development of Layer 2 scaling solutions, most notably the Lightning Network (LN).<sup>84</sup> The LN operates *on top* of Bitcoin, creating off-chain payment channels between users.<sup>84</sup> Within these channels, users can conduct a virtually unlimited number of transactions almost instantaneously and with extremely low fees (often fractions of a satoshi).<sup>84</sup> Transactions only need to touch the main Bitcoin blockchain when opening or closing a channel.<sup>239</sup> The LN uses routing through interconnected channels (facilitated by mechanisms like Multi-Path Payments - MPPs <sup>247</sup>) to enable payments between users who don't have a direct channel.<sup>226</sup> Theoretically, the LN can handle millions or even billions of TPS.<sup>239</sup> It enables micropayments, which are infeasible on the base layer due to fees.<sup>226</sup> While promising for improving Bitcoin's MoE capabilities, the LN introduces its own complexities and trade-offs, including the need for channel liquidity management, potential centralization risks around large routing hubs, and usability challenges, particularly for non-custodial solutions.<sup>239</sup> Importantly, the ultimate security and final settlement of LN transactions still rely on the underlying Bitcoin blockchain.<sup>245</sup>

### C. Bitcoin as a Censorship-Resistant Asset

This value proposition stems directly from Bitcoin's decentralized architecture and cryptographic foundations.<sup>14</sup>

-   **Supporting Properties:**

    -   *Decentralization:* The absence of a central controller (bank, government, company) makes it difficult for any single entity to dictate which transactions are allowed or to block specific users at the protocol level.<sup>3</sup>

    -   *Permissionless Access:* Anyone with an internet connection can generate keys, receive bitcoin, run a node, and broadcast transactions without needing permission from any authority.<sup>8</sup>

    -   *Proof-of-Work Consensus:* While miners select transactions, the competitive and distributed nature of mining makes systematic censorship of valid transactions difficult and costly, especially if users are willing to pay adequate fees.<sup>33</sup>

    -   *Seizure Resistance (Self-Custody):* If a user securely controls their private keys (self-custody), their bitcoins cannot be easily confiscated without physical coercion or compromising the keys.<sup>14</sup> This contrasts sharply with funds held in traditional financial institutions.

-   **Use Cases:** Bitcoin's censorship resistance makes it potentially valuable in contexts where traditional financial systems are restrictive, unstable, or subject to control. This includes use by individuals under oppressive regimes, in countries with strict capital controls, or as a means for cross-border value transfer resistant to interference.<sup>14</sup>

-   **Limitations:** Censorship resistance in Bitcoin is not absolute and faces practical challenges:

    -   *Interaction Points:* While the protocol itself is resistant, censorship can be enforced at points where users interact with the traditional financial system or regulated intermediaries, such as exchanges.<sup>190</sup> Governments can regulate or ban exchanges, making it difficult to convert bitcoin to/from fiat currency.

    -   *Privacy Limitations:* Bitcoin operates on a pseudonymous, not anonymous, basis. All transactions are public on the blockchain. While addresses are not directly linked to real-world identities in the protocol, blockchain analysis techniques can potentially link addresses together and, through off-chain information (e.g., exchange KYC), connect them to individuals.<sup>5</sup> This lack of strong privacy can make users vulnerable to targeted censorship or coercion if their identities become known.<sup>181</sup>

    -   *Network-Level Attacks:* Theoretical attacks on the P2P network layer, such as Eclipse attacks (isolating nodes) or Partitioning attacks (splitting the network), could potentially be used to censor transactions from specific nodes or regions, although these are complex and costly to execute effectively against a large, distributed network like Bitcoin.<sup>123</sup>

    -   *Fee Market Censorship:* While not direct censorship, miners prioritizing high-fee transactions can effectively "censor" low-fee transactions during periods of high congestion, making the network unusable for those unwilling or unable to pay high fees.<sup>227</sup>

Ultimately, Bitcoin's value propositions are direct outcomes of its first principles. The effectiveness of Bitcoin as an SoV, MoE, or censorship-resistant asset is inherently tied to the strengths and weaknesses embedded in its core design. The pursuit of scarcity and decentralized security necessarily involves trade-offs, particularly concerning base-layer scalability and transaction costs, which impacts its utility as a pure medium of exchange. Layer 2 solutions represent attempts to ameliorate these trade-offs by building functionalities on top of the base layer, acknowledging its inherent limitations while leveraging its core security guarantees.

## VIII. Inherent Design Limitations and Trade-offs

The fundamental design choices made by Satoshi Nakamoto, while enabling Bitcoin's core properties like decentralization and scarcity, also lead to inherent limitations and trade-offs. These are not flaws to be easily "fixed" but rather consequences of prioritizing certain characteristics over others, often framed within the concept of the Blockchain Trilemma.

### A. The Scalability Conundrum

Bitcoin's limited ability to process a high volume of transactions on its base layer is perhaps its most cited limitation, stemming directly from core design parameters intended to maintain decentralization and security.

-   **Low Throughput:** The Bitcoin network can only process a maximum of roughly 3-7 transactions per second (TPS).<sup>67</sup> This contrasts sharply with centralized payment networks like Visa, capable of handling thousands of TPS.<sup>67</sup> This low throughput is a direct result of two factors: the average 10-minute interval between block creation and the limit on the amount of data each block can contain.<sup>111</sup>

-   **Block Size/Weight Limit:** Originally, Bitcoin blocks had a strict 1 megabyte (MB) size limit, introduced partly as an anti-spam measure.<sup>112</sup> The Segregated Witness (SegWit) upgrade in 2017 introduced the concept of "block weight," separating signature data (witness) from transaction data and giving witness data a lower weight.<sup>81</sup> This effectively increased the capacity, allowing blocks up to a theoretical maximum of 4 megabytes (4 million weight units), though typical block sizes are often closer to 1.3-2 MB.<sup>81</sup> The debate around increasing the block size limit further (the "block size wars") highlighted a fundamental trade-off: larger blocks could increase TPS but would also increase the hardware requirements (storage, bandwidth) for running a full node, potentially centralizing node operation and harming the network's decentralization.<sup>9</sup>

-   **Fee Market and Congestion:** When the demand for transactions exceeds the available block space, a fee market emerges.<sup>55</sup> Users must bid higher fees (in sats/vB) to incentivize miners to include their transactions promptly.<sup>55</sup> This leads to volatile and potentially very high transaction fees during periods of congestion, making Bitcoin impractical for small, everyday payments on the base layer.<sup>55</sup>

-   **The Blockchain Trilemma:** Bitcoin's scalability limitations are a direct manifestation of the Blockchain Trilemma, which posits that it is difficult for a decentralized network to simultaneously optimize for scalability, security, and decentralization.<sup>67</sup> Bitcoin's design choices clearly prioritize security (via robust PoW and cryptography) and decentralization (via accessible node requirements and distributed consensus) at the expense of high on-chain transaction throughput.<sup>134</sup> Layer 2 solutions like the Lightning Network are attempts to improve scalability by moving transactions off the base layer, implicitly acknowledging the base layer's inherent constraints.<sup>111</sup>

### B. The Energy Debate

The Proof-of-Work consensus mechanism, while providing robust security and enabling decentralization, is inherently energy-intensive.

-   **PoW Energy Consumption:** Mining requires specialized hardware (ASICs) performing trillions of hash calculations per second to solve the cryptographic puzzle.<sup>16</sup> This computational effort directly translates into significant electricity consumption to power the mining rigs and associated cooling systems.<sup>15</sup>

-   **Estimates and Comparisons:** Quantifying Bitcoin's exact energy consumption is challenging due to the distributed and opaque nature of mining operations.<sup>256</sup> Leading estimates, such as the Cambridge Bitcoin Electricity Consumption Index (CBECI) and Digiconomist, provide ranges based on network hash rate and hardware efficiency assumptions. Estimates vary but often place Bitcoin's annual electricity consumption in the range of \~100-175 TWh, comparable to the consumption of entire mid-sized countries like Poland, Ukraine, or Argentina.<sup>68</sup> This represents a notable fraction (e.g., 0.6% - 2.3% in the US context) of global or national electricity use.<sup>257</sup>

-   **Environmental Impact:** The environmental impact, particularly the carbon footprint, depends heavily on the energy sources used by miners.<sup>68</sup> While some mining operations utilize renewable sources (like hydropower, particularly historically in regions like Sichuan, China, or currently in other areas), a significant portion still relies on fossil fuels, especially coal, contributing to substantial CO2 emissions (estimated in the tens of millions of tons annually, comparable to countries like Qatar or Singapore).<sup>68</sup> Concerns also exist regarding electronic waste (e-waste) from the rapid obsolescence of specialized ASIC hardware <sup>257</sup> and potential water usage for cooling.<sup>257</sup>

-   **Arguments For/Against:**

    -   *Criticisms:* The energy consumption is vast and disproportionate to the network's transaction throughput.<sup>256</sup> The computational work is "useless" outside of securing the network.<sup>68</sup> Reliance on fossil fuels contributes significantly to climate change.<sup>68</sup> Comparisons are often drawn to the much higher energy efficiency of Proof-of-Stake (PoS) systems, which Ethereum and other blockchains have adopted.<sup>15</sup>

    -   *Defenses:* Energy consumption is a fundamental requirement for PoW's security and decentralization; it's the "cost" of achieving trustlessness without intermediaries.<sup>68</sup> Bitcoin mining can monetize stranded or otherwise wasted energy resources, such as excess hydroelectric power or flared natural gas, potentially making renewables more viable or reducing methane emissions.<sup>68</sup> The energy expenditure is driven by market demand for Bitcoin's security and reflects the value participants place on it.<sup>267</sup> Bitcoin's total energy consumption remains a small fraction (less than 1%) of global energy use and comparable to other industries like gold mining, data centers, or even recreational activities.<sup>257</sup> Proponents argue that comparing energy per transaction is misleading, as Bitcoin's primary function might be settlement or store of value, not high-frequency payments like Visa.<sup>258</sup>

### C. Price Volatility

Bitcoin's price exhibits significantly higher volatility compared to traditional assets like gold, stocks, or fiat currencies, which impacts its usability as both a stable store of value and a predictable medium of exchange.<sup>208</sup> This volatility stems from several factors rooted in its fundamental nature and market context:

-   **Nascent Asset Class & Price Discovery:** As a relatively new asset class (existing since 2009), Bitcoin is still undergoing price discovery. The market is working to establish a consensus on its long-term fair value, leading to large price swings as new information, participants, and use cases emerge.<sup>208</sup>

-   **Inelastic Supply:** Bitcoin's supply is highly inelastic and algorithmically determined (fixed cap, halving schedule). Changes in demand therefore have a disproportionately large impact on price, as supply cannot quickly adjust to meet shifts in market sentiment or utility.<sup>213</sup>

-   **Speculation and Sentiment:** Due to the difficulty in applying traditional valuation models (no cash flows, limited industrial use), Bitcoin's price is heavily influenced by speculation, market sentiment, news events (positive or negative), media hype, and social media trends.<sup>213</sup> Fear Of Missing Out (FOMO) and Fear, Uncertainty, and Doubt (FUD) can drive rapid buying or selling pressure.<sup>213</sup>

-   **Market Structure and Liquidity:** While growing, the Bitcoin market still has lower liquidity and depth compared to mature traditional markets like equities or forex.<sup>213</sup> Large buy or sell orders, particularly from institutional players or "whales," can significantly move the market price.<sup>213</sup> Liquidity is also fragmented across numerous exchanges.<sup>215</sup>

-   **Regulatory Uncertainty:** The evolving and often uncertain regulatory landscape for cryptocurrencies globally creates significant risk and influences investor sentiment, leading to price reactions to regulatory news or actions.<sup>213</sup>

-   **Macroeconomic Factors:** Bitcoin's price is increasingly influenced by broader macroeconomic trends, such as inflation rates, interest rate policies by central banks, and geopolitical instability, as investors consider its role as a potential inflation hedge or risk asset.<sup>213</sup>

While Bitcoin's volatility has shown a decreasing trend over longer time frames as the market matures and institutional adoption increases, it remains substantially higher than traditional assets.<sup>209</sup>

### D. Security Vulnerabilities (Protocol/Network Level)

Despite its robust cryptographic foundations and PoW security model, Bitcoin is not immune to potential attacks, particularly those targeting the consensus mechanism or the P2P network layer.

-   **Consensus Attacks:**

    -   *51% Attack:* As previously discussed, an entity controlling &gt;50% of the network hash rate could theoretically rewrite recent blockchain history, primarily to double-spend their own transactions or prevent others' transactions from confirming.<sup>74</sup> While economically challenging for Bitcoin due to the immense cost <sup>85</sup>, it remains a fundamental theoretical vulnerability of PoW consensus.<sup>70</sup>

    -   *Selfish Mining:* A strategic deviation where miners withhold discovered blocks to gain an advantage over honest miners.<sup>72</sup> By selectively releasing their hidden chain, they can cause honest miners' blocks to be orphaned, increasing their relative share of block rewards beyond their hash rate proportion.<sup>72</sup> This attack becomes more effective and potentially profitable as an attacker's hash rate share increases (thresholds debated, potentially &gt;23-33%).<sup>72</sup>

    -   *Timejacking:* An attack manipulating a node's perception of time by feeding it inaccurate timestamps from malicious peers.<sup>73</sup> This could potentially trick a node into accepting an invalid chain, rejecting valid blocks, or miscalculating the difficulty adjustment.<sup>73</sup>

-   **P2P Network Attacks:** These attacks exploit vulnerabilities in the communication layer rather than the core cryptography or consensus rules.

    -   *Eclipse Attack:* An attacker isolates a specific victim node by monopolizing all its incoming and outgoing peer connections, feeding it false information about the blockchain state.<sup>74</sup> This can be used to trick the victim into accepting double-spends, waste mining power, or be censored from the true network state.<sup>192</sup> Countermeasures involve improving peer selection and connection management.<sup>191</sup>

    -   *Sybil Attack:* An attacker creates a large number of pseudonymous identities (nodes) to gain disproportionate influence on the network.<sup>33</sup> While PoW makes Sybil attacks on *consensus* (block creation) prohibitively expensive, Sybil nodes can still be used to manipulate peer discovery, aid Eclipse attacks, or potentially interfere with transaction/block propagation.<sup>75</sup>

    -   *Partitioning Attacks:* These aim to split the P2P network into two or more isolated segments, often by manipulating internet routing protocols (like BGP hijacking) or overwhelming node connections (connection starvation).<sup>123</sup> Partitioning can lead to different blockchain versions forming in each segment, causing inconsistencies, wasted mining effort, and potential double-spends when the partition heals.<sup>116</sup> The feasibility and sustainability of partitioning Bitcoin are debated, with network dynamics like churn and peer eviction mechanisms providing some resilience, but the potential impact remains a concern.<sup>116</sup>

-   **Bitcoin Script Limitations:** While enabling basic programmability, Bitcoin's scripting language (Script) has intentional limitations designed for security and predictability, which constrain its functionality compared to more expressive smart contract platforms.

    -   *Turing Incompleteness:* Script lacks complex loops and recursion capabilities, preventing infinite loops and ensuring that script execution terminates predictably.<sup>248</sup> This enhances security against denial-of-service attacks embedded in transactions but limits the complexity of computations possible directly on-chain.

    -   *Statelessness:* Scripts execute based only on the data provided within the transaction and the script itself; they cannot access or modify external state information beyond the UTXO being spent.<sup>275</sup> This simplifies validation but restricts the ability to create complex stateful contracts that track information over time or across multiple interactions.

    -   *Limited Opcodes:* The set of available operations (opcodes) is restricted, focusing on cryptographic checks (signatures, hashes), arithmetic, logic, stack manipulation, and flow control (conditionals, timelocks).<sup>275</sup> While enabling features like Pay-to-Public-Key-Hash (P2PKH), Multi-Signature (requiring M-of-N keys) <sup>122</sup>, Timelocks (absolute via OP\_CHECKLOCKTIMEVERIFY or relative via OP\_CHECKSEQUENCEVERIFY) <sup>122</sup>, and Pay-to-Script-Hash (P2SH) <sup>248</sup>, it cannot easily support arbitrary computations or complex application logic found on platforms like Ethereum. Enhancements like Taproot aim to improve script efficiency and privacy but still operate within these fundamental constraints.<sup>275</sup>

These limitations are intrinsic to Bitcoin's design philosophy, reflecting a prioritization of simplicity, security, and predictability for the base layer, often necessitating more complex functionalities be built on higher layers or sidechains. Bitcoin's security model is primarily economic and probabilistic rather than absolute; it relies on making attacks computationally and economically infeasible for rational actors under normal network conditions, rather than cryptographically impossible.

## IX. Synthesis: A First-Principles Perspective on Bitcoin

This analysis, grounded in Bitcoin's original whitepaper and core technical and economic components, provides a first-principles view of its fundamental nature. Bitcoin emerges not just as a digital currency, but as a complex, self-regulating system built on specific, interconnected principles designed to achieve a distinct set of goals.

Recap of Core Principles:

The foundational vision was a peer-to-peer electronic cash system minimizing reliance on trusted third parties.1 This is achieved through a combination of:

-   **Cryptography:** ECDSA for ownership via public/private keys and transaction authorization via digital signatures <sup>39</sup>, and SHA-256 hashing for data integrity, transaction identification, and Proof-of-Work.<sup>18</sup>

-   **Blockchain:** A distributed, timestamped, and effectively immutable ledger composed of cryptographically linked blocks containing verified transactions.<sup>1</sup>

-   **Proof-of-Work Consensus:** A mechanism using computational energy expenditure to secure the ledger, validate transactions, achieve decentralized agreement on the ledger's state, and govern new coin issuance.<sup>6</sup> The longest chain (most accumulated work) is accepted as the valid history.<sup>6</sup>

-   **Economic Model:** An algorithmically enforced fixed supply cap of 21 million coins, achieved through a diminishing block subsidy via periodic halving events, supplemented by a market-based transaction fee system.<sup>8</sup>

-   **Decentralization:** A P2P network architecture with distributed nodes validating rules, miners securing the chain, and an open-source development process governed by rough consensus among stakeholders.<sup>13</sup>

Inherent Strengths (Derived from First Principles):

These core principles give rise to Bitcoin's fundamental strengths:

-   **Decentralization Potential:** The architecture is designed to operate without central points of control or failure.

-   **Censorship Resistance:** The protocol inherently resists attempts to block or reverse valid transactions based on sender, receiver, or content.

-   **Seizure Resistance:** Control rests with the holder of the private keys, making assets difficult to confiscate when properly self-custodied.

-   **Transparency & Auditability:** The public ledger allows anyone to verify transactions and the total supply.

-   **Predictable & Scarce Monetary Policy:** The fixed supply cap and predetermined issuance schedule create verifiable digital scarcity, resistant to arbitrary inflation.

-   **Robust Security Model:** PoW provides strong (though not absolute) economic security against tampering with the ledger history.

Inherent Weaknesses/Trade-offs (Derived from First Principles):

The same design choices that create strengths also impose limitations, reflecting the Blockchain Trilemma:

-   **Scalability Limitations:** Prioritizing security and decentralization results in low base-layer transaction throughput, leading to potential network congestion and high fees.

-   **Energy Consumption:** The PoW security model is inherently energy-intensive.

-   **Price Volatility:** Factors like fixed supply, market nascency, and speculation contribute to significant price fluctuations, hindering stable SoV and MoE use cases.

-   **Limited Base-Layer Programmability:** The non-Turing complete, stateless scripting language prioritizes security and predictability over complex smart contract functionality on the main chain.

-   **Practical Centralization Vectors:** Despite the decentralized design, practical centralization can emerge in mining pool operations, hardware manufacturing, and potentially developer influence.

-   **Network Vulnerabilities:** The P2P network layer remains susceptible to specific attacks (e.g., partitioning, eclipse, Sybil) that could disrupt connectivity or enable targeted censorship/fraud.

-   **Long-Term Security Budget Uncertainty:** The eventual transition from block subsidies to transaction fees as the primary miner incentive introduces uncertainty about the long-term economic viability of maintaining sufficient network security.

Concluding Statement:

From a first-principles perspective, Bitcoin is best understood as a decentralized system for achieving consensus on a specific state (the ledger) through computationally expensive work, secured by cryptography and governed by pre-defined economic incentives. Its core value proposition lies in its ability to provide a censorship-resistant, seizure-resistant, digitally scarce asset with a predictable monetary policy, operating outside the control of traditional intermediaries. However, these properties are achieved through deliberate design trade-offs that inherently limit its base-layer scalability, programmability, and introduce significant energy consumption and price volatility. Its evolution and suitability for various use cases (Store of Value, Medium of Exchange) are fundamentally shaped by these inherent strengths and weaknesses derived directly from its foundational code and principles.

#### Works cited

1.  Bitcoin Whitepaper - Northcrypto, accessed May 1, 2025, [<u>https://www.northcrypto.com/learn/blog/bitcoin-whitepaper-eng</u>](https://www.northcrypto.com/learn/blog/bitcoin-whitepaper-eng)

2.  Bitcoin whitepaper - bitFlyer, accessed May 1, 2025, [<u>https://bitflyer.com/en-us/s/glossary/bitcoin-whitepaper</u>](https://bitflyer.com/en-us/s/glossary/bitcoin-whitepaper)

3.  The Bitcoin White Paper: Read & Download the Original PDF - Hodder Law, accessed May 1, 2025, [<u>https://hodder.law/bitcoin-white-paper/</u>](https://hodder.law/bitcoin-white-paper/)

4.  Bitcoin Whitepaper: Explained In Simple Terms - Trust Wallet, accessed May 1, 2025, [<u>https://trustwallet.com/blog/cryptocurrency/bitcoin-whitepaper-explained</u>](https://trustwallet.com/blog/cryptocurrency/bitcoin-whitepaper-explained)

5.  Bitcoin's White Paper Explained: A 9-Page Revolution in Digital Finance - CCN.com, accessed May 1, 2025, [<u>https://www.ccn.com/education/crypto/bitcoin-white-paper-9-page-revolution/</u>](https://www.ccn.com/education/crypto/bitcoin-white-paper-9-page-revolution/)

6.  Bitcoin: A Peer-to-Peer Electronic Cash System - United States Sentencing Commission, accessed May 1, 2025, [<u>https://www.ussc.gov/sites/default/files/pdf/training/annual-national-training-seminar/2018/Emerging\_Tech\_Bitcoin\_Crypto.pdf</u>](https://www.ussc.gov/sites/default/files/pdf/training/annual-national-training-seminar/2018/Emerging_Tech_Bitcoin_Crypto.pdf)

7.  The Bitcoin Whitepaper Summary - Bitcoin's first official document - Zerocap, accessed May 1, 2025, [<u>https://zerocap.com/insights/articles/the-bitcoin-whitepaper-summary/</u>](https://zerocap.com/insights/articles/the-bitcoin-whitepaper-summary/)

8.  The Bitcoin Whitepaper Explained:Key Takeaways in Simplified Terms - Kinesis Money, accessed May 1, 2025, [<u>https://kinesis.money/pro/articles/bitcoin/bitcoin-whitepaper-explained-key-takeaways/</u>](https://kinesis.money/pro/articles/bitcoin/bitcoin-whitepaper-explained-key-takeaways/)

9.  Bitcoin Years Later: Was the Nakamoto White Paper Right? - Investopedia, accessed May 1, 2025, [<u>https://www.investopedia.com/tech/return-nakamoto-white-paper-bitcoins-10th-birthday/</u>](https://www.investopedia.com/tech/return-nakamoto-white-paper-bitcoins-10th-birthday/)

10. A Peer-to-Peer Electronic Cash System - Bitcoin, accessed May 1, 2025, [<u>https://bitcoin.org/bitcoin.pdf</u>](https://bitcoin.org/bitcoin.pdf)

11. Bitcoin: A Peer-to-Peer Electronic Cash System - SEC.gov, accessed May 1, 2025, [<u>https://www.sec.gov/comments/s7-04-23/s70423-290181-707862.pdf</u>](https://www.sec.gov/comments/s7-04-23/s70423-290181-707862.pdf)

12. The Bitcoin Whitepaper simply explained - Bitpanda Academy, accessed May 1, 2025, [<u>https://www.bitpanda.com/academy/en/lessons/the-bitcoin-whitepaper-simply-explained</u>](https://www.bitpanda.com/academy/en/lessons/the-bitcoin-whitepaper-simply-explained)

13. scottgriv/bitcoin-white\_paper: Original Satoshi paper ("Bitcoin White Paper") in various formats. - GitHub, accessed May 1, 2025, [<u>https://github.com/scottgriv/bitcoin-white\_paper</u>](https://github.com/scottgriv/bitcoin-white_paper)

14. What is Bitcoin? Everything You Need to Know About BTC - OSL, accessed May 1, 2025, [<u>https://osl.com/academy/article/what-is-bitcoin-everything-you-need-to-know-about-btc</u>](https://osl.com/academy/article/what-is-bitcoin-everything-you-need-to-know-about-btc)

15. What Is Proof of Work (PoW) in Blockchain? - Investopedia, accessed May 1, 2025, [<u>https://www.investopedia.com/terms/p/proof-work.asp</u>](https://www.investopedia.com/terms/p/proof-work.asp)

16. How Does Bitcoin Mining Work? A Detailed Explanation of the Process - 21bitcoin, accessed May 1, 2025, [<u>https://21bitcoin.app/en/blog/how-does-bitcoin-mining-work</u>](https://21bitcoin.app/en/blog/how-does-bitcoin-mining-work)

17. Building Bitcoin's Proof of Work: A TypeScript Implementation Guide - Radzion.com, accessed May 1, 2025, [<u>https://radzion.com/blog/proof</u>](https://radzion.com/blog/proof)

18. Blockchain Hash Functions - Halborn, accessed May 1, 2025, [<u>https://www.halborn.com/blog/post/blockchain-hash-functions</u>](https://www.halborn.com/blog/post/blockchain-hash-functions)

19. Bitcoin - Keeping Proof of Work Decentralized - Fidelity Digital Assets, accessed May 1, 2025, [<u>https://www.fidelitydigitalassets.com/sites/g/files/djuvja3256/files/acquiadam/1075400.3.0%20-%20Bitcoin%20Keeping%20Proof%20of%20Work%20Decentralized%20%281%29.pdf</u>](https://www.fidelitydigitalassets.com/sites/g/files/djuvja3256/files/acquiadam/1075400.3.0%20-%20Bitcoin%20Keeping%20Proof%20of%20Work%20Decentralized%20%281%29.pdf)

20. Bitcoin Mining: Complete Guide for Beginners - Blockpit, accessed May 1, 2025, [<u>https://www.blockpit.io/en-us/blog/what-is-bitcoin-mining</u>](https://www.blockpit.io/en-us/blog/what-is-bitcoin-mining)

21. Top Bitcoin Nonce Easy Proof of Work and Hashing - Nadcab Labs, accessed May 1, 2025, [<u>https://www.nadcab.com/blog/bitcoin-nonce</u>](https://www.nadcab.com/blog/bitcoin-nonce)

22. Merkle Trees \| Cryptocurrency & Blockchain Technology - Freeman Law, accessed May 1, 2025, [<u>https://freemanlaw.com/merkle-trees-2/</u>](https://freemanlaw.com/merkle-trees-2/)

23. What Is a Merkle Tree & What Is Its Role in Blockchain? - OSL, accessed May 1, 2025, [<u>https://osl.com/academy/article/what-is-a-merkle-tree-and-what-is-its-role-in-blockchain</u>](https://osl.com/academy/article/what-is-a-merkle-tree-and-what-is-its-role-in-blockchain)

24. A Quick Guide to Blockchain: Merkle Tree - Analytics Vidhya, accessed May 1, 2025, [<u>https://www.analyticsvidhya.com/blog/2022/10/a-quick-guide-to-blockchain-merkle-tree/</u>](https://www.analyticsvidhya.com/blog/2022/10/a-quick-guide-to-blockchain-merkle-tree/)

25. Merkle Tree in Blockchain: What is it, How does it work and Benefits - Simplilearn.com, accessed May 1, 2025, [<u>https://www.simplilearn.com/tutorials/blockchain-tutorial/merkle-tree-in-blockchain</u>](https://www.simplilearn.com/tutorials/blockchain-tutorial/merkle-tree-in-blockchain)

26. Everything you need to know about Merkle trees - Bitpanda, accessed May 1, 2025, [<u>https://www.bitpanda.com/academy/en/lessons/everything-you-need-to-know-about-merkle-trees</u>](https://www.bitpanda.com/academy/en/lessons/everything-you-need-to-know-about-merkle-trees)

27. Merkle Tree in Blockchain: Understanding Crypto Data Storage - dYdX, accessed May 1, 2025, [<u>https://dydx.exchange/crypto-learning/merkle-tree</u>](https://dydx.exchange/crypto-learning/merkle-tree)

28. Merkle Root \| A Fingerprint for the Transactions in a Block - Learn Me A Bitcoin, accessed May 1, 2025, [<u>https://learnmeabitcoin.com/technical/block/merkle-root/</u>](https://learnmeabitcoin.com/technical/block/merkle-root/)

29. Blockchain Merkle Trees - GeeksforGeeks, accessed May 1, 2025, [<u>https://www.geeksforgeeks.org/blockchain-merkle-trees/</u>](https://www.geeksforgeeks.org/blockchain-merkle-trees/)

30. 2.2. Blocks, Transactions, and the Role of Hashing - Byte Federal, accessed May 1, 2025, [<u>https://www.bytefederal.com/byteu/11/128</u>](https://www.bytefederal.com/byteu/11/128)

31. SHA-256 in Blockchain: A Comprehensive Guide - DX Talks, accessed May 1, 2025, [<u>https://www.dxtalks.com/blog/news-2/sha-256-in-blockchain-everything-you-need-to-know-747</u>](https://www.dxtalks.com/blog/news-2/sha-256-in-blockchain-everything-you-need-to-know-747)

32. Securing Bitcoin: The Role of SHA-256 and Beyond - D-Central, accessed May 1, 2025, [<u>https://d-central.tech/securing-bitcoin-the-role-of-sha-256-and-beyond/</u>](https://d-central.tech/securing-bitcoin-the-role-of-sha-256-and-beyond/)

33. Exploring the Immutable: Can Bitcoin Transactions Be Censored? - D-Central Technologies, accessed May 1, 2025, [<u>https://d-central.tech/exploring-the-immutable-can-bitcoin-transactions-be-censored/</u>](https://d-central.tech/exploring-the-immutable-can-bitcoin-transactions-be-censored/)

34. What is a P2P Network? - Peer-to-Peer Networks \| Horizen Academy, accessed May 1, 2025, [<u>https://www.horizen.io/academy/peer-to-peer-networks-p2p/</u>](https://www.horizen.io/academy/peer-to-peer-networks-p2p/)

35. Bitcoin Node Distribution Live Map Chart - Newhedge, accessed May 1, 2025, [<u>https://newhedge.io/bitcoin/node-map</u>](https://newhedge.io/bitcoin/node-map)

36. This map shows distribution of reachable Bitcoin nodes in the world. Each one of these 10000+ nodes has an entire copy of the network's ledger, with every single transaction ever sent recorded and accounted for. They enforce and validate the rules of Bitcoin. - Reddit, accessed May 1, 2025, [<u>https://www.reddit.com/r/Bitcoin/comments/s6hefa/this\_map\_shows\_distribution\_of\_reachable\_bitcoin/</u>](https://www.reddit.com/r/Bitcoin/comments/s6hefa/this_map_shows_distribution_of_reachable_bitcoin/)

37. How Nodes Contribute to Security and Decentralization of the Bitcoin Network \| BitPay, accessed May 1, 2025, [<u>https://www.bitpay.com/blog/bitcoin-nodes</u>](https://www.bitpay.com/blog/bitcoin-nodes)

38. The Bitcoin Whitepaper, accessed May 1, 2025, [<u>https://bitcoin.com.au/education/the-bitcoin-whitepaper/</u>](https://bitcoin.com.au/education/the-bitcoin-whitepaper/)

39. ECDSA - River Financial, accessed May 1, 2025, [<u>https://river.com/learn/terms/e/ecdsa/</u>](https://river.com/learn/terms/e/ecdsa/)

40. 4\. Keys, Addresses - Mastering Bitcoin, 2nd Edition \[Book\] - O'Reilly Media, accessed May 1, 2025, [<u>https://www.oreilly.com/library/view/mastering-bitcoin-2nd/9781491954379/ch04.html</u>](https://www.oreilly.com/library/view/mastering-bitcoin-2nd/9781491954379/ch04.html)

41. What Is Elliptic Curve Digital Signature Algorithm? - ECDSA - Cyfrin, accessed May 1, 2025, [<u>https://www.cyfrin.io/blog/elliptic-curve-digital-signature-algorithm-and-signatures</u>](https://www.cyfrin.io/blog/elliptic-curve-digital-signature-algorithm-and-signatures)

42. ECDSA: Elliptic Curve Signatures - Practical Cryptography for Developers, accessed May 1, 2025, [<u>https://cryptobook.nakov.com/digital-signatures/ecdsa-sign-verify-messages</u>](https://cryptobook.nakov.com/digital-signatures/ecdsa-sign-verify-messages)

43. ECDSA \| Elliptic Curve Digital Signature Algorithm - Learn Me A Bitcoin, accessed May 1, 2025, [<u>https://learnmeabitcoin.com/technical/cryptography/elliptic-curve/ecdsa/</u>](https://learnmeabitcoin.com/technical/cryptography/elliptic-curve/ecdsa/)

44. Elliptic Curve Digital Signature Algorithm - Bitcoin Wiki, accessed May 1, 2025, [<u>https://en.bitcoin.it/wiki/Elliptic\_Curve\_Digital\_Signature\_Algorithm</u>](https://en.bitcoin.it/wiki/Elliptic_Curve_Digital_Signature_Algorithm)

45. Elliptic Curve in Bitcoin, accessed May 1, 2025, [<u>https://estudiobitcoin.com/elliptic-curve-in-bitcoin/</u>](https://estudiobitcoin.com/elliptic-curve-in-bitcoin/)

46. What is Secp256k1? Cryptocurrency's Key Elliptic Curve - Nervos Network, accessed May 1, 2025, [<u>https://www.nervos.org/knowledge-base/secp256k1\_a\_key%20algorithm\_(explainCKBot)</u>](https://www.nervos.org/knowledge-base/secp256k1_a_key%20algorithm_(explainCKBot))

47. Secp256k1 - River Financial, accessed May 1, 2025, [<u>https://river.com/learn/terms/s/secp256k1/</u>](https://river.com/learn/terms/s/secp256k1/)

48. Keys and Bitcoin Addresses: Elliptic Curve Cryptography Explained - Saylor Academy, accessed May 1, 2025, [<u>https://learn.saylor.org/mod/book/view.php?id=36353</u>](https://learn.saylor.org/mod/book/view.php?id=36353)

49. Elliptic Curve \| Mathematics for Cryptographic Systems - Learn Me A Bitcoin, accessed May 1, 2025, [<u>https://learnmeabitcoin.com/technical/cryptography/elliptic-curve/</u>](https://learnmeabitcoin.com/technical/cryptography/elliptic-curve/)

50. Secp256k1 - Bitcoin Wiki, accessed May 1, 2025, [<u>https://en.bitcoin.it/wiki/Secp256k1</u>](https://en.bitcoin.it/wiki/Secp256k1)

51. Security of the Secp256k1 Elliptic Curve used in the Bitcoin Blockchain:, accessed May 1, 2025, [<u>https://www.ijcns.latticescipub.com/wp-content/uploads/papers/v4i1/A1426054124.pdf</u>](https://www.ijcns.latticescipub.com/wp-content/uploads/papers/v4i1/A1426054124.pdf)

52. Digital Signatures - Learn Me A Bitcoin, accessed May 1, 2025, [<u>https://learnmeabitcoin.com/beginners/guide/digital-signatures/</u>](https://learnmeabitcoin.com/beginners/guide/digital-signatures/)

53. What Hashing Algorithm Does Bitcoin Use to Hash Blocks? - Crypto ..., accessed May 1, 2025, [<u>https://cryptohead.io/what-hashing-algorithm-does-bitcoin-use-to-hash-blocks/</u>](https://cryptohead.io/what-hashing-algorithm-does-bitcoin-use-to-hash-blocks/)

54. Understanding How ECDSA Protects Your Data. : 15 Steps - Instructables, accessed May 1, 2025, [<u>https://www.instructables.com/Understanding-how-ECDSA-protects-your-data/</u>](https://www.instructables.com/Understanding-how-ECDSA-protects-your-data/)

55. How do Bitcoin transactions work? - MtPelerin, accessed May 1, 2025, [<u>https://www.mtpelerin.com/blog/how-do-bitcoin-transactions-work</u>](https://www.mtpelerin.com/blog/how-do-bitcoin-transactions-work)

56. SHA-256 Cryptographic Hash Algorithm - Komodo Platform, accessed May 1, 2025, [<u>https://komodoplatform.com/en/academy/sha-256-algorithm/</u>](https://komodoplatform.com/en/academy/sha-256-algorithm/)

57. Satoshi Nakamoto - AWS, accessed May 1, 2025, [<u>https://libertyme-library.s3.amazonaws.com/\_Other+Books/Phil+Champagne/BookOfSatoshi.pdf</u>](https://libertyme-library.s3.amazonaws.com/_Other+Books/Phil+Champagne/BookOfSatoshi.pdf)

58. Bitcoin whitepaper: simplified for everyone - Coinbase, accessed May 1, 2025, [<u>https://www.coinbase.com/learn/crypto-basics/bitcoin-whitepaper-simplified-for-everyone</u>](https://www.coinbase.com/learn/crypto-basics/bitcoin-whitepaper-simplified-for-everyone)

59. Unpacking the Bitcoin Whitepaper - Uphold, accessed May 1, 2025, [<u>https://uphold.com/en-us/learn/intermediate/unpacking-the-bitcoin-whitepaper</u>](https://uphold.com/en-us/learn/intermediate/unpacking-the-bitcoin-whitepaper)

60. Proof of Work (PoW) Guide - Cryptohopper, accessed May 1, 2025, [<u>https://www.cryptohopper.com/blog/proof-of-work-pow-guide-10947</u>](https://www.cryptohopper.com/blog/proof-of-work-pow-guide-10947)

61. What Is Nakamoto Consensus? - Nervos Network, accessed May 1, 2025, [<u>https://www.nervos.org/knowledge-base/what\_is\_nakamoto\_consensus</u>](https://www.nervos.org/knowledge-base/what_is_nakamoto_consensus)

62. How the Nakamoto consensus powers Bitcoin - Cointelegraph, accessed May 1, 2025, [<u>https://cointelegraph.com/learn/articles/how-the-nakamoto-cconsensus-powers-bitcoin</u>](https://cointelegraph.com/learn/articles/how-the-nakamoto-cconsensus-powers-bitcoin)

63. What Is Nakamoto Consensus And How Does It Power Bitcoin?, accessed May 1, 2025, [<u>https://bitcoinmagazine.com/guides/what-is-nakamoto-consensus-bitcoin</u>](https://bitcoinmagazine.com/guides/what-is-nakamoto-consensus-bitcoin)

64. Cryptocurrency decentralization - Digiconomist, accessed May 1, 2025, [<u>https://digiconomist.net/cryptocurrency-decentralization/</u>](https://digiconomist.net/cryptocurrency-decentralization/)

65. How many bitcoin are there? Bitcoin supply explained - Kraken, accessed May 1, 2025, [<u>https://www.kraken.com/learn/how-many-bitcoin-are-there-bitcoin-supply-explained</u>](https://www.kraken.com/learn/how-many-bitcoin-are-there-bitcoin-supply-explained)

66. An overview of Bitcoin and its potential use cases - Fidelity Digital Assets, accessed May 1, 2025, [<u>https://www.fidelitydigitalassets.com/sites/g/files/djuvja3256/files/acquiadam/FDA%20Bitcoin%20Coin%20Report%20-%2012-06.pdf</u>](https://www.fidelitydigitalassets.com/sites/g/files/djuvja3256/files/acquiadam/FDA%20Bitcoin%20Coin%20Report%20-%2012-06.pdf)

67. A Deep Dive Into Blockchain Scalability - Crypto.com, accessed May 1, 2025, [<u>https://crypto.com/en/university/blockchain-scalability</u>](https://crypto.com/en/university/blockchain-scalability)

68. The Environmental Impact of Bitcoin - Pager Power, accessed May 1, 2025, [<u>https://www.pagerpower.com/news/the-environmental-impact-of-bitcoin/</u>](https://www.pagerpower.com/news/the-environmental-impact-of-bitcoin/)

69. The Sustainability of Bitcoin and its Impact on the Environment, accessed May 1, 2025, [<u>https://grc.berkeley.edu/the-sustainability-of-bitcoin-and-its-impact-on-the-environment/</u>](https://grc.berkeley.edu/the-sustainability-of-bitcoin-and-its-impact-on-the-environment/)

70. What is the Blockchain Trilemma? - SynFutures Academy, accessed May 1, 2025, [<u>https://academy.synfutures.com/the-blockchain-trilemma-security-scalability-and-decentralization-in-web3/</u>](https://academy.synfutures.com/the-blockchain-trilemma-security-scalability-and-decentralization-in-web3/)

71. (PDF) Bitcoin's Blockchain Peer-to-Peer Network Security Attacks and Countermeasures, accessed May 1, 2025, [<u>https://www.researchgate.net/publication/342983771\_Bitcoin's\_Blockchain\_Peer-to-Peer\_Network\_Security\_Attacks\_and\_Countermeasures</u>](https://www.researchgate.net/publication/342983771_Bitcoin's_Blockchain_Peer-to-Peer_Network_Security_Attacks_and_Countermeasures)

72. Statistical detection of selfish mining in proof-of-work blockchain systems - PMC, accessed May 1, 2025, [<u>https://pmc.ncbi.nlm.nih.gov/articles/PMC10943236/</u>](https://pmc.ncbi.nlm.nih.gov/articles/PMC10943236/)

73. On the Profitability of Selfish Mining Against Difficulty Adjustment Algorithms - Cryptology ePrint Archive, accessed May 1, 2025, [<u>https://eprint.iacr.org/2020/094.pdf</u>](https://eprint.iacr.org/2020/094.pdf)

74. The Different Bitcoin Mining Attacks Explained - D-Central Technologies, accessed May 1, 2025, [<u>https://d-central.tech/the-different-bitcoin-mining-attacks-explained/</u>](https://d-central.tech/the-different-bitcoin-mining-attacks-explained/)

75. Security Analysis of Cryptocurrency Protocols and Exchanges - Family Office Advisors, accessed May 1, 2025, [<u>https://groco.com/article/cryptocurrency-protocols-security/</u>](https://groco.com/article/cryptocurrency-protocols-security/)

76. Understanding Block Rewards \| Built In, accessed May 1, 2025, [<u>https://builtin.com/articles/block-reward</u>](https://builtin.com/articles/block-reward)

77. Velocity Propagation Protocol - ASU Blockchain Research - Arizona State University, accessed May 1, 2025, [<u>https://blockchain.asu.edu/velocity-scalability-improvements-in-block-propagation-through-rateless-erasure-coding</u>](https://blockchain.asu.edu/velocity-scalability-improvements-in-block-propagation-through-rateless-erasure-coding)

78. Bitcoin /BlockChain for Experts, accessed May 1, 2025, [<u>http://people.cs.uchicago.edu/\~huanke/Blockchain.pptx.pdf</u>](http://people.cs.uchicago.edu/~huanke/Blockchain.pptx.pdf)

79. mempool - Bitcoin Explorer, accessed May 1, 2025, [<u>https://mempool.space/</u>](https://mempool.space/)

80. Charts - Mempool Transaction Count - Blockchain.com, accessed May 1, 2025, [<u>https://www.blockchain.com/charts/mempool-count</u>](https://www.blockchain.com/charts/mempool-count)

81. Transaction Fee \| The Remainder of a Transaction - Learn Me A Bitcoin, accessed May 1, 2025, [<u>https://learnmeabitcoin.com/technical/transaction/fee/</u>](https://learnmeabitcoin.com/technical/transaction/fee/)

82. Bitcoin transaction Fees - cloudfront.net, accessed May 1, 2025, [<u>https://d2ghdaxqb194v2.cloudfront.net/2865/192262.pdf</u>](https://d2ghdaxqb194v2.cloudfront.net/2865/192262.pdf)

83. How Bitcoin Fees Work - River Financial, accessed May 1, 2025, [<u>https://river.com/learn/how-bitcoin-fees-work/</u>](https://river.com/learn/how-bitcoin-fees-work/)

84. Introduction to Channel Splicing on Bitcoin's Lightning Network - Fidelity Digital Assets, accessed May 1, 2025, [<u>https://www.fidelitydigitalassets.com/research-and-insights/introduction-channel-splicing-bitcoins-lightning-network</u>](https://www.fidelitydigitalassets.com/research-and-insights/introduction-channel-splicing-bitcoins-lightning-network)

85. What is a 51% attack? - Bitstamp, accessed May 1, 2025, [<u>https://www.bitstamp.net/en-gb/learn/security/what-is-a-51-percent-attack/</u>](https://www.bitstamp.net/en-gb/learn/security/what-is-a-51-percent-attack/)

86. Explaining the Bitcoin Block Reward - Argo Blockchain, accessed May 1, 2025, [<u>https://www.argoblockchain.com/articles/explaining-the-bitcoin-block-reward</u>](https://www.argoblockchain.com/articles/explaining-the-bitcoin-block-reward)

87. Block Reward \| Incentive for Miners to Mine Blocks, accessed May 1, 2025, [<u>https://learnmeabitcoin.com/technical/mining/block-reward/</u>](https://learnmeabitcoin.com/technical/mining/block-reward/)

88. What's the Difference Between Block Subsidy and Block Reward? - Nervos Network, accessed May 1, 2025, [<u>https://www.nervos.org/knowledge-base/difference\_block\_subsidy\_block\_reward\_(explainCKBot)</u>](https://www.nervos.org/knowledge-base/difference_block_subsidy_block_reward_(explainCKBot))

89. Challenges of Bitcoin Block Rewards for Miners - Nadcab Labs, accessed May 1, 2025, [<u>https://www.nadcab.com/blog/bitcoin-block-rewards</u>](https://www.nadcab.com/blog/bitcoin-block-rewards)

90. Mining Pools - MIT Digital Currency Initiative, accessed May 1, 2025, [<u>https://www.dci.mit.edu/s/WG20-21FidelityMining-uneditablewithcover.pdf</u>](https://www.dci.mit.edu/s/WG20-21FidelityMining-uneditablewithcover.pdf)

91. Bitcoin Halving Explained - Mintlayer, accessed May 1, 2025, [<u>https://www.mintlayer.org/blogs/bitcoin-halving</u>](https://www.mintlayer.org/blogs/bitcoin-halving)

92. Publish or Perish: A Backward-Compatible Defense against Selfish Mining in Bitcoin - COSIC - KU Leuven, accessed May 1, 2025, [<u>https://cosicdatabase.esat.kuleuven.be/backend/publications/files/conferencepaper/2746</u>](https://cosicdatabase.esat.kuleuven.be/backend/publications/files/conferencepaper/2746)

93. What Is Proof-of-work (PoW)? All You Need to Know - Blockworks, accessed May 1, 2025, [<u>https://blockworks.co/news/what-is-proof-of-work</u>](https://blockworks.co/news/what-is-proof-of-work)

94. Block Reward: Definition, How They Provide Incentive, and Future, accessed May 1, 2025, [<u>https://www.investopedia.com/terms/b/block-reward.asp</u>](https://www.investopedia.com/terms/b/block-reward.asp)

95. Bitcoin Mining Difficulty: What You Need to Know - Cointelegraph, accessed May 1, 2025, [<u>https://cointelegraph.com/learn/articles/bitcoin-mining-difficulty-explained</u>](https://cointelegraph.com/learn/articles/bitcoin-mining-difficulty-explained)

96. Target \| The Number you need to get below to Mine a Block, accessed May 1, 2025, [<u>https://learnmeabitcoin.com/technical/mining/target/</u>](https://learnmeabitcoin.com/technical/mining/target/)

97. The Power of Bitcoin Mining - Grayscale Research, accessed May 1, 2025, [<u>https://research.grayscale.com/reports/the-power-of-bitcoin-mining</u>](https://research.grayscale.com/reports/the-power-of-bitcoin-mining)

98. Security budget - Onramp Bitcoin, accessed May 1, 2025, [<u>https://onrampbitcoin.com/security-budget/</u>](https://onrampbitcoin.com/security-budget/)

99. What is the Difficulty in Bitcoin?, accessed May 1, 2025, [<u>https://learnmeabitcoin.com/beginners/guide/difficulty/</u>](https://learnmeabitcoin.com/beginners/guide/difficulty/)

100. Bitcoin Difficulty Adjustment Estimator - Newhedge, accessed May 1, 2025, [<u>https://newhedge.io/bitcoin/difficulty-estimator</u>](https://newhedge.io/bitcoin/difficulty-estimator)

101. Difficulty - Bitcoin Wiki, accessed May 1, 2025, [<u>https://en.bitcoin.it/wiki/Difficulty</u>](https://en.bitcoin.it/wiki/Difficulty)

102. Mining Fees, Block Data, Block Headers, and Proof-of-Work: Retargeting to Adjust Difficulty, accessed May 1, 2025, [<u>https://learn.saylor.org/mod/book/view.php?id=36375&chapterid=19023</u>](https://learn.saylor.org/mod/book/view.php?id=36375&chapterid=19023)

103. Bitcoin basics: What is the difficulty target and how does it adjust itself? - YouTube, accessed May 1, 2025, [<u>https://www.youtube.com/watch?v=iEL-y\_APu64</u>](https://www.youtube.com/watch?v=iEL-y_APu64)

104. Real-Time Block Rate Targeting - Ledger, accessed May 1, 2025, [<u>https://ledger.pitt.edu/ojs/ledger/article/download/195/187/1008</u>](https://ledger.pitt.edu/ojs/ledger/article/download/195/187/1008)

105. Difficulty adjustment mechanism : r/Bitcoin - Reddit, accessed May 1, 2025, [<u>https://www.reddit.com/r/Bitcoin/comments/zadgi7/difficulty\_adjustment\_mechanism/</u>](https://www.reddit.com/r/Bitcoin/comments/zadgi7/difficulty_adjustment_mechanism/)

106. Bitcoin Halving 2024 - Deltec Bank and Trust, accessed May 1, 2025, [<u>https://www.deltecbank.com/news-and-insights/bitcoin-halving-2024/</u>](https://www.deltecbank.com/news-and-insights/bitcoin-halving-2024/)

107. Understanding the Bitcoin Halving - Fidelity Digital Assets, accessed May 1, 2025, [<u>https://www.fidelitydigitalassets.com/research-and-insights/understanding-bitcoin-halving</u>](https://www.fidelitydigitalassets.com/research-and-insights/understanding-bitcoin-halving)

108. When will the Last Bitcoin be Mined? - Trakx, accessed May 1, 2025, [<u>https://trakx.io/resources/insights/when-will-the-last-bitcoin-be-mined/</u>](https://trakx.io/resources/insights/when-will-the-last-bitcoin-be-mined/)

109. BTC: Supply and Scarcity - Glassnode Studio, accessed May 1, 2025, [<u>https://studio.glassnode.com/dashboards/btc-supply-scarcity?referrer=use\_case</u>](https://studio.glassnode.com/dashboards/btc-supply-scarcity?referrer=use_case)

110. How Bitcoin Mining Incentives Balance Profitability and Network Security - CCN.com, accessed May 1, 2025, [<u>https://www.ccn.com/education/crypto/bitcoin-mining-incentives-profitability-network-security/</u>](https://www.ccn.com/education/crypto/bitcoin-mining-incentives-profitability-network-security/)

111. Bitcoin Scalability: What Is It & How Is It Being Addressed? - Xverse, accessed May 1, 2025, [<u>https://www.xverse.app/blog/bitcoin-scalability</u>](https://www.xverse.app/blog/bitcoin-scalability)

112. Understanding the Bitcoin Block Size Limit Debate and Its Implications - D-Central, accessed May 1, 2025, [<u>https://d-central.tech/what-is-the-bitcoin-block-size-limit/</u>](https://d-central.tech/what-is-the-bitcoin-block-size-limit/)

113. How is the target section of a block header calculated? - Bitcoin Stack Exchange, accessed May 1, 2025, [<u>https://bitcoin.stackexchange.com/questions/23912/how-is-the-target-section-of-a-block-header-calculated</u>](https://bitcoin.stackexchange.com/questions/23912/how-is-the-target-section-of-a-block-header-calculated)

114. The Economics of a Bitcoin Halving:A Miner's Perspective - Fidelity Digital Assets, accessed May 1, 2025, [<u>https://www.fidelitydigitalassets.com/research-and-insights/economics-bitcoin-halvinga-miners-perspective</u>](https://www.fidelitydigitalassets.com/research-and-insights/economics-bitcoin-halvinga-miners-perspective)

115. The Risks of the Blockchain A Review on Current Vulnerabilities and Attacks, accessed May 1, 2025, [<u>https://www.researchgate.net/publication/363091448\_The\_Risks\_of\_the\_Blockchain\_A\_Review\_on\_Current\_Vulnerabilities\_and\_Attacks</u>](https://www.researchgate.net/publication/363091448_The_Risks_of_the_Blockchain_A_Review_on_Current_Vulnerabilities_and_Attacks)

116. Churn in the Bitcoin Network: Characterization and Impact - BU Personal Websites, accessed May 1, 2025, [<u>https://people.bu.edu/staro/Characterizing\_churn.pdf</u>](https://people.bu.edu/staro/Characterizing_churn.pdf)

117. usa.visa.com, accessed May 1, 2025, [<u>https://usa.visa.com/solutions/crypto/consensus-mechanisms.html\#:\~:text=For%20example%2C%20Bitcoin%20uses%20the,explained%20in%20the%20PoW%20section).</u>](https://usa.visa.com/solutions/crypto/consensus-mechanisms.html#:~:text=For%20example%2C%20Bitcoin%20uses%20the,explained%20in%20the%20PoW%20section).)

118. Longest Chain \| The Blockchain that Nodes Adopt - Learn Me A Bitcoin, accessed May 1, 2025, [<u>https://learnmeabitcoin.com/technical/blockchain/longest-chain/</u>](https://learnmeabitcoin.com/technical/blockchain/longest-chain/)

119. Foundations of Blockchains Lectures \#8: Longest-Chain Consensus (ROUGH DRAFT) - GitHub Pages, accessed May 1, 2025, [<u>https://timroughgarden.github.io/fob21/l/l8.pdf</u>](https://timroughgarden.github.io/fob21/l/l8.pdf)

120. Assessing Blockchain Consensus and Security Mechanisms against the 51% Attack - MDPI, accessed May 1, 2025, [<u>https://www.mdpi.com/2076-3417/9/9/1788</u>](https://www.mdpi.com/2076-3417/9/9/1788)

121. Why 21 million as the number of bitcoins to be created? - Coinhouse, accessed May 1, 2025, [<u>https://www.coinhouse.com/insights/bitcoin/bitcoin-en/why-21-million</u>](https://www.coinhouse.com/insights/bitcoin/bitcoin-en/why-21-million)

122. Bitcoin Basics for Developers - Daily.dev, accessed May 1, 2025, [<u>https://daily.dev/blog/bitcoin-basics-for-developers</u>](https://daily.dev/blog/bitcoin-basics-for-developers)

123. Ask HN: What happens to blockchain transactions in case of network partition? \| Hacker News, accessed May 1, 2025, [<u>https://news.ycombinator.com/item?id=14594172</u>](https://news.ycombinator.com/item?id=14594172)

124. SoK: Security Analysis of Blockchain-based Cryptocurrency - arXiv, accessed May 1, 2025, [<u>https://arxiv.org/html/2503.22156v1</u>](https://arxiv.org/html/2503.22156v1)

125. 51% Attacks - MIT Digital Currency Initiative, accessed May 1, 2025, [<u>https://www.dci.mit.edu/projects/51-percent-attacks</u>](https://www.dci.mit.edu/projects/51-percent-attacks)

126. 51% Attacks: How They Work, Ramifications, & Safeguards - Corporate Finance Institute, accessed May 1, 2025, [<u>https://corporatefinanceinstitute.com/resources/cryptocurrency/what-is-a-51-attack/</u>](https://corporatefinanceinstitute.com/resources/cryptocurrency/what-is-a-51-attack/)

127. The 51% Attack on Blockchains: A Mining Behavior Study - ResearchGate, accessed May 1, 2025, [<u>https://www.researchgate.net/publication/355290937\_The\_51\_Attack\_on\_Blockchains\_A\_Mining\_Behavior\_Study</u>](https://www.researchgate.net/publication/355290937_The_51_Attack_on_Blockchains_A_Mining_Behavior_Study)

128. Raising the Security Bar? Dash Claims a 51% Attack Is Not Enough - Cointelegraph, accessed May 1, 2025, [<u>https://cointelegraph.com/news/raising-the-security-bar-dash-claims-a-51-attack-is-not-enough</u>](https://cointelegraph.com/news/raising-the-security-bar-dash-claims-a-51-attack-is-not-enough)

129. PoW vs PoS - Economic Cost To Attack - BitMEX Blog, accessed May 1, 2025, [<u>https://blog.bitmex.com/pow-vs-pos-economic-cost-to-attack/</u>](https://blog.bitmex.com/pow-vs-pos-economic-cost-to-attack/)

130. Charts - Hashrate Distribution - Blockchain.com, accessed May 1, 2025, [<u>https://www.blockchain.com/pools</u>](https://www.blockchain.com/pools)

131. Bitcoin: Fee-Based Security Modeling - Lyn Alden, accessed May 1, 2025, [<u>https://www.lynalden.com/bitcoin-security-modeling/</u>](https://www.lynalden.com/bitcoin-security-modeling/)

132. Why investors need to consider bitcoin separately from other digital assets, accessed May 1, 2025, [<u>https://www.fidelitydigitalassets.com/sites/g/files/djuvja3256/files/acquiadam/Bitcoin%20First\_Nov1%20%282%29.pdf</u>](https://www.fidelitydigitalassets.com/sites/g/files/djuvja3256/files/acquiadam/Bitcoin%20First_Nov1%20%282%29.pdf)

133. What Are Censorship-Resistant Blockchain Networks? - Gemini, accessed May 1, 2025, [<u>https://www.gemini.com/cryptopedia/what-is-censorship-resistance-bitcoin-censorship-resistant</u>](https://www.gemini.com/cryptopedia/what-is-censorship-resistance-bitcoin-censorship-resistant)

134. Comparing Monolithic vs.Modular Blockchains - Fidelity Digital Assets, accessed May 1, 2025, [<u>https://www.fidelitydigitalassets.com/research-and-insights/comparing-monolithic-vsmodular-blockchains</u>](https://www.fidelitydigitalassets.com/research-and-insights/comparing-monolithic-vsmodular-blockchains)

135. Is Bitcoin bad for the environment? Targeting ESG-friendly crypto investments - Britannica, accessed May 1, 2025, [<u>https://www.britannica.com/money/cryptocurrency-environmental-impact</u>](https://www.britannica.com/money/cryptocurrency-environmental-impact)

136. Cryptocurrency-Security-Audit-Guide/Blockchain-Common-Vulnerability-List.md at main, accessed May 1, 2025, [<u>https://github.com/slowmist/Cryptocurrency-Security-Audit-Guide/blob/main/Blockchain-Common-Vulnerability-List.md</u>](https://github.com/slowmist/Cryptocurrency-Security-Audit-Guide/blob/main/Blockchain-Common-Vulnerability-List.md)

137. Blockchain Security: A Comparative Analysis of Threats and Countermeasures, accessed May 1, 2025, [<u>https://www.jdcs.ir/article\_214052\_fed04a2a1e32eaf0541cc0bd7bc34173.pdf</u>](https://www.jdcs.ir/article_214052_fed04a2a1e32eaf0541cc0bd7bc34173.pdf)

138. Full article: Security and dependability analysis of blockchain systems in partially synchronous networks with Byzantine faults - Taylor & Francis Online, accessed May 1, 2025, [<u>https://www.tandfonline.com/doi/full/10.1080/17445760.2023.2272777</u>](https://www.tandfonline.com/doi/full/10.1080/17445760.2023.2272777)

139. Poster: Hades: Practical Partitioning Attack on Cryptocurrencies - Network and Distributed System Security (NDSS) Symposium, accessed May 1, 2025, [<u>https://www.ndss-symposium.org/wp-content/uploads/2023/02/NDSS2023Poster\_paper\_8997.pdf</u>](https://www.ndss-symposium.org/wp-content/uploads/2023/02/NDSS2023Poster_paper_8997.pdf)

140. Bitcoin Governance: Decisions in the Bitcoin Ecosystem - bitcoindepot.com, accessed May 1, 2025, [<u>https://bitcoindepot.com/bitcoin-atm-info/bitcoin-governance-how-decisions-are-made-in-the-bitcoin-ecosystem/</u>](https://bitcoindepot.com/bitcoin-atm-info/bitcoin-governance-how-decisions-are-made-in-the-bitcoin-ecosystem/)

141. What is censorship resistance in blockchain technology? - Cointelegraph, accessed May 1, 2025, [<u>https://cointelegraph.com/explained/what-is-censorship-resistance-in-blockchain-technology</u>](https://cointelegraph.com/explained/what-is-censorship-resistance-in-blockchain-technology)

142. Popular Cryptocurrencies & Their Use Cases - Caleb & Brown, accessed May 1, 2025, [<u>https://calebandbrown.com/blog/types-of-crypto/</u>](https://calebandbrown.com/blog/types-of-crypto/)

143. What is censorship resistance? \| Get Started with Bitcoin.com, accessed May 1, 2025, [<u>https://www.bitcoin.com/get-started/what-is-censorship-resistance/</u>](https://www.bitcoin.com/get-started/what-is-censorship-resistance/)

144. Bitcoin Governance as a Decentralized Financial Market Infrastructure, accessed May 1, 2025, [<u>https://stanford-jblp.pubpub.org/pub/bitcoin-governance</u>](https://stanford-jblp.pubpub.org/pub/bitcoin-governance)

145. Bitcoin Scarcity and Store-of-Value Attributes - Global X ETFs, accessed May 1, 2025, [<u>https://www.globalxetfs.com/bitcoin-scarcity-and-store-of-value-attributes/</u>](https://www.globalxetfs.com/bitcoin-scarcity-and-store-of-value-attributes/)

146. Bitcoin Scaling Solutions And Their Downsides - Bates White, accessed May 1, 2025, [<u>https://www.bateswhite.com/media/publication/172\_Bitcoin\_Scaling\_Solutions\_And\_Their\_Downsides.pdf</u>](https://www.bateswhite.com/media/publication/172_Bitcoin_Scaling_Solutions_And_Their_Downsides.pdf)

147. The Blockchain Trilemma: Decentralization, Security & Scalability - Webopedia, accessed May 1, 2025, [<u>https://www.webopedia.com/crypto/learn/blockchain-trilemma-explained/</u>](https://www.webopedia.com/crypto/learn/blockchain-trilemma-explained/)

148. Understanding The Blockchain Trilemma: A Beginner's Guide - CCN.com, accessed May 1, 2025, [<u>https://www.ccn.com/education/understanding-the-blockchain-trilemma-a-beginners-guide/</u>](https://www.ccn.com/education/understanding-the-blockchain-trilemma-a-beginners-guide/)

149. Blockchain trilemma: decentralization, security, and scalability challenges explained - Trezor, accessed May 1, 2025, [<u>https://trezor.io/learn/a/what-is-the-blockchain-trilemma</u>](https://trezor.io/learn/a/what-is-the-blockchain-trilemma)

150. P2P Network - Bitcoin, accessed May 1, 2025, [<u>https://developer.bitcoin.org/devguide/p2p\_network.html</u>](https://developer.bitcoin.org/devguide/p2p_network.html)

151. Information Propagation in the Bitcoin Network - UCSB Computer Science, accessed May 1, 2025, [<u>https://sites.cs.ucsb.edu/\~rich/class/cs293b-cloud/papers/bitcoin-delay</u>](https://sites.cs.ucsb.edu/~rich/class/cs293b-cloud/papers/bitcoin-delay)

152. 6\. The Bitcoin Network - Mastering Bitcoin \[Book\] - O'Reilly Media, accessed May 1, 2025, [<u>https://www.oreilly.com/library/view/mastering-bitcoin/9781491902639/ch06.html</u>](https://www.oreilly.com/library/view/mastering-bitcoin/9781491902639/ch06.html)

153. The Bitcoin Network - Saylor Academy, accessed May 1, 2025, [<u>https://learn.saylor.org/mod/book/tool/print/index.php?id=36307</u>](https://learn.saylor.org/mod/book/tool/print/index.php?id=36307)

154. SoK: Network-Level Attacks on the Bitcoin P2P Network - UPF, accessed May 1, 2025, [<u>https://repositori-api.upf.edu/api/core/bitstreams/8cc0b3c9-d076-4ba5-90d6-231c3b2ffc03/content</u>](https://repositori-api.upf.edu/api/core/bitstreams/8cc0b3c9-d076-4ba5-90d6-231c3b2ffc03/content)

155. ConMan: A Connection Manipulation-based Attack Against Bitcoin Networking - NSF-PAR, accessed May 1, 2025, [<u>https://par.nsf.gov/servlets/purl/10292392</u>](https://par.nsf.gov/servlets/purl/10292392)

156. (PDF) SoK: Network-Level Attacks on the Bitcoin P2P Network - ResearchGate, accessed May 1, 2025, [<u>https://www.researchgate.net/publication/363312986\_SoK\_Network-Level\_Attacks\_on\_the\_Bitcoin\_P2P\_Network</u>](https://www.researchgate.net/publication/363312986_SoK_Network-Level_Attacks_on_the_Bitcoin_P2P_Network)

157. Statistical and clustering analysis of attributes of Bitcoin backbone nodes - PubMed Central, accessed May 1, 2025, [<u>https://pmc.ncbi.nlm.nih.gov/articles/PMC10631630/</u>](https://pmc.ncbi.nlm.nih.gov/articles/PMC10631630/)

158. Global Bitcoin Nodes by Country - Bitnodes, accessed May 1, 2025, [<u>https://bitnodes.io/nodes/all/countries/1d/</u>](https://bitnodes.io/nodes/all/countries/1d/)

159. Reachable Bitcoin Nodes - Bitnodes, accessed May 1, 2025, [<u>https://bitnodes.io/?The=</u>](https://bitnodes.io/?The)

160. Bitnodes: Reachable Bitcoin Nodes, accessed May 1, 2025, [<u>https://bitnodes.io/</u>](https://bitnodes.io/)

161. Bitcoin Network 1 Year Charts - Bitnodes, accessed May 1, 2025, [<u>https://bitnodes.io/dashboard/1y/</u>](https://bitnodes.io/dashboard/1y/)

162. Blockchain meets Internet Routing, accessed May 1, 2025, [<u>https://btc-hijack.ethz.ch/</u>](https://btc-hijack.ethz.ch/)

163. The Ultimate Deep Dive Into Bitcoin's Security Model \| CoinMarketCap, accessed May 1, 2025, [<u>https://coinmarketcap.com/academy/article/the-ultimate-deep-dive-into-bitcoin-s-security-model</u>](https://coinmarketcap.com/academy/article/the-ultimate-deep-dive-into-bitcoin-s-security-model)

164. Mining Pool Stats - En - Braiins Academy, accessed May 1, 2025, [<u>https://academy.braiins.com/en/mining-insights/mining-pool-stats/</u>](https://academy.braiins.com/en/mining-insights/mining-pool-stats/)

165. GHash.io - Wikipedia, accessed May 1, 2025, [<u>https://en.wikipedia.org/wiki/GHash.io</u>](https://en.wikipedia.org/wiki/GHash.io)

166. Decentralized Mining in Centralized Pools - NYU Law, accessed May 1, 2025, [<u>http://www.law.nyu.edu/sites/default/files/upload\_documents/SSRN-id3160046\_1.pdf</u>](http://www.law.nyu.edu/sites/default/files/upload_documents/SSRN-id3160046_1.pdf)

167. Decentralized Mining in Centralized Pools - Duke Seminars, accessed May 1, 2025, [<u>https://ipl.econ.duke.edu/seminars/system/files/seminars/2265.pdf</u>](https://ipl.econ.duke.edu/seminars/system/files/seminars/2265.pdf)

168. Bitcoin's Blockchain Peer-to-Peer Network Security Attacks and Countermeasures, accessed May 1, 2025, [<u>https://sciresol.s3.us-east-2.amazonaws.com/IJST/Articles/Feb/3rd%20issue/149691.pdf</u>](https://sciresol.s3.us-east-2.amazonaws.com/IJST/Articles/Feb/3rd%20issue/149691.pdf)

169. Exploring Partitioning Attacks on the Bitcoin Network \| Request PDF - ResearchGate, accessed May 1, 2025, [<u>https://www.researchgate.net/publication/354110070\_Exploring\_Partitioning\_Attacks\_on\_the\_Bitcoin\_Network</u>](https://www.researchgate.net/publication/354110070_Exploring_Partitioning_Attacks_on_the_Bitcoin_Network)

170. How Many Bitcoin Are Left to Mine? \| Bitcoin's Supply Explained, accessed May 1, 2025, [<u>https://www.rhinobitcoin.com/blog/how-many-bitcoin-left-mined</u>](https://www.rhinobitcoin.com/blog/how-many-bitcoin-left-mined)

171. Cambridge Digital Mining Industry Report, accessed May 1, 2025, [<u>https://www.jbs.cam.ac.uk/wp-content/uploads/2025/04/2025-04-cambridge-digital-mining-industry-report.pdf</u>](https://www.jbs.cam.ac.uk/wp-content/uploads/2025/04/2025-04-cambridge-digital-mining-industry-report.pdf)

172. Bitcoin hashrate distribution as of 24 October, 2019. - ResearchGate, accessed May 1, 2025, [<u>https://www.researchgate.net/figure/Bitcoin-hashrate-distribution-as-of-24-October-2019\_fig2\_338647150</u>](https://www.researchgate.net/figure/Bitcoin-hashrate-distribution-as-of-24-October-2019_fig2_338647150)

173. The Anonymous Bitcoin.org Owner Accuses BTC Mining Pools of Centralization, accessed May 1, 2025, [<u>https://news.bitcoin.com/the-anonymous-bitcoin-org-owner-accuses-btc-mining-pools-of-centralization/</u>](https://news.bitcoin.com/the-anonymous-bitcoin-org-owner-accuses-btc-mining-pools-of-centralization/)

174. Bitmain Nears 51% of Network Hash Rate: Why This Matters and Why It Doesn't \| Nasdaq, accessed May 1, 2025, [<u>https://www.nasdaq.com/articles/bitmain-nears-51-of-network-hash-rate:-why-this-matters-and-why-it-doesnt-2018-06-28</u>](https://www.nasdaq.com/articles/bitmain-nears-51-of-network-hash-rate:-why-this-matters-and-why-it-doesnt-2018-06-28)

175. The centralization of Bitcoin: Behind the two mining pools controlling 51% of the global hash rate - CryptoSlate, accessed May 1, 2025, [<u>https://cryptoslate.com/behind-the-two-mining-pools-controlling-51-percent-of-the-global-hash-rate/</u>](https://cryptoslate.com/behind-the-two-mining-pools-controlling-51-percent-of-the-global-hash-rate/)

176. GHash gains 51 percent of Bitcoin's mining power, should you worry? - SiliconANGLE, accessed May 1, 2025, [<u>https://siliconangle.com/2014/06/17/ghash-gains-51-percent-of-bitcoins-mining-power-should-you-worry/</u>](https://siliconangle.com/2014/06/17/ghash-gains-51-percent-of-bitcoins-mining-power-should-you-worry/)

177. Bitcoin Mining Pool Ghash.io DDos-ed in Response to threat of 51% attack? - CCN.com, accessed May 1, 2025, [<u>https://www.ccn.com/bitcoin-mining-pool-ghash-io-ddos-ed-response-51-attack/</u>](https://www.ccn.com/bitcoin-mining-pool-ghash-io-ddos-ed-response-51-attack/)

178. The large environmental consequences of bitcoin mining - LSE Business Review, accessed May 1, 2025, [<u>https://blogs.lse.ac.uk/businessreview/2024/11/08/the-large-environmental-consequences-of-bitcoin-mining/</u>](https://blogs.lse.ac.uk/businessreview/2024/11/08/the-large-environmental-consequences-of-bitcoin-mining/)

179. arXiv:2504.20838v1 \[cs.CY\] 29 Apr 2025, accessed May 1, 2025, [<u>https://arxiv.org/pdf/2504.20838</u>](https://arxiv.org/pdf/2504.20838)

180. Bitcoin Governance: What are BIPs and how do they work? - sFOX, accessed May 1, 2025, [<u>https://www.sfox.com/blog/bitcoin-governance-what-are-bips-and-how-do-they-work/</u>](https://www.sfox.com/blog/bitcoin-governance-what-are-bips-and-how-do-they-work/)

181. July 2018 Journal - WORDS Bitcoin Journal, accessed May 1, 2025, [<u>https://bitcoinwords.github.io/cy18m7</u>](https://bitcoinwords.github.io/cy18m7)

182. How does a blockchain decide its future direction? - Uphold, accessed May 1, 2025, [<u>https://uphold.com/en-us/learn/advanced/evolution-of-a-blockchain</u>](https://uphold.com/en-us/learn/advanced/evolution-of-a-blockchain)

183. Bitcoin Governance Explained - YouTube, accessed May 1, 2025, [<u>https://www.youtube.com/watch?v=HwqpbyZ\_0T4</u>](https://www.youtube.com/watch?v=HwqpbyZ_0T4)

184. Bitcoin's Next Major Upgrade: A Comprehensive Assessment of OP\_CAT and OP\_CTV, accessed May 1, 2025, [<u>https://www.galaxy.com/insights/research/bitcoins-next-major-upgrade-op-cat-and-op-ctv/</u>](https://www.galaxy.com/insights/research/bitcoins-next-major-upgrade-op-cat-and-op-ctv/)

185. What is a Bitcoin Improvement Proposal (BIP)? And How Does It Work? - DeFi Planet, accessed May 1, 2025, [<u>https://defi-planet.com/2023/10/what-is-a-bitcoin-improvement-proposal-bip-and-how-does-it-work/</u>](https://defi-planet.com/2023/10/what-is-a-bitcoin-improvement-proposal-bip-and-how-does-it-work/)

186. What are Bitcoin improvement proposals (BIPs), and how do they work? - Cointelegraph, accessed May 1, 2025, [<u>https://cointelegraph.com/explained/what-are-bitcoin-improvement-proposals-bips-and-how-do-they-work</u>](https://cointelegraph.com/explained/what-are-bitcoin-improvement-proposals-bips-and-how-do-they-work)

187. bitcoin-cap/bcap: Repo for Analyzing Bitcoin Consensus: Risks in Protocol Upgrades - GitHub, accessed May 1, 2025, [<u>https://github.com/bitcoin-cap/bcap</u>](https://github.com/bitcoin-cap/bcap)

188. Bitcoin as Decentralized Money: Prices, Mining, and Network Security, accessed May 1, 2025, [<u>https://www.jbs.cam.ac.uk/wp-content/uploads/2020/08/paper-pagnotta-bitcoinasdecentralisedmoney.pdf</u>](https://www.jbs.cam.ac.uk/wp-content/uploads/2020/08/paper-pagnotta-bitcoinasdecentralisedmoney.pdf)

189. Bitcoin in Times of Economic Crisis: Is It Still a Hedge or Just Another Risk Asset?, accessed May 1, 2025, [<u>https://www.ccn.com/education/crypto/bitcoin-economic-crisis-hedge-or-risk-explained/</u>](https://www.ccn.com/education/crypto/bitcoin-economic-crisis-hedge-or-risk-explained/)

190. How Censorship Resistant Are Decentralized Systems? - Liberty Street Economics, accessed May 1, 2025, [<u>https://libertystreeteconomics.newyorkfed.org/2025/02/how-censorship-resistant-are-decentralized-systems/</u>](https://libertystreeteconomics.newyorkfed.org/2025/02/how-censorship-resistant-are-decentralized-systems/)

191. Eclipse Attack Explained: Safeguard Your Mobile App's Data Integrity, accessed May 1, 2025, [<u>https://www.zimperium.com/glossary/eclipse-attack/</u>](https://www.zimperium.com/glossary/eclipse-attack/)

192. Eclipse attack vs. Sybil attack - Bitcoin Stack Exchange, accessed May 1, 2025, [<u>https://bitcoin.stackexchange.com/questions/61151/eclipse-attack-vs-sybil-attack</u>](https://bitcoin.stackexchange.com/questions/61151/eclipse-attack-vs-sybil-attack)

193. Eclipse Attacks on Bitcoin's Peer-to-Peer Network - USENIX, accessed May 1, 2025, [<u>https://www.usenix.org/conference/usenixsecurity15/technical-sessions/presentation/heilman</u>](https://www.usenix.org/conference/usenixsecurity15/technical-sessions/presentation/heilman)

194. Security Threats Classification in Blockchains - The Repository at St. Cloud State, accessed May 1, 2025, [<u>https://repository.stcloudstate.edu/cgi/viewcontent.cgi?article=1093&context=msia\_etds</u>](https://repository.stcloudstate.edu/cgi/viewcontent.cgi?article=1093&context=msia_etds)

195. Crypto Use Cases \| Galaxy, accessed May 1, 2025, [<u>https://www.galaxy.com/insights/research/crypto-use-cases/</u>](https://www.galaxy.com/insights/research/crypto-use-cases/)

196. Bitcoin Halving 2024: Impact, Predictions & Expert Analysis \[NEW\] - Blockpit, accessed May 1, 2025, [<u>https://www.blockpit.io/en-us/blog/bitcoin-halving</u>](https://www.blockpit.io/en-us/blog/bitcoin-halving)

197. Hot Topics in International Trade - April 2025 - Security for New Bitcoin Strategic Reserve, accessed May 1, 2025, [<u>https://www.jdsupra.com/legalnews/hot-topics-in-international-trade-april-3555770/</u>](https://www.jdsupra.com/legalnews/hot-topics-in-international-trade-april-3555770/)

198. Understanding Bitcoin's 21 Million Cap - Kelly+Partners, accessed May 1, 2025, [<u>https://www.kellypartners.com.au/insights-centre/understanding-bitcoins-21-million-cap?hsLang=en-au</u>](https://www.kellypartners.com.au/insights-centre/understanding-bitcoins-21-million-cap?hsLang=en-au)

199. What Happens to Bitcoin After All 21 Million Are Mined? - Investopedia, accessed May 1, 2025, [<u>https://www.investopedia.com/tech/what-happens-bitcoin-after-21-million-mined/</u>](https://www.investopedia.com/tech/what-happens-bitcoin-after-21-million-mined/)

200. How does the bitcoin source code define its 21 million cap? - Unchained, accessed May 1, 2025, [<u>https://unchained.com/blog/bitcoin-source-code-21-million</u>](https://unchained.com/blog/bitcoin-source-code-21-million)

201. Can Bitcoin's Hard Cap of 21 Million Be Changed? \| River, accessed May 1, 2025, [<u>https://river.com/learn/can-bitcoins-hard-cap-of-21-million-be-changed/</u>](https://river.com/learn/can-bitcoins-hard-cap-of-21-million-be-changed/)

202. Bitcoin Halving 2024 - This Time It's Different - CME Group, accessed May 1, 2025, [<u>https://www.cmegroup.com/articles/2024/bitcoin-halving-2024-this-time-its-different.html</u>](https://www.cmegroup.com/articles/2024/bitcoin-halving-2024-this-time-its-different.html)

203. The Bitcoin Halving explained \| EY - Switzerland, accessed May 1, 2025, [<u>https://www.ey.com/en\_ch/insights/blockchain/the-bitcoin-halving-explained</u>](https://www.ey.com/en_ch/insights/blockchain/the-bitcoin-halving-explained)

204. Controlled supply - Bitcoin Wiki, accessed May 1, 2025, [<u>https://en.bitcoin.it/wiki/Controlled\_supply</u>](https://en.bitcoin.it/wiki/Controlled_supply)

205. How Many Bitcoin Are There? How Much Supply Left to Mine? - Bitbo, accessed May 1, 2025, [<u>https://bitbo.io/how-many-bitcoin/</u>](https://bitbo.io/how-many-bitcoin/)

206. Bitcoin's Market Cycle & Crypto Cycles Chart \| Key Insights & Trends - Caleb & Brown, accessed May 1, 2025, [<u>https://calebandbrown.com/blog/bitcoins-market-cycle/</u>](https://calebandbrown.com/blog/bitcoins-market-cycle/)

207. Charts - Total Circulating Bitcoin - Blockchain.com, accessed May 1, 2025, [<u>https://www.blockchain.com/charts/total-bitcoins</u>](https://www.blockchain.com/charts/total-bitcoins)

208. Bitcoin vs. Gold: Which Is a Better Store of Value? - OSL, accessed May 1, 2025, [<u>https://osl.com/academy/article/bitcoin-vs-gold-which-is-a-better-store-of-value</u>](https://osl.com/academy/article/bitcoin-vs-gold-which-is-a-better-store-of-value)

209. Comparing Bitcoin and Gold - NYDIG, accessed May 1, 2025, [<u>https://www.nydig.com/research/comparing-bitcoin-and-gold</u>](https://www.nydig.com/research/comparing-bitcoin-and-gold)

210. Bitcoin vs. Gold: A Comparative Analysis - Coinmetro, accessed May 1, 2025, [<u>https://www.coinmetro.com/learning-lab/bitcoin-vs.-gold</u>](https://www.coinmetro.com/learning-lab/bitcoin-vs.-gold)

211. Bitcoin vs. Gold - River Financial, accessed May 1, 2025, [<u>https://river.com/learn/bitcoin-vs-gold/</u>](https://river.com/learn/bitcoin-vs-gold/)

212. Gold Vs Bitcoin As Safe Haven Assets: A Comparative Research - Trakx, accessed May 1, 2025, [<u>https://trakx.io/resources/research/gold-vs-bitcoin-safe-haven-asset/</u>](https://trakx.io/resources/research/gold-vs-bitcoin-safe-haven-asset/)

213. Bitcoin Volatility Explained: Causes, Trends & Trading Strategies \| Caleb & Brown, accessed May 1, 2025, [<u>https://calebandbrown.com/blog/bitcoin-volatility/</u>](https://calebandbrown.com/blog/bitcoin-volatility/)

214. Bitcoin Volatility: What Causes BTC Price Swings? \| Crypto.com, accessed May 1, 2025, [<u>https://crypto.com/en/bitcoin/why-is-bitcoins-price-volatile</u>](https://crypto.com/en/bitcoin/why-is-bitcoins-price-volatile)

215. Why is Crypto So Volatile? Understanding Market Movements - Caleb & Brown, accessed May 1, 2025, [<u>https://calebandbrown.com/blog/crypto-volatility/</u>](https://calebandbrown.com/blog/crypto-volatility/)

216. On Bitcoin's transaction fees - Collin Rukundo, accessed May 1, 2025, [<u>https://rukundo.mataroa.blog/blog/on-bitcoins-transaction-fees-dfd72e50/</u>](https://rukundo.mataroa.blog/blog/on-bitcoins-transaction-fees-dfd72e50/)

217. Bitcoin Halving: What It Is and Why It Matters for Crypto Investors - Investopedia, accessed May 1, 2025, [<u>https://www.investopedia.com/bitcoin-halving-4843769</u>](https://www.investopedia.com/bitcoin-halving-4843769)

218. Bitcoin halving dates history - StormGain, accessed May 1, 2025, [<u>https://stormgain.com/blog/bitcoin-halving-dates-history</u>](https://stormgain.com/blog/bitcoin-halving-dates-history)

219. Will Fees Alone Keep the Bitcoin Network Secure in the Long Term? - Blockworks, accessed May 1, 2025, [<u>https://blockworks.co/news/bitcoin-network-secure-fees</u>](https://blockworks.co/news/bitcoin-network-secure-fees)

220. Why is Bitcoin Volatile? An Overview of Bitcoin Price Fluctuations - VanEck, accessed May 1, 2025, [<u>https://www.vaneck.com/us/en/blogs/digital-assets/bitcoin-volatility/</u>](https://www.vaneck.com/us/en/blogs/digital-assets/bitcoin-volatility/)

221. Trends, Tips, Tolls: A Longitudinal Study of Bitcoin Transaction Fees - Malte Möser, accessed May 1, 2025, [<u>https://maltemoeser.de/paper/transaction-fees.pdf</u>](https://maltemoeser.de/paper/transaction-fees.pdf)

222. Bitcoin Transaction Fees - Explained - 101 Blockchains, accessed May 1, 2025, [<u>https://101blockchains.com/bitcoin-transaction-fees-explained/</u>](https://101blockchains.com/bitcoin-transaction-fees-explained/)

223. Bitcoin Transaction Fees Explained \| Tangem Blog, accessed May 1, 2025, [<u>https://tangem.com/en/blog/post/bitcoin-transaction-fees/</u>](https://tangem.com/en/blog/post/bitcoin-transaction-fees/)

224. Sats/vB Meaning - Ledger, accessed May 1, 2025, [<u>https://www.ledger.com/academy/glossary/sats-vb</u>](https://www.ledger.com/academy/glossary/sats-vb)

225. Sats/vB Meaning in Crypto - Tangem, accessed May 1, 2025, [<u>https://tangem.com/en/glossary/sats-vb/</u>](https://tangem.com/en/glossary/sats-vb/)

226. Bitcoin Scalability Solutions: Lightning Network and Segregated Witness (SegWit) - Hakia, accessed May 1, 2025, [<u>https://hakia.com/bitcoin-scalability-solutions-lightning-network-and-segregated-witness-segwit/</u>](https://hakia.com/bitcoin-scalability-solutions-lightning-network-and-segregated-witness-segwit/)

227. Guide to Blockchain Scalability: Bitcoin Scalability Problem and Effects - Master The Crypto, accessed May 1, 2025, [<u>https://masterthecrypto.com/blockchain-scalability-bitcoin-scalability-problem-effects/</u>](https://masterthecrypto.com/blockchain-scalability-bitcoin-scalability-problem-effects/)

228. Layer-1 And Layer-2 Blockchain Scaling Solutions, Explained - CCN.com, accessed May 1, 2025, [<u>https://www.ccn.com/education/layer-1-and-layer-2-blockchain-scaling-solutions/</u>](https://www.ccn.com/education/layer-1-and-layer-2-blockchain-scaling-solutions/)

229. On the Instability of Bitcoin Without the Block Reward - cs.Princeton, accessed May 1, 2025, [<u>https://www.cs.princeton.edu/\~arvindn/publications/mining\_CCS.pdf</u>](https://www.cs.princeton.edu/~arvindn/publications/mining_CCS.pdf)

230. Gold vs Bitcoin: The Battle of the Safe Havens - Coin Bazaar, accessed May 1, 2025, [<u>https://coinbazaar.in/blog/gold-vs-bitcoin-the-battle-of-the-safe-havens/</u>](https://coinbazaar.in/blog/gold-vs-bitcoin-the-battle-of-the-safe-havens/)

231. Demystifying Blockchain and Cryptocurrency Ideologies - Insight Partners, accessed May 1, 2025, [<u>https://www.insightpartners.com/ideas/demystifying-blockchain-and-cryptocurrency-ideologies/</u>](https://www.insightpartners.com/ideas/demystifying-blockchain-and-cryptocurrency-ideologies/)

232. Bitcoin versus Fiat Currency: An Ethical Perspective - Stellenbosch University, accessed May 1, 2025, [<u>https://scholar.sun.ac.za/bitstreams/5c1f0ef2-94e4-4488-9eb0-c2fadaad8867/download</u>](https://scholar.sun.ac.za/bitstreams/5c1f0ef2-94e4-4488-9eb0-c2fadaad8867/download)

233. Putting an End to the Bitcoin Store of Value Fallacy, accessed May 1, 2025, [<u>https://news.bitcoin.com/putting-an-end-to-the-bitcoin-store-of-value-fallacy/</u>](https://news.bitcoin.com/putting-an-end-to-the-bitcoin-store-of-value-fallacy/)

234. Bitcoin vs. Gold: What's the Difference? - VALR's blog, accessed May 1, 2025, [<u>https://blog.valr.com/blog/bitcoin-vs-gold-whats-the-difference</u>](https://blog.valr.com/blog/bitcoin-vs-gold-whats-the-difference)

235. osl.com, accessed May 1, 2025, [<u>https://osl.com/academy/article/bitcoin-vs-gold-which-is-a-better-store-of-value\#:\~:text=Gold%20typically%20exhibits%20lower%20volatility,can%20attract%20risk%2Dseeking%20investors.</u>](https://osl.com/academy/article/bitcoin-vs-gold-which-is-a-better-store-of-value#:~:text=Gold%20typically%20exhibits%20lower%20volatility,can%20attract%20risk%2Dseeking%20investors.)

236. Bitcoin as an Investment and Hedge Alternative. A DCC MGARCH Model Analysis, accessed May 1, 2025, [<u>https://www.researchgate.net/publication/367862639\_Bitcoin\_as\_an\_Investment\_and\_Hedge\_Alternative\_A\_DCC\_MGARCH\_Model\_Analysis</u>](https://www.researchgate.net/publication/367862639_Bitcoin_as_an_Investment_and_Hedge_Alternative_A_DCC_MGARCH_Model_Analysis)

237. calebandbrown.com, accessed May 1, 2025, [<u>https://calebandbrown.com/blog/bitcoin-volatility/\#:\~:text=Compared%20to%20traditional%20financial%20markets,can%20create%20sudden%20price%20fluctuations.</u>](https://calebandbrown.com/blog/bitcoin-volatility/#:~:text=Compared%20to%20traditional%20financial%20markets,can%20create%20sudden%20price%20fluctuations.)

238. What affects crypto's price? \| Crypto volatility - Fidelity Investments, accessed May 1, 2025, [<u>https://www.fidelity.com/learning-center/trading-investing/bitcoin-price</u>](https://www.fidelity.com/learning-center/trading-investing/bitcoin-price)

239. The Lightning Network: Bitcoin's Layer 2 Scaling Solution - Arch Lending, accessed May 1, 2025, [<u>https://archlending.com/blog/lightning-network</u>](https://archlending.com/blog/lightning-network)

240. Lightning : le protocole de transmission à haut débit de Bitcoin - CoinShares, accessed May 1, 2025, [<u>https://coinshares.com/lu/insights/research-data/lightning-explained-bitcoin-high-speed-transmission-protocol/</u>](https://coinshares.com/lu/insights/research-data/lightning-explained-bitcoin-high-speed-transmission-protocol/)

241. Bitcoin Lightning Network Explained - Caleb & Brown, accessed May 1, 2025, [<u>https://calebandbrown.com/blog/bitcoin-lightning-network-explained/</u>](https://calebandbrown.com/blog/bitcoin-lightning-network-explained/)

242. Bitcoin's Lightning Network: 3 Possible Problems - Investopedia, accessed May 1, 2025, [<u>https://www.investopedia.com/tech/bitcoin-lightning-network-problems/</u>](https://www.investopedia.com/tech/bitcoin-lightning-network-problems/)

243. Bitcoin scalability problem - Wikipedia, accessed May 1, 2025, [<u>https://en.wikipedia.org/wiki/Bitcoin\_scalability\_problem</u>](https://en.wikipedia.org/wiki/Bitcoin_scalability_problem)

244. Performance-Based Analysis of Blockchain Scalability Metric, accessed May 1, 2025, [<u>https://hrcak.srce.hr/file/367642</u>](https://hrcak.srce.hr/file/367642)

245. The Bitcoin Lightning Network - NYDIG, accessed May 1, 2025, [<u>https://www.nydig.com/learn/the-bitcoin-lightning-network</u>](https://www.nydig.com/learn/the-bitcoin-lightning-network)

246. On the Impact of the Lightning Network on Bitcoin Transaction Fees and Network Value, accessed May 1, 2025, [<u>https://www.researchgate.net/publication/383488750\_On\_the\_Impact\_of\_the\_Lightning\_Network\_on\_Bitcoin\_Transaction\_Fees\_and\_Network\_Value</u>](https://www.researchgate.net/publication/383488750_On_the_Impact_of_the_Lightning_Network_on_Bitcoin_Transaction_Fees_and_Network_Value)

247. What are multi-path payments on the Bitcoin blockchain? - Lightspark, accessed May 1, 2025, [<u>https://www.lightspark.com/learn/bitcoin/what-are-multi-path-payments-on-the-bitcoin-blockchain</u>](https://www.lightspark.com/learn/bitcoin/what-are-multi-path-payments-on-the-bitcoin-blockchain)

248. What Are Bitcoin Smart Contracts? A Complete Guide \| Sovryn, accessed May 1, 2025, [<u>https://sovryn.com/all-things-sovryn/bitcoin-smart-contracts</u>](https://sovryn.com/all-things-sovryn/bitcoin-smart-contracts)

249. On the Sustainability of Bitcoin Partitioning Attacks - Research Collection, accessed May 1, 2025, [<u>https://www.research-collection.ethz.ch/bitstream/handle/20.500.11850/611944/fc23-final204.pdf</u>](https://www.research-collection.ethz.ch/bitstream/handle/20.500.11850/611944/fc23-final204.pdf)

250. On the Sustainability of Bitcoin Partitioning Attacks, accessed May 1, 2025, [<u>https://fc23.ifca.ai/preproceedings/204.pdf</u>](https://fc23.ifca.ai/preproceedings/204.pdf)

251. A Simulation Model for Analysis of Attacks on the Bitcoin Peer-to-Peer Network - Philipp Andelfinger, accessed May 1, 2025, [<u>https://philipp-andelfinger.net/pdfs/neudecker2015simulation.pdf</u>](https://philipp-andelfinger.net/pdfs/neudecker2015simulation.pdf)

252. Protecting Bitcoin against Routing Attacks, accessed May 1, 2025, [<u>https://netsyn.princeton.edu/sites/g/files/toruqf3201/files/documents/ndss2019\_slides.pdf</u>](https://netsyn.princeton.edu/sites/g/files/toruqf3201/files/documents/ndss2019_slides.pdf)

253. What is the blockchain trilemma? - Coinbase, accessed May 1, 2025, [<u>https://www.coinbase.com/learn/crypto-glossary/what-is-the-blockchain-trilemma</u>](https://www.coinbase.com/learn/crypto-glossary/what-is-the-blockchain-trilemma)

254. The Blockchain Trilemma: A Formal Proof of the Inherent Trade-Offs Among Decentralization, Security, and Scalability - MDPI, accessed May 1, 2025, [<u>https://www.mdpi.com/2076-3417/15/1/19</u>](https://www.mdpi.com/2076-3417/15/1/19)

255. The Blockchain Trilemma: Fast, Secure, and Scalable Networks - Gemini, accessed May 1, 2025, [<u>https://www.gemini.com/cryptopedia/blockchain-trilemma-decentralization-scalability-definition</u>](https://www.gemini.com/cryptopedia/blockchain-trilemma-decentralization-scalability-definition)

256. An Analysis of Energy Consumption and Carbon Footprints of Cryptocurrencies and Possible Solutions - arXiv, accessed May 1, 2025, [<u>https://arxiv.org/pdf/2203.03717</u>](https://arxiv.org/pdf/2203.03717)

257. What's the Environmental Impact of Cryptocurrency? - Investopedia, accessed May 1, 2025, [<u>https://www.investopedia.com/tech/whats-environmental-impact-cryptocurrency/</u>](https://www.investopedia.com/tech/whats-environmental-impact-cryptocurrency/)

258. Bitcoin Energy Consumption Index - Digiconomist, accessed May 1, 2025, [<u>https://digiconomist.net/bitcoin-energy-consumption</u>](https://digiconomist.net/bitcoin-energy-consumption)

259. Tracking electricity consumption from U.S. cryptocurrency mining operations - U.S. Energy Information Administration (EIA), accessed May 1, 2025, [<u>https://www.eia.gov/todayinenergy/detail.php?id=61364</u>](https://www.eia.gov/todayinenergy/detail.php?id=61364)

260. Bitcoin Mining's Energy Consumption and Global Carbon Dioxide Emissions: Wavelet Coherence Analysis, accessed May 1, 2025, [<u>https://www.amf.org.ae/sites/default/files/publications/2022-06/Bitcoin%20Minings%20Energy%20Consumption%20final.pdf</u>](https://www.amf.org.ae/sites/default/files/publications/2022-06/Bitcoin%20Minings%20Energy%20Consumption%20final.pdf)

261. Digital gold? UNM Economics professors help decode the high cost of Bitcoin mining, accessed May 1, 2025, [<u>https://news.unm.edu/news/digital-gold</u>](https://news.unm.edu/news/digital-gold)

262. Explained: Proof-of-Work vs. Proof-of-Stake Carbon Footprint - Bitwave, accessed May 1, 2025, [<u>https://www.bitwave.io/blog/explained-proof-of-work-vs-proof-of-stake-carbon-footprint</u>](https://www.bitwave.io/blog/explained-proof-of-work-vs-proof-of-stake-carbon-footprint)

263. Is Proof-of-Stake Really More Energy-Efficient Than Proof-of-Work? - Bitwave, accessed May 1, 2025, [<u>https://www.bitwave.io/blog/is-proof-of-stake-really-more-energy-efficient-than-proof-of-work</u>](https://www.bitwave.io/blog/is-proof-of-stake-really-more-energy-efficient-than-proof-of-work)

264. Cryptocurrency's Energy Consumption Problem - RMI, accessed May 1, 2025, [<u>https://rmi.org/cryptocurrencys-energy-consumption-problem/</u>](https://rmi.org/cryptocurrencys-energy-consumption-problem/)

265. Bitcoin GHG Emissions: Comparisons - Cambridge Centre for Alternative Finance, accessed May 1, 2025, [<u>https://ccaf.io/cbnsi/cbeci/ghg/comparisons</u>](https://ccaf.io/cbnsi/cbeci/ghg/comparisons)

266. Fact-Checking 8 Claims About Crypto's Climate Impact - Time, accessed May 1, 2025, [<u>https://time.com/6193004/crypto-climate-impact-facts/</u>](https://time.com/6193004/crypto-climate-impact-facts/)

267. Bitcoin's Energy Usage Isn't a Problem. Here's Why. - Lyn Alden, accessed May 1, 2025, [<u>https://www.lynalden.com/bitcoin-energy/</u>](https://www.lynalden.com/bitcoin-energy/)

268. Why Is Bitcoin Volatile? - Investopedia, accessed May 1, 2025, [<u>https://www.investopedia.com/articles/investing/052014/why-bitcoins-value-so-volatile.asp</u>](https://www.investopedia.com/articles/investing/052014/why-bitcoins-value-so-volatile.asp)

269. Why is Bitcoin Volatile? An Overview of Bitcoin Price Fluctuations - VanEck, accessed May 1, 2025, [<u>https://www.vaneck.com/fi/en/blog/digital-assets/why-is-bitcoin-volatile-an-overview-of-bitcoin-pricefluctuations/</u>](https://www.vaneck.com/fi/en/blog/digital-assets/why-is-bitcoin-volatile-an-overview-of-bitcoin-pricefluctuations/)

270. Bitcoin Selfish Mining Modeling and Dependability Analysis - ODU Digital Commons, accessed May 1, 2025, [<u>https://digitalcommons.odu.edu/cgi/viewcontent.cgi?article=1314&context=ece\_fac\_pubs</u>](https://digitalcommons.odu.edu/cgi/viewcontent.cgi?article=1314&context=ece_fac_pubs)

271. An Analysis of Attacks on Blockchain Consensus - ResearchGate, accessed May 1, 2025, [<u>https://www.researchgate.net/publication/309424665\_An\_Analysis\_of\_Attacks\_on\_Blockchain\_Consensus</u>](https://www.researchgate.net/publication/309424665_An_Analysis_of_Attacks_on_Blockchain_Consensus)

272. NC-Max: Breaking the Security-Performance Tradeoff in Nakamoto Consensus - Cryptology ePrint Archive, accessed May 1, 2025, [<u>https://eprint.iacr.org/2020/1101.pdf</u>](https://eprint.iacr.org/2020/1101.pdf)

273. Examining Attacks on Consensus and Incentive Systems in Proof-of-Work Blockchains: A Systematic Literature Review - arXiv, accessed May 1, 2025, [<u>https://arxiv.org/html/2411.00349v2</u>](https://arxiv.org/html/2411.00349v2)

274. Detection and Mitigation of the Eclipse Attack in Chord Overlays, accessed May 1, 2025, [<u>https://re.public.polimi.it/bitstream/11311/994720/5/panzeri.pdf</u>](https://re.public.polimi.it/bitstream/11311/994720/5/panzeri.pdf)

275. Authorization and Authentication, accessed May 1, 2025, [<u>https://bitcoinbook.hankmo.com/ch07\_authorization-authentication.html</u>](https://bitcoinbook.hankmo.com/ch07_authorization-authentication.html)

276. What is Bitcoin Script? Unveiling Its Role in Bitcoin - Komodo Platform, accessed May 1, 2025, [<u>https://komodoplatform.com/en/academy/bitcoin-script/</u>](https://komodoplatform.com/en/academy/bitcoin-script/)

277. HTX Ventures: Bitcoin Scripting Advances Unlock Potential for Secure and Scalable BTCFI, accessed May 1, 2025, [<u>https://www.prnewswire.com/in/news-releases/htx-ventures-bitcoin-scripting-advances-unlock-potential-for-secure-and-scalable-btcfi-302246924.html</u>](https://www.prnewswire.com/in/news-releases/htx-ventures-bitcoin-scripting-advances-unlock-potential-for-secure-and-scalable-btcfi-302246924.html)

278. Advanced Transactions and Scripting - Saylor Academy, accessed May 1, 2025, [<u>https://learn.saylor.org/mod/book/tool/print/index.php?id=36369</u>](https://learn.saylor.org/mod/book/tool/print/index.php?id=36369)

279. Chapter 7: 'Advanced Transactions and Scripting' · GitBook, accessed May 1, 2025, [<u>https://cypherpunks-core.github.io/bitcoinbook/ch07.html</u>](https://cypherpunks-core.github.io/bitcoinbook/ch07.html)

280. BitVM 2: Opening Up The Playing Field - Bitcoin Magazine, accessed May 1, 2025, [<u>https://bitcoinmagazine.com/technical/bitvm-2-opening-up-the-playing-field</u>](https://bitcoinmagazine.com/technical/bitvm-2-opening-up-the-playing-field)
