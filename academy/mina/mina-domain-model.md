# Mina Domain Model

**Mina** is a lightweight **blockchain** that operates on **Proof-of-Stake consensus**. What makes this blockchain succinct and lightweight is the zero-knowledge principle of consensus, which allows the consensus to be reached without full knowledge of all history of **transactions**. Mina solves the blockchain trilemma (see **Figure 1** and **Appendix 1**) by separating the functions of **block production** performed by **validators** (**block producers**), **transaction validation** and **verification** performed by **ZK-snarkers** (**snark producers**), and storing the blockchain historical data performed by **archive nodes**. Like any other blockchain, the Mina blockchain consists of **blocks** that are added to the **canonical chain** using an **encryption algorithm** and which contain data about transactions manifesting the change of state (**state machine**).

### **Glossary Reference 1**

{% hint style="info" %}
**Archive node** - a node that is designated to store historical data about transactions and blocks.

**Block** - a discrete unit of a blockchain that carries information about transactions, which is recorded in a special cryptographic way.

**Blockchain** - a digitally distributed decentralized public ledger that exists across a network and represents a sequence of blocks that are linked together in a special cryptographic manner, where each new block is added in the course of consensus work carried out by the chain participants.

**Block production** - the process of producing blocks, which includes adding transactions to a block and recording them therein in a cryptographic manner, as well as gossipping network participants and adding a new block to the network.

**Canonical chain** - the main chain in the Mina blockchain that contains only canonical blocks.

**Consensus** - a process by which individual sections of a network define uniform rules and agree upon adding new blocks to the blockchain.

**Mina** - cryptocurrency based on the Mina protocol.

**Proof-of-Stake (PoS)** - a method of protection in crypto currencies, in which the probability of the formation of the next block in the blockchain by the participant is proportional to the share that the accounting units of this cryptocurrency belong to this participant from their total number.

**State machine** - computer science concept, in which a machine can have multiple states but only one state at a time.

**Transaction** - a transfer of data from one block to another in a cryptographic manner that launches state transition.

**Validation** - an activity of validators aimed at ensuring that a transaction is valid and its states are all correct and true.

**Validator (block producer)** - a node that maintains the integrity of the blockchain by constantly calculating the link from the first block to the last one and by approving new blocks created by block producers.

**ZK-snarker** (**snark producer**) - a network node that provides ZK-proof (snark-work).

See [Mina glossary](mina-glossary.md).
{% endhint %}

<details>

<summary><strong>Appendix 1 - Blockchain Trilemma</strong></summary>

The fact that blockchain as computer technology is novel, it’s exposed to a number of developmental diseases that hinder its adoption. Vitalik Buterin, the co-founder of Ethereum, a blockchain investor, enthusiast and end evangelist, thus formulated the notorious “blockchain trilemma“, the cornerstone issue that needs to be addressed by any blockchain aiming to be a success.

Basically, for a blockchain to be a success, it has to reach a trade-off between three aspects: decentralization, scalability and security (see **Figure 1**) each of which meaning this:

* **Decentralization**: creating a blockchain system that does not rely on a central point of control;
* **Scalability**: the ability of a blockchain system to handle an increasingly growing amount of transactions;
* **Security**: the ability of a blockchain system to operate as expected, defend itself from attacks, bugs, and other unforeseen issues.

1. **Decentralization**

Traditional financial services are centralized by their nature and totally rely on institutions and middlemen like central banks, tax authorities, governments, banks and non-banking financial organizations, world financial organizations, insurance companies, etc. Blockchain, as it was seen by Satoshi Nakamoto, the founder (or the group of founders) of Bitcoin, was designed to handle this peril by providing decentralized services that would be faster, less costly due to lower fees, and more transparent and secure, than conventional financial services.

The trade-off of pure decentralization, however, is speed. Once you put too much weight on decentralization, which makes transactions require multiple confirmations before reaching consensus, then inherently, it would take longer than if a transaction can be confirmed by a single entity.

2\. **Scalability**

This aspect is important for mass adoption, which is usually a big issue for blockchain projects due to the technical complexity of blockchain and the pretty high entrance threshold. When it comes to scalability, it’s the question of how much a blockchain system can sustain, and whether the system can operate smoothly as demand increases. The main goal here is to increase transaction throughput: the more transactions per second that can be processed in a blockchain, the faster and the more scalable it is.

The downside of putting too much emphasis on scalability is excessive centralization, which curbs the originally declared mission of the blockchain technology: to reform financial services in a way that they become more decentralized.

3\. **Security**

As an innovative, promising technology seeking to earn its fame by streamlining the existing infrastructure, the security of a blockchain system is paramount. Due to the transparent nature of the source code and the potentially lucrative benefits one can receive from conducting a successful attack, blockchains have become prime targets for hackers. Therefore, a blockchain must be designed in a way it can ensure transparency and security of transactions.

What seems to be the problem with these three aspects is that it’s next to impossible to combine them all in a single blockchain. All in all, there are 3 extreme cases with the blockchain trilemma:

1.  **A blockchain can be decentralized and secure, but it can’t be scalable.**

    This is exactly what happened with Bitcoin, which boasts its decentralization and consensus algorithm and is highly secure for Byzantine behavior. Using Bitcoin you can be sure of your transaction security, consistency and integrity. However, it takes 10 minutes to agree upon 1 transaction only, whereas Ripple has a throughput of 1,500 TPS and Solana has a throughput of 50,000 TPS.
2. **A blockchain can be decentralized and scalable, but it can’t be secure.**

Ethereum was designed to overcome the Bitcoin scalability issue. Smart contracts helped to do it, however, Etherium is more exposed to security issues. For example: In August 2020, the ETC Blockchain — which is a fork of Ethereum —  suffered three 51% attacks that reorganized more than 4,000 blocks. This allowed the perpetrators to manipulate data and double-spend its ETC currency, resulting in the loss of millions of dollars in value on the network.

3\. **A blockchain can be scalable and secure, but it can’t be decentralized.**

A typical example of this can be a private blockchain that is not intended to allow more participants since it is governed/managed by a single group or organization. The internet swarms with no-name blockchains that exist only for their own sake and purpose. However, they aren’t likely to live up to be a stable platform for decentralized organizations like DAOs or DEFIs.

In reality, most blockchains rarely follow these extreme cases and find their own way of solving the blockchain trilemma. However, the answer is where to find the right balance is a key to designing the architecture and other technical solutions for blockchain projects. The desire to solve the blockchain trilemma gave rise to Layer 1 and Layer 2 blockchains. Though we speak about the blockchain trilemma, the aforementioned issues are not the only ones that blockchain technology has to tackle. There are multiple other issues to be addressed. Certic team insist that we’d rather consider the blockchain pyramid (a hierarchical model) rather than a trilemma when we talk about blockchain. This may help us form a more holistic view of the blockchain phenomenon and come up with more comprehensive solutions.

</details>

### Figure 1 - Blockchain Trilemma

![](<../../.gitbook/assets/Blockchain Trilemma.png>)

The blockchain embraces **nodes**, connected to each other in the **Mina Protocol**, which come as either **validators (block producers) **_****_ or **ZK-snarkers (snark workers)**, and **delegators**. ZK-snarkers are nodes that provide the proof of the validity of the previous transactions for the validators to add them to a new block so that the validators don’t have to find proof of the validity of the previous transactions. It means that making a new block no more requires a great deal of CPU, and the whole distributed ledger may fit in a single I-phone. For producing **ZK-snarks (snark works)** ZK-snarkers take a **fee**. A node can be simultaneously a validator and a ZK-snarker.

### Glossary Reference 2

{% hint style="info" %}
**Delegator** - an account that makes its staking by providing its owns funds to a node rather than running its own node.

**Fee** - a cryptocurrency transaction fee that is charged to users when performing crypto transactions.

**Mina Protocol** - a lightweight Proof-of-Stake blockchain protocol that maintains a constant size of just 22 KB, no matter how many transactions are made on the network, because of using the ZK-proof approach.

**Node** - a device (such as a computer) that contains a copy of the blockchain's transaction history and maintains a blockchain.

**Validator (block producer)** - a node that maintains the integrity of the blockchain by constantly calculating the link from the first block to the last one and by approving new blocks created by block producers.

**ZK-snark (snark work)** - a cryptographic method by which one party (a prover) can prove to another party (a verifier) that a given statement is true while the prover avoids conveying any additional information apart from the fact that the statement is indeed true.

See [Mina glossary](mina-glossary.md).
{% endhint %}

Validators, in their turn, are nodes that create blocks, therefore they’re also called block producers. To do so, they pick out transactions from the **mempool **_****_ which are of the highest **amount** and match them with a ZK-snark from the **snarketplace**, for which the ZK-snarker takes the smallest **fee**. When a certain set of transaction-ZK-snark matches has accumulated, a new block is produced. Later nodes vote for the new block. If they validate it, it is then a **canonical block**, and it is added to the canonical chain, otherwise, this block is deemed **orphaned** and doesn’t enter the chain. The Mina Protocol is designed in a way that no forks are possible and the canonical chain is, in theory, infinite. For producing a block a validator receives a **reward**, which has a **coinbase**. The reward is paid in **tokens **_****_ - Mina. In usual blocks a coinbase is 720 mina, in **supercharged blocks** - 1440 Mina. In case the account of the validator is unlocked, the validator creates a supercharged block, for which it is granted a double reward. The process of getting a reward for block production is called **staking**. Staking is an incentive for blockchain participants to be involved in maintaining blockchain integrity. Staked tokens are locked for an **epoch** plus a period before the validator distributes rewards. This time is specified in the terms, and, combined with an epoch it makes up 1 calendar month. An epoch consists of 7140 **slots** and lasts roughly for roughly 2 weeks (almost 15 days, to be more exact).

### **Glossary Reference 3**

{% hint style="info" %}
**Canonical block** - a block included in the primary block chain and referenced directly or indirectly by future blocks.

**Coinbase** - the amount of coins rewarded.

**Epoch** - specific period of time used to indicate when certain events will occur in the blockchain network, such as when incentives will be distributed or when a new group of validators will be assigned to validate transactions. The duration of an epoch in the Mina Protocol is 7140 slots per epoch. A new slot is allocated every 3 minutes. With that in mind, an epoch lasts 21420 minutes, that's about 14 days and 21 hours.

**Mempool** - a cryptocurrency node mechanism for storing information about unconfirmed transactions that are awaiting confirmation - a database where new transactions are stored.

**Orphaned block** - a block that has been resolved on the blockchain network but has not been accepted by the network.

**Reward** - tokens paid to a block producer for block production to encourage it to engage in maintaining the blockchain consistency.

**Slot** - basic unit of time in the blockchain. One epoch contains 7140 slots. 1 slot equals approximately 3 minutes.

**Snarker fee** - a fee for using the network node that provides ZK-proof.

**Snarketplace** - a buffer marketplace where nodes: validators and snarkers - exchange services.

**Staking** - the process of holding tokens locked on the blockchain as a proof of stake to mint new blockchain coins and thus maintain the inflation of the system. The blockchain participants that are engaged in staking, gain reward for it as an incentive.

**Supercharged block** - a block, which, when produced, gives a supercharged reward (2x to a regular reward) to the block winner, which is given when the block winner has no locked funds on the account.

**Token** - a special crypto asset, a unit of cryptocurrency of a certain blockchain, issued according to the rules of a particular blockchain and can be used as a cryptocurrency.

**Transaction amount** - the amount of Mina funds that is being transacted.

See [Mina glossary](mina-glossary.md).
{% endhint %}

In Mina, there are nodes that produced at least one block in the last epoch and there's nodes that are just connected to the network but are now engaged in block production and **Consensus**. Nodes that produced at least one block in the last epoch are called “**active validators**“. So a node (a validator) does not necessarily need to produce blocks to be part of Mina Blockchain: it’s possible that a user runs a node but is not involved in block production.

A validator also stakes its tokens in the blockchain. The more a validator stakes, the more chances of winning a block it has. Furthermore, a validator may delegate its funds to itself.

Not only validators can stake tokens. If an account wants to stake Mina but doesn’t wish to run a node, it may delegate tokens to a validator. In this case, this account is a delegator. At the end of an epoch, delegators get repaid with part of the total validator’s reward according to their share in the total amount of the tokens staked by the validator. To delegate a validator charges a fee from its delegators. Overall, a delegator receives its share of the reward minus the fee. This is the way both delegators and validators are encouraged to stake tokens with Mina. Not all delegators delegate tokens - some can just have an account but stay passive and choose not to delegate their tokens. Moreover, delegators can delegate tokens themselves. At any time a delegator may choose to undelegate its tokens. A delegator delegates all its balance and can’t delegate only its part. During the delegation period, a delegator may use the delegated tokens in transactions and can withdraw it. The balance changes affect the delegated amount and the repaid reward respectively.

Both nodes and delegators have an **account** through which they stake tokens. An account consists of a **private key** and a **public key**. A public key is the part of the account address that is seen by the other blockchain community. A private key is kept secret. It under no condition must be revealed to the public or third persons for security reasons. A public key is used to prove a validator’s vote for a block. A private key is used to access the **account**.

We develop an **explorer** that accumulates analytical data about nodes, blocks, transactions, rewards, fees, epochs and any other relevant data about the Mina blockchain for stakeholders, be it individual users, holders, traders or validator owners and other experts and stakeholders. We want our explorer to be easy to use and navigate, succinct, compendious and helpful for users.

### **Glossary Reference 4**

{% hint style="info" %}
**Account** - a personal profile for digital asset management and other operations in the Mina blockchain.

**Active validator** - a working node responsible for validating transactions and committing new blocks to the blockchain.

**Explorer** - a piece of software that uses a blockchain node to extract various data from the blockchain, and then uses a database to organize the searched data and present the data to the user in a searchable format.

**Private key** - an extremely large number, a mnemonic entry, used in cryptography as a password - the secret part of an account address.

**Public key** - a cryptographic code that allows users to receive cryptocurrency into their accounts - the open part of an account address.

See [Mina glossary](mina-glossary.md).
{% endhint %}

The diagram in **Figure 2** shows the main entities in Mina Protocol and their associations.

### **Figure 2. Mina Domain Diagram**

![](<../../.gitbook/assets/Mina Domain Diagram.png>)
