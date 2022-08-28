---
description: >-
  This article gives a deeper dive into the delegation process. It can be useful
  for blockchain specialists and developers.
---

# Mina Delegations Explained

{% hint style="info" %}
Before you read this article, you can learn the basics: [**Mina Staking Process**](https://docs.staketab.com/academy/mina/mina-delegations-beginners).
{% endhint %}

## Delegation Statuses <a href="#delegation-statuses-explained" id="delegation-statuses-explained"></a>

In the Mina blockchain, there are no statuses for delegations. We find it reasonable to introduce delegation statuses since it appears that delegations may come in different states. To do so it’s critical to understand how delegations are processed within the Mina Protocol.

<figure><img src="../../.gitbook/assets/SMD Delegation Lifecycle.png" alt=""><figcaption><p><strong>State Machine Diagram - Delegation Statuses (Lifecycle)</strong></p></figcaption></figure>

We suggest the following statuses for a delegation: **Waiting**, **Active**, **Replaced**, **Skipped**, **Ended**:

* &#x20;<mark style="background-color:orange;">WAITING</mark> is a status when a new delegation was made until it becomes active. It takes 2 epochs.
* &#x20;<mark style="background-color:green;">ACTIVE</mark> is a status when a delegation is currently active and produces rewards.
* &#x20;<mark style="background-color:red;">REPLACED</mark> is a status when a delegation was replaced by another delegation to another validator before rewards were produced since in the Mina blockchain there can currently be only one delegation, which fixes the account balance at the end of each epoch.
* &#x20;<mark style="background-color:blue;">SKIPPED</mark> is a status when a new delegation was made to the same validator again before rewards were produced; such a transaction makes no sense, since the account balance will be fixed at the end of the epoch as it is, and the validator remains the same.
* &#x20;<mark style="background-color:purple;">ENDED</mark> is a status when a delegation cycle comes to an end with rewards being produced, which was triggered by changing the validator 2 epochs before.

{% hint style="success" %}
We have illustrated this process in the [**Mina Explorer**](https://mina.staketab.com/). To do this, find your account there, go to **Account Details** and select the "**Staking**" tab.
{% endhint %}

## Ledger Stages <a href="#delegation-ledgers" id="delegation-ledgers"></a>

Delegation data are entered in 4 ledgers: the **snarked ledger**, the **staking ledger**, the **next epoch ledger,** and the **staged ledger**. Each ledger extracts data from node databases.

{% hint style="info" %}
**Staged ledger** - most recent staged ledger (from the best tip of that node). A staged ledger can be regarded as a "Pending accounts database" that has transactions (payments, coinbase, and proof-fees) applied for which there are no snarks available yet.

**Snarked ledger** - the ledger containing only transactions that have an associated proof.

**Next epoch ledger** - the staking ledger for the next epoch.

**Staking ledger** - the ledger used to determine block producers for a slot, as the probability of winning a slot is proportional to the amount of stake.

See [Mina glossary](mina-glossary.md).
{% endhint %}

<figure><img src="../../.gitbook/assets/AD Delegation Lifecycle (1).png" alt=""><figcaption><p><strong>Activity Diagram - Delegation transaction made in epoch X</strong></p></figcaption></figure>

When a delegation is made (**Epoch X**), it enters the <mark style="background-color:purple;"></mark> <mark style="background-color:purple;"></mark><mark style="background-color:purple;">**staged ledger**</mark> <mark style="background-color:purple;"></mark><mark style="background-color:purple;"></mark> . The delegation transaction enters the scan state for snark workers to generate a **snark proof** of the transaction - the amount of time this takes is dependent on the transaction throughput of the network. Once a proof containing the delegation transaction is generated a new <mark style="background-color:purple;"></mark> <mark style="background-color:purple;"></mark><mark style="background-color:purple;">**snarked ledger**</mark> <mark style="background-color:purple;"></mark><mark style="background-color:purple;"></mark> is produced.&#x20;

{% hint style="info" %}
For more details see the [**Scan state**](https://docs.staketab.com/academy/mina/scan-state) **** article
{% endhint %}

By the end of Epoch X, the delegation amount can change with the changes in the account balance. On the last block of the epoch when the delegation was made the account balance gets fixed, and this becomes the delegation amount that moves on to the next epoch.

In the next epoch (**Epoch X+1**) the delegation **amount is fixed** starting with the first block of Epoch X+1. From now on the delegation amount will not change whatever changes may come with the account balance. \
After the 290th block of Epoch X+1 the staking ledger is finalized and named the <mark style="background-color:purple;"></mark> <mark style="background-color:purple;"></mark><mark style="background-color:purple;">**next epoch ledger**</mark> <mark style="background-color:purple;"></mark><mark style="background-color:purple;"></mark> . However, the delegation is not active yet.

<figure><img src="../../.gitbook/assets/Ledgers (1).png" alt=""><figcaption><p><strong>Mina Ledgers</strong></p></figcaption></figure>

In the next epoch (**Epoch X+2**) starting from the first block of the epoch the delegation becomes active the <mark style="background-color:purple;">**staking ledger**</mark> (current epoch staking ledger is the snarked ledger of the last block of an epoch, two epochs prior). Delegation remains active until the last block of Epoch X+2.

{% hint style="warning" %}
The reward can be paid in **Epoch X+2, Epoch X+3 or later**. Mina does not regulate the validator-delegator relationship, so each validator sets its own payout schedule. You can see the **reward payment terms** [**here**](https://mina.staketab.com/mainnet/validators/terms?epoch=35\&isFullyUnlocked=false\&isNotAnonymous=true\&isVerifOnly=false\&isWithFee=true\&orderBy=DESC\&page=0\&searchStr=\&size=100\&sortBy=amount\_staked\&stake=1000\&type=active).
{% endhint %}

{% hint style="info" %}
For more information on the **reward payment** please see **** [**Mina Reward Calculation**](https://docs.staketab.com/academy/mina/mina-reward-calculation).
{% endhint %}
