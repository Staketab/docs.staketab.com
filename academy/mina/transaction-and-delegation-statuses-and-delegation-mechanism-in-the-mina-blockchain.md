# Transaction and Delegation Statuses and Delegation Mechanism in the Mina Blockchain

## Delegation in the Mina Blockchain <a href="#delegation-in-the-mina-blockchain" id="delegation-in-the-mina-blockchain"></a>

A **delegation** is a **transaction**, when a **delegator**, i.e. an **account** that doesn’t run a **node** and can’t **stake Mina** itself, delegates its **tokens** to a **validator**, i.e. an account that runs a node and can stake Mina, hoping to get its part of the **reward** from the **coinbase** (720 - for a regular block, 1440 - for a **supercharged block**) according to its share in the validator’s **stake** in the event the said validator wins **block production** (for more information please go to [Mina Domain Model](mina-domain-model.md)).

### Glossary Reference 1

{% hint style="info" %}
**Account** - a personal profile for digital asset management and other operations in the Mina blockchain.

**Block production** - the process of producing blocks, which includes adding transactions to a block and recording them therein in a cryptographic manner, as well as gossipping network participants and adding a new block to the network.

**Coinbase** - the amount of coins rewarded.

**Delegation** - a type of blockchain consensus protocol that allows users to spend their coins or tokens to vote for different delegates.

**Delegator** - an account that makes its staking by providing its own funds to a node rather than running its own node.

**Mina** - the cryptocurrency based on the Mina protocol.

**Node** - a device (such as a computer) that contains a copy of the blockchain's transaction history and maintains a blockchain.

**Reward** - tokens paid to a block producer for block production to encourage it to engage in maintaining the blockchain consistency.

**Stake** - the share of staked validator tokens in total staked tokens.

**Staking** - the process of holding tokens locked on the blockchain as a proof of stake to mint new blockchain coins and thus maintain the inflation of the system. The blockchain participants that are engaged in staking, gain reward for it as an incentive.

**Supercharged block** - a supercharged reward for block production in the amount of 1440 Mina paid when a certain condition is met, i.e. when the token holder has fully unlocked tokens.

**Token** - a special crypto asset, a unit of cryptocurrency of a certain blockchain, issued according to the rules of a particular blockchain and can be used as a cryptocurrency.

**Transaction** - a transfer of data from one block to another in a cryptographic manner that launches state transition.

See [Mina glossary](mina-glossary.md).
{% endhint %}

A delegator may delegate or undelegate its tokens. A delegation is not a **transfer** of tokens from one account to another - in fact, a transfer is another type of transaction. With a delegation delegator’s tokens remain on its account, but they are **locked** for the delegation period. A delegator may redelegate its fund to another validator or to the same validator again. After re-delegating, there is a latency period of 2-4 weeks before your new stake delegation comes into effect. A delegator can receive its reward 1 **epoch** (2 weeks) after its validator wins block production and produces its **block** (for more information on reward calculation please go to [Reward Calculation](reward-calculation.md)).

### Glossary Reference 2

{% hint style="info" %}
**Block** - a discrete unit of a blockchain that carries information about transactions, which is recorded in a special cryptographic way.

**Epoch** - a specific period of time used to indicate when certain events will occur in the blockchain network, such as when incentives will be distributed or when a new group of validators will be assigned to validate transactions. The duration of an epoch in the Mina Protocol is 7140 slots per epoch. A new slot is allocated every 3 minutes. With that in mind, an epoch lasts 21420 minutes, that's about 14 days and 21 hours.

**Locked funds** - funds with which transactions cannot be made because the accounts that have these funds are locked.

**Transfer** - a transaction when tokens are sent from one account to another account (payment).

See [Mina glossary](mina-glossary.md).
{% endhint %}

## Transaction Statuses <a href="#transaction-statuses" id="transaction-statuses"></a>

In Mina blockchain transactions come in 3 statuses: **applied**, **pending,** and **failed** (see **Figure 1**):

* <mark style="color:green;background-color:green;">**APPLIED**</mark> is a status when a transaction is successfully processed;
* <mark style="background-color:yellow;"><mark style="color:yellow;">**PENDING**<mark style="color:yellow;"></mark> <mark style="background-color:yellow;"></mark><mark style="background-color:yellow;"></mark> is a status when a transaction is being processed;
* <mark style="color:red;background-color:red;">**FAILED**</mark> is a status when a transaction was not processed for some reason.

### Figure 1. Transaction Statuses State-Machine Diagram

![](<../../.gitbook/assets/Mina Transaction State Machine Diagram.png>)

## Delegation Ledgers <a href="#delegation-ledgers" id="delegation-ledgers"></a>

When a delegation is made (Epoch x), it enters the **snarked ledger**. By the end of Epoch x, the delegation amount can change with the changes in the **account balance**, since it’s always possible to delegate only the full amount of funds on the account balance. On the last block of the epoch when the delegation was made the account balance gets fixed, and this becomes the delegation amount that moves on to the next epoch.

In the next epoch (Epoch x+1) the delegation amount is fixed starting with the first block of Epoch x+1. From now on the delegation amount will not change whatever changes may come with the account balance. At the 290th block of Epoch x+1, the delegation amount enters the next epoch ledger. However, the delegation is not active yet.

In the next epoch (Epoch x+2) starting from the first block of the epoch the delegation becomes active and enters the **staking ledger** and the **staged ledger**. It remains active until the last block of Epoch x+2.

The reward can be paid in Epoch x+3. The reward payment frequency is different from validator to validator. Some validators pay rewards once a week, some - once every two weeks or once a month.

At any point of the delegation lifecycle, the delegator may delegate its funds to another validator or to the same validator again. As a result of another delegation, a new delegation appears. However, if a delegator delegates its funds to the same validator again in Epoch x, this is deemed as the same delegation. A delegation receives the replaced status only if the delegator delegated tokens in the same epoch when the delegation was made. If the delegator delegated funds later, this transaction is deemed as a new delegation with the waiting (amount changeable) status and the previously made delegation has the active status. **Figure 2** shows the lifecycle of a delegation in the Mina blockchain.

### Figure 2. Delegation Lifecycle

![](<../../.gitbook/assets/Delegation Lifecycle.png>)

## Delegation Statuses <a href="#delegation-statuses" id="delegation-statuses"></a>

In the Mina blockchain, there are no **statuses for delegations**. We find it reasonable to introduce delegation statuses since it appears that delegations may come in different states. To do so it’s critical to understand how delegation data are processed within Mina Protocol.

**Figure 3** shows delegation statuses. In the Mina blockchain, there are no statuses of delegations, so we suggest our own statuses:

namely: **waiting (amount changeable)**, **waiting (amount fixed)**, **active**, **replaced**, **ended** (see **Figure 3**):

* <mark style="color:yellow;background-color:yellow;">WAITING</mark> is a status when a new delegation was made until it becomes active. It takes 2 epochs.;
* <mark style="color:green;background-color:green;">ACTIVE</mark> is a status when a new delegation was made and 2 epochs have passed;
* <mark style="background-color:purple;"><mark style="color:purple;">REPLACED<mark style="color:purple;"></mark> is a status when a new delegation was made, and in the same epoch another delegation was made to the same delegator again;
* <mark style="background-color:red;">ENDED</mark> is a status when a new delegation was made and more than 2 epochs have passed or when a delegator undelegated its stake.

### Figure 3. Delegation Statuses State Machine Diagram

![](<../../.gitbook/assets/Mina Delegation State Machine Diagram (1).png>)

Delegation data is entered in 4 ledgers: the snarked ledger, the staking ledger, the **next epoch ledger,** and the staged ledger. A ledger is an electronic book that shows data on the account balance and delegation state. Each ledger extracts data from node databases. A delegation enters the snarked ledger once the delegation is made in Epoch x. On the 290th of Epoch x+1, the delegation enters the next epoch ledger. On the 1st block of Epoch x+2, the delegation enters the staking ledger and the staged ledger. The staged ledger has the same information as the staking ledger, but in the staged ledger the **receipt chain hash** updates every hour (see **Figure 4**).

### Glossary Reference 3

{% hint style="info" %}
**Account balance** - the amount of crypto assets on the account.

**Delegation status** - value showing the state of the delegation.

**Next epoch ledger** - the staking ledger for the next epoch (Epoch x+1).

**Receipt chain hash** - a unique string of characters that is given to every transaction that is verified and added to the blockchain for encryption reasons.

**Snarked ledger** - the ledger containing only transactions that have an associated proof (Epoch x).

**Staking ledger** - the ledger used to determine block producers for a slot, as the probability of winning a slot is proportional to the amount of stake (Epoch x+2).

**Staged ledger** - most recent staged ledger (from the best tip of that node). A staged ledger can be regarded as a "Pending accounts database" that has transactions(payments, coinbase, and proof-fees) applied for which there are no snarks available yet (Epoch x+2).

See [Mina glossary](mina-glossary.md).
{% endhint %}

### Figure 4. Ledgers

![](<../../.gitbook/assets/Mina ledgers.png>)
