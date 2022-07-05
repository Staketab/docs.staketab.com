# Mina Accounts

## Mina Accounts <a href="#mina-accounts" id="mina-accounts"></a>

Officially there are no **accounts** in Mina, and all users operate in Mina blockchain through their **addresses** that have a **public key** - i.e. the part of the account address that is seen by the other blockchain community and serves as the part that helps to identify an address in Mina blockchain. An account also has a **private key** - the secret part of the account that is used for authorization purposes. However, we operate with this term - account - for convenience reasons. **Figure 1** shows how accounts and addresses are related in Mina.

### Glossary Reference 1

{% hint style="info" %}
**Account** - a personal profile for digital asset management and other operations in the Mina blockchain.

**Address** - the public address of a private key that serves as an identity of the subject of an account.

**Private key** - extremely large number, a mnemonic entry, used in cryptography as a password - the secret part of an account address.

**Public key** - a cryptographic code that allows users to receive cryptocurrency into their accounts - the open part of an account address.

See [Mina glossary](mina-glossary.md).
{% endhint %}

### Figure 1 - Accounts and Addresses

![](<../../.gitbook/assets/Mina Accounts and Addresses (1).png>)

## How to make a profit in the Mina blockchain <a href="#how-to-make-a-profit-in-the-mina-blockchain" id="how-to-make-a-profit-in-the-mina-blockchain"></a>

Basically, there are 4 ways you can make a profit in the Mina blockchain:

1. **Running a node**. If you run a validator, you can maintain the consistency of Mina blockchain by producing new **blocks**. For this you get a **reward**.
2. **Running a** **staking provider**. If you run a staking provider (validator), you can provide your node to delegators for staking. In return you get a **validator fee**.
3. **ZK-snark works**. If you run a **ZK-snarker**, you can provide **ZK snark proofs** for validators and get a fee for that.
4. **Staking and delegation**. If you don’t run a node, but you’re willing to participate in staking, you can delegate your Mina funds to one of its validators hoping to get your part of the validator’s reward. If run a validator, to whom funds were delegated, you get a validator fee **** for that.

### Reference Gossary 2

{% hint style="info" %}
**Block** - a discrete unit of a blockchain that carries information about transactions, which is recorded in a special cryptographic way.

**Reward** - tokens paid to a block producer for block production to encoure it engage in maintaining the blockchain consistency.

**Validator fee** - a fee for verifying transactions on a blockchain (validation).

**ZK-snarker** - a network node that provides ZK-proof (snark-work).

**ZK snark work** - a cryptographic method by which one party (a prover) can prove to another party (a verifier) that a given statement is true while the prover avoids conveying any additional information apart from the fact that the statement is indeed true.

See [Mina glossary](mina-glossary.md).
{% endhint %}

## Types of Accounts and Addresses <a href="#types-of-accounts-and-addresses" id="types-of-accounts-and-addresses"></a>

Depending on how accounts make a profit and how they operate in Mina, all accounts come into two groups: **nodes** and **non-nodes**. Non-nodes come as delegators, who make profit by delegating funds to validators hoping to get their part of the block production reward, and other accounts that execute transactions in Mina blockchain. Nodes, in their turn, are computers that are connected to Mina blockchain and maintain its operation. Nodes come as ZK-snarkers that do snark-works, **validators** (that are also known as **block producers** and **staking providers** - depending on their role) that are involved in **block production** and **archive nodes**, that keep the blockchain data in an uncompressed (unSNARKed) database, in order to provide easy access to the chain’s history. At the same time, there are validators that actively produce blocks and validators that don’t produce blocks or even have produced no block so far since the Genesis. The validators that produce blocks are **active validators**. This is not an original Mina term, however, we believe it to be important to distinguish the validators that actively produce blocks, since this information may be of importance for our users. **Figure 2** shows how the aforementioned notions correlate.

### Glossary Reference 3

{% hint style="info" %}
**Active validator** - a working node responsible for validating transactions and committing new blocks to the blockchain.

**Archive node** - a node that is designated to store historical data about transactions and blocks.

**Block producer** - a validator that participates in choosing which new blocks are valid to enter a blockchain and therefore participates in block production.

**Block production** - the process of producing blocks, which includes adding transactions to a block and recording them therein in a cryptographic manner, as well as gossipping network participants and adding a new block to the network.

**Node** - a device (such as a computer) that contains a copy of the blockchain's transaction history and maintains a blockchain.

**Non-node** - an address other than a node (a validator or a ZK-snarker) that doesn’t participate in mainaining the blockchain integrity and can execute transactions and hold Mina tokens.

**Staking provider** - a validator to which tokens are delegated by delegators, i.e. a validator that provides staking to accounts that are non-nodes.

**Validator** - a node that maintains the integrity of the blockchain by constantly calculating the link from the first block to the last one and by approving new blocks created by block producers.

See [Mina glossary](mina-glossary.md).
{% endhint %}

### Figure 2 - Mina account

![](<../../.gitbook/assets/Mina Accounts.png>)

A validator as an account can have two addresses: a node address, through which it operates, and a coinbase address, to which rewards are transferred (see **Figure 3**).

### Figure 3 - Validator Account

![](<../../.gitbook/assets/Mina Validator Account.png>)

## How to create an account in the Mina blockchain <a href="#how-to-create-an-account-in-the-mina-blockchain" id="how-to-create-an-account-in-the-mina-blockchain"></a>

\
An account is created via **Mina SDK** or by a node through **CLI**. and activated in Mina by the following flow (see **Figure 4**):

1. A virtual address is created - not in the blockchain - but it is generated either by a node or via CLI.
2. A private key is assigned.
3. An address appears in Mina blockchain once it gets funds - at least 1 Mina.
4. The accrued assets are debited from the account balance.
5. The address gets into the snarked ledger.
6. At the 290th block of the next epoch it gets into the next epoch ledger.
7. At the 1st block of the epoch afterwards the address gets into the **Staking ledger** and the **Staged ledger**.

### Reference Glossary 4

{% hint style="info" %}
**CLI** - Command Line Interface - a text-based user interface that connects a user to a computer program or operating system. Through the CLI, users interact with a system or application by typing in text (commands).

**Mina SDK** - a software development kit used by the Mina blockchain that allows generating keypairs, signing and verifying messages, and signing transactions that can be broadcast to the network.

**Staged ledger** - most recent staged ledger (from the best tip of that node). A staged ledger can be regarded as a "Pending accounts database" that has transactions(payments, coinbase, and proof-fees) applied for which there are no snarks available yet (Epoch x+2).

**Staking ledger** - the Ledger used to determine block producers for a slot, as the probability of winning a slot is proportional to the amount of stake (Epoch x+2).

See [Mina glossary](mina-glossary.md)
{% endhint %}

### Figure 4 - Account Creation

![](<../../.gitbook/assets/Mina Account Creation.png>)

For more information on the ledgers please go to [Account Balance: Locked and Unlocked Tokens](account-balance-locked-and-unlocked-tokens.md).
