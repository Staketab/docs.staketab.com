# Account Balance: Locked and Unlocked Tokens

## Account Balance in Mina <a href="#account-balance-in-mina" id="account-balance-in-mina"></a>

An **account balance** consists of three types of funds: free funds, **current locked balance** and **current unlocked balance**. Free funds and currently unlocked funds make up **movable balance**. An account can stake, delegate or send only the funds in the movable balance (see **Figure 1** and **Appendix 1**).

### Glossary Reference 1

{% hint style="info" %}
**Account** - a personal profile for digital asset management and other operations in the Mina blockchain.

**Account balance** - the amount of crypto assets on the account.

**Current locked balance** - the amount of Mina tokens that are currently locked on an account.\
**Current unlocked balance** - the amount of Mina tokens that are now unlocked on an account.

**Delegation** - type of blockchain consensus protocol that allows users to spend their coins or tokens to vote for different delegates.

**Initial supply** - the total amount of Mina tokens in the Mina blockchain at the Genesis.

**Movable balance** - the amount of Mina funds on an account that can be used in transactions or withdrawn.

**Slot** - basic unit of time in the blockchain. One epoch contains 7140 slots. 1 slot equals approximately 3 minutes.

**Staking** - the process of holding tokens locked on the blockchain as a proof of stake to mint new blockchain coins and thus maintain the inflation of the system. The blockchain participants that are engaged in staking, gain reward for it as an incentive.

See [Mina glossary](mina-glossary.md).
{% endhint %}

### Figure 1 - Account Balance

![](<../../.gitbook/assets/Account Balance.png>)

## **Unlock mechanism in Mina protocol** <a href="#unlock-mechanism-in-mina-protocol" id="unlock-mechanism-in-mina-protocol"></a>

There are 2 mechanisms of unlocking funds the Mina protocol: **cliff** and **vesting**. With the cliff mechanism a part of initially locked funds (**cliff amount**) will be unlocked when the **cliff time** comes in. Vesting means that the rest of the initially locked funds will keep unlocking, but gradually, in increments, according to the set **vesting time**, the **vesting increment**. The first **initial locked balance** are unlocked through the cliff mechanism, the rest are unlocked through the vesting mechanism.

### Glossary Reference 2

{% hint style="info" %}
**Initial locked balance** - the amount of Mina tokens that were locked on an account at the Genesis.\
**Cliff amount** - the amount of Mina funds on the account that will be unlocked when the block number corresponding to the cliff time is mined.\
**Cliff time** - number of slots through which cliff\_amount tokens will be unlocked.

**Vesting increment** - the amount of Mina funds that are unlocked whenever the next vesting time interval is over.\
**Vesting time**- number of slots through which vesting\_increment tokens will be unlocked.

See [Mina glossary](mina-glossary.md).
{% endhint %}

Let’s see how the unlock mechanism works in mina on a simple example (**Table 1**).

### Table 1. Example of funds unlock in Mina

\


| **Parameter**           | **Value** |
| ----------------------- | --------- |
| Initial minimum balance | 1000 Mina |
| Cliff amount            | 500 MIna  |
| Cliff time              | Slot 10   |
| Vesting period          | 1         |
| Vesting increment       | 100 Mina  |

From slot 1 to slot 9 all tokens (initial minimum balance) are locked. Then unlocked on slot 10 (cliff amount) 500 Mina. 11, 12, 13, 14 and 15 slots will be unlocked (vesting increment) by 100 tokens\
and on slot 15 all initial minimum balance will be unlocked (see **Figure 2**)**.**

### Figure 2. Unlock mechanisms

![](<../../.gitbook/assets/Unlock Mechanism.png>)

## Genesis and sponsor award <a href="#genesis-and-sponsor-award" id="genesis-and-sponsor-award"></a>

At **Genesis** each member receives 66,000 Mina tokens at launch. They are all locked tokens. These grants open for 4 years, with an initial cut off 1 year after the **Genesis Block**. These grants must be delivered, otherwise they will be cancelled. A total of 4.3% of the initial distribution is allocated to 663 Genesis members selected from numerous Mina **testnets**.

### Glossary Reference 3

{% hint style="info" %}
**Genesis** - the very first block upon which additional blocks in a blockchain are added; the launch of a blockchain.

**Genesis block** - the first block in the blockchain.

**Testnet** - an alternative blockchain to be used for testing.

See [Mina glossary](mina-glossary.md).
{% endhint %}

The Genesis program prepares participants to become the first Mina block producers and ensures high decentralization when the mainnet launches. In addition to node operators, the Genesis program also consists of community developers and creators with a variety of skills and experiences. Their contributions include creating tools and applications, creating documentation, organizing community events, and reporting critical bugs.

The total share of Mina tokens allocated to sponsors is 20.52% of the initial allocation. These tokens unlock within 18 months of launch, with no sponsor unlocking their entire distribution at launch. In addition, all tokens allocated to supporters are fully locked up for 40 days after the community sale, so that supporters' tokens will only receive the first tranche of their unlocked tokens once the community sale token unlock begins.
