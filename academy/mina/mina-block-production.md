# Mina Block Production

## Block Production and Consensus Mechanism in Mina <a href="#block-production-and-consensus-mechanism-in-mina" id="block-production-and-consensus-mechanism-in-mina"></a>

In the Mina blockchain **validators** are **nodes** that produce **blocks** in the course of **Consensus**. In Mina Consensus is run on the **Ouroboros Samasika** Consensus mechanism. A **validator** in the blockchain which will produce a new block is chosen randomly based on its **stake**. The bigger stake a validator has, the more chances there are that this validator will win a new block. For producing blocks validators and their delegators win a **reward**. The selection mechanism is random in its nature and is built around a **VRF** (verifiable random function), that is any node can be selected for block production, though the chances depend on the validator stake.

### Glossary Reference 1

{% hint style="info" %}
**Block** - a discrete unit of a blockchain that carries information about transactions, which is recorded in a special cryptographic way.

**Consensus** - a process by which individual sections of a network define uniform rules and agree upon adding new blocks to the blockchain.

**Node** - a device (such as a computer) that contains a copy of the blockchain's transaction history and maintains a blockchain.

**Ouroboros Samasika** - a robustly secure PoS protocol that combines the best features of each Iteration of Ouroboros to provide a PoS mechanism, allowing far forks, requiring no history, or risking centralization by relying on trusted third parties to provide information about forks.

**Reward** - tokens paid to a block producer for block production to encourage its engagement in maintaining the blockchain consistency.

**Stake** - the share of staked validator tokens in total staked tokens.

**Validator** - a node that maintains the integrity of the blockchain by constantly calculating the link from the first block to the last one and by approving new blocks created by block producers.

**VRF (Verifiable Random Function)** - a function used to select a block producer for a slot and takes as input a random seed obtained from the output of the previous epoch's VRF, in addition to the public key and the current rate registry, and is deterministic.

See [Mina glossary](mina-glossary.md).
{% endhint %}

When a block is added to the blockchain, the winning block producer generates a hash, which contains a part of the previous block hash. In the course of the Consensus validators sign the block, and if it receives the majority of signatures (51% and over), it enters the blockchain. In Mina, unlike other blockchains, it’s OK if there are multiple signatures with one public key, meaning that one account can sign a block twice or more.

The process of block creation is rather straightforward and it looks as follows:

1. Block production starts at the beginning of an **epoch**. Each time a transaction is carried out, it enters the **mempool**.
2. Each transaction in the mempool is validated. If it’s not valid, it gets deleted from the mempool.
3. A validator selects a valid transaction with the highest amount.
4. Then the validator selects a **ZK-snarker** **(snark producer)** with the lowest fee for the valid transaction at the **snarketplace**.
5. The selected ZK-snarker makes a **ZK-snark** (**snark-work**) for the selected transaction to prove its validity.
6. When the transaction-ZK-snark pairs reach a particular set value, a new block is ready. Overall, there can be 128 transactions in one block. Once it is ready, the produced block is added to the blockchain.
7. The queue state and the ZK-snark state are updated.
8. The produced block is validated. If it’s invalid, it is withdrawn, and the validator receives no rewards for the block. If a new block is valid, it is further approved in the blockchain.
9. The validator receives a reward for the produced block. If the validator’s **account** is **unlocked**, it gets a **supercharged reward**, which is 2X of a normal reward. A normal reward is 720 Mina tokens, whereas a supercharged reward is 1440 Mina tokens.
10. The validator distributes the reward between its **delegators** according to their share in the validator’s total stake. For staking delegated tokens the validator charges a fee from the delegators.

The diagram in **Figure 1** shows the process of block production in Mina (**Figure 1**).

### Glossary Reference 2

{% hint style="info" %}
**Account** - a personal profile for digital asset management and other operations in the Mina blockchain.

**Delegator** - an account that makes its staking by providing its own funds to a node rather than running its own node.

**Epoch** - a specific period of time used to indicate when certain events will occur in the blockchain network, such as when incentives will be distributed or when a new group of validators will be assigned to validate transactions. The duration of an epoch in the Mina Protocol is 7140 slots per epoch. A new slot is allocated every 3 minutes. With that in mind, an epoch lasts 21420 minutes, that's about 14 days and 21 hours.

**Mempool** - a cryptocurrency node mechanism for storing information about unconfirmed transactions that are awaiting confirmation - a database where new transactions are stored.

**Snarketplace** - a buffer marketplace where nodes: validators and snarkers - exchange services.

**Supercharged reward** - a supercharged reward for block production in the amount of 1440 Mina paid when a certain condition is met, i.e. when the token holder has fully unlocked tokens.

**ZK-snark** (**snark-work**) - a cryptographic method by which one party (a prover) can prove to another party (a verifier) that a given statement is true while the prover avoids conveying any additional information apart from the fact that the statement is indeed true.

**ZK-snarker** **(snark producer)** - a network node that provides ZK-proof (snark-work).

See [Mina glossary](mina-glossary.md).
{% endhint %}

### Figure 1. Block production process in Mina

![](<../../.gitbook/assets/Mina Block Production (1).png>)

## Canonical and Orphaned Blocks <a href="#canonical-and-orphaned-blocks" id="canonical-and-orphaned-blocks"></a>

When added to the blockchain, a new block then becomes a **canonical**, or an **on-chain, block**. However, there can be more than one block producer per **slot** due to the way block producers are selected. So if two or more blocks are produced for the same slot, it will cause a short fork, and only one branch will be chosen - the winner in this instance is random based on the VRF output for each block producer. The Mina protocol uses both blocks until one chain has more verified blocks than the other. When this happens, the blocks in the longer chain will be canonical, and the blocks in the shorter chain are **orphaned**, or **off-chain, blocks**. Technically it means that Mina can have no forks. **Figure 2** shows the canonical chain, which goes back to the Genesis. The green blocks are canonical blocks, the blue blocks are orphaned blocks.

### Glossary Reference 3

{% hint style="info" %}
**Canonical (on-chain) block** - a block included in the primary blockchain and referenced directly or indirectly by future blocks.

**Orphaned (off-chain) block** - a block that has been resolved on the blockchain network but has not been accepted by the network.

**Slot** - a basic unit of time in the blockchain. One epoch contains 7140 slots. 1 slot equals approximately 3 minutes.

See [Mina glossary](mina-glossary.md).
{% endhint %}

### Figure 2. Canonical Chain

![](<../../.gitbook/assets/Canonical Chain (1).png>)
