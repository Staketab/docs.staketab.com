# Reward Calculation

Mina blockchain offers a reward for **block production** to encourage **nodes** to produce new **blocks** so that the blockchain will be continuously maintained. You can get a **reward** for staking Mina either by running a node and producing blocks or by **delegating** **tokens** to a **validator**. Validators that stake Mina get 100% of the reward they win minus the reward of their **delegators** and the **snark-work fee** (see **Formula 1**).

### Glossary Reference 1

{% hint style="info" %}
**Block** - a discrete unit of a blockchain that carries information about transactions, which is recorded in a special cryptographic way.

**Block production** - the process of producing blocks, which includes adding transactions to a block and recording them therein in a cryptographic manner, as well as gossipping network participants and adding a new block to the network.

**Delegation** - a type of blockchain consensus protocol that allows users to spend their coins or tokens to vote for different delegates.

**Delegator** - an account that makes its staking by providing its own funds to a node rather than running its own node.

**Node** - a device (such as a computer) that contains a copy of the blockchain's transaction history and maintains a blockchain.

**Reward** - tokens paid to a block producer for block production to encourage it to engage in maintaining the blockchain consistency.

**Snarker fee** - a fee for using the network node that provides ZK-proof.

**Validator** - a node that maintains the integrity of the blockchain by constantly calculating the link from the first block to the last one and by approving new blocks created by block producers.

See [Mina glossary](mina-glossary.md).
{% endhint %}

<details>

<summary>Formula1: Validator Reward Calculation</summary>

**BR = CR+TF+SF +(\*SR),**

where **BR** - block reward,

**CR** - coinbase reward,

**TF** - transaction fee,

**SF** - snark-work fee,

**SR** - supercharged reward.

</details>

Winning a reward for block creation is a lottery and the chances depend on the validator’s pool share: the higher the pool share is, the more chances a validator has to win block production. The amount of the reward paid depends on the **coinbase**. For producing a regular block the coinbase is 720 Mina, for a **supercharged block** the coinbase is 2x, i.e. 1440 Mina. This happens only if the accounts that take part in block creation, contain only unlocked tokens.

### Glossary Reference 2

{% hint style="info" %}
**Coinbase** - the amount of coins rewarded.

**Supercharged block** - a block, for which a supercharged reward is paid; a supercharged reward for block production in the amount of 1440 Mina paid when a certain condition is met, i.e. when the token holder has fully unlocked tokens.

See [Mina glossary](mina-glossary.md).
{% endhint %}

Delegators can win a reward in the result of a delegation, and its size depends on their stake (share) in the **validator pool**: the bigger stake a delegator has in the validator pool, the bigger share of the reward it can receive. Delegation is beneficial for both validators and delegators: the first charge a fee for a delegation from delegators, the latter get a chance to participate in staking without having to run a node. The amount of the reward paid to a delegator is calculated as specified by **Formula 2**.

### Glossary Reference 3

{% hint style="info" %}
**Validator pool** - a pool which consists of the stake of elected validators.

See [Mina glossary](mina-glossary.md).
{% endhint %}

<details>

<summary>Formula 2: Delegator Reward Calculation</summary>

**DR = (BR\*S + (SR)) \* (1-PF),**

where **DR** - delegator reward,

**BR** - block reward,

**S** - shares,

**SR** - supercharged reward,

**PF** - pool fees.

</details>
