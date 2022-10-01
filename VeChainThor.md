---
alias: []
tags: []
---

# VeChainThor
----
VeChainThor is a public [[Blockchain]] that is designed for **mass adoption** of blockchain technology by **business users** of all sizes. It is intended to serve as the foundation for a sustainable and scalable business blockchain ecosystem.
From a technical point of view, the VeChainThor blockchain is built upon existing proven blockchain innovations and novel technologies that are created for achieving mass adoption. These technologies include the **Proof-of-Authority (“PoA”) consensus algorithm**, **meta transaction** features, protocols of **transaction fee delegation**, on-chain **governance mechanism**, built-in **smart contracts** as well as **tools for developers**.

### Proof of Authority
----
VeChainThor implements the Proof of Authority (PoA) consensus algorithm which states that **there would not be anonymous block producers**, but a **fixed number of known validators (Authority Masternodes) authorized** by the steering committee of the VeChain Foundation.
To be an Authority Masternode (AM), the individual or entity voluntarily discloses who they are (identity and reputation by extension) to the VeChain Foundation in exchange for the right to validate and produce blocks. It is their identities and reputations placed at stake that give all the AMs additional incentives to behave and keep the network secure. In VeChainThor, **each AM has to go through a strict know-your-customer (KYC)** procedure and satisfy the minimum requirements set by the Foundation.

### Meta Transaction Features (Enhanced Transaction Model)
----
The VeChainThor blockchain achieves its TX uniqueness as follows. First, it defines the TX Nonce as a 64-bit unsigned integer that is determined totally by the TX sender. Given a TX, it computes two hashes, the **hash of the [[RLP - Recursive Length Prefix Serialization|RLP]] encoded TX data** without the signature and the **hash of the previously computed hash concatenated by the sender's account address**. The second hash which is 256-bit long, is used as TXID to uniquely identify the given TX. Note that **the calculation of TXID does not require a private** key to sign the TX.

### Multi-Task Transaction (MTT)
----
The VeChainThor blockchain allows a **single transaction to carry out multiple tasks**. To do that, the **Clause structure** is introduced to represent a single task and allow multiple tasks defined in one transaction. A task is defined by fields To, Value and Data. A Clause array, named Clauses, is then introduced in the transaction model to accommodate multiple tasks.

The multi-task mechanism has two interesting characteristics:
• The **execution of tasks in a single TX is atomic**, meaning that either they are all executed successfully or rejected all together.
• **Tasks** in a single TX **are processed one by one in the exact order** they are put in Clauses.
``` Go
type Clause struct {
	body clauseBody
}

type clauseBody struct {
	To    *thor.Address `rlp:"nil"`
	Value *big.Int
	Data  []byte
}
```

### Forcible Transaction Dependency
----
The VeChainThor blockchain provides a safety mechanism that allows users to **force a TX to depend on the success of another TX**. It has been done with the help of field DependsOn in the TX model. If DependsOn has been assigned a valid TXID, the system will check the status of the referred TX. Only if the status says successful, then the current TX will be accepted for processing. A transaction is successful if:
1. the referred TX has been included in the ledger; and
2. it has been executed without being reverted.

### Transaction Lifecycle Control
----
The VeChainThor blockchain gives users control of the lifecycle of the TXs they send. In particular, **users can tell the system when is the earliest time their TXs can be processed and how long a pending TX expires** via fields  BlockRef and Expiration defined in the TX model. 

### TX Fee Delegation
----
The VeChainThor blockchain is the first public blockchain that successfully implemented the TX fee delegation mechanism.
There are currently two protocols running on the VeChainThor blockchain that enable such a mechanism: the _Multi-Party Payment_ (MPP) protocol and the _Designated Gas Payer_ protocol.

#### MPP Multi Party Payment
----
MPP allows an account on the VeChainThor blockchain to pay fees for TXs sent from some designated accounts.

![image](https://ccdn.goodq.top/caches/4e3ec9666d6eaf80311dfe1a66b1b561/aHR0cDovL3d3dy52ZWNoYWluLm9yZy9xZnktY29udGVudC91cGxvYWRzLzIwMTkvMTIvODliZGRmZjNkYjk4NmM1YjMxYWEyM2NiZTEyNWEwNTAtODAud2VicA_p_p100_p_3D_p_p100_p_3D.webp)

• USER: account sending TXs
• PAYER: account receiving TXs from USER and paying the TX fee
• MASTER: account from which the TX fee is actually deducted from. MASTER can be either PAYER itself if it is a normal account or the account deploys PAYER if it is a contract account

#### VIP-191 Designated Gas Payer
----
**VIP-191 allows a TX sender to seek for an arbitrary party**, not necessarily the TX recipient, who is willing to pay for the TX. The protocol works quite simple. It **requires both the TX sender and payer to put their digital signatures in the TX**. The sender also needs to turn on the VIP-191 feature to inform the system that it is a **VIP-191 enabled TX**. Once the TX is accepted and executed, the fee will be deducted from the payer account.

### On-chain Governance Mechanism
----
The VeChainThor blockchain's on-chain governance is about stakeholders or its governing body making **decisions on some critical on-chain actions and executing those actions**. The actions can, for instance, be authorizing or revoking consensus validators (i.e., the Authority Masternodes), changing network parameters, such as the base gas price and block reward ratio, or any on-chain activity embodied by a smart contract deployed on the VeChainThor blockchain.

![image](https://ccdn.goodq.top/caches/4e3ec9666d6eaf80311dfe1a66b1b561/aHR0cDovL3d3dy52ZWNoYWluLm9yZy9xZnktY29udGVudC91cGxvYWRzLzIwMTkvMTIvN2JjMmNiMWEwMmM1NjU3YjkzMDc5YjlkODlhNDIxYzEtODAud2VicA_p_p100_p_3D_p_p100_p_3D.webp)

• **Decision making** is the first phase where decisions on executing certain on-chain actions are made. **Decisions are obtained through voting.** Voting can be conducted either on chain via a voting contract or off chain within the governing body. The former provides maximal transparency and often involves all stakeholders, while the latter complements the former to offer efficiency and agility.

• **Authorization** is the second phase where a voted on-chain action is proposed to the governing body for final approval. **Each proposal has to be approved by a majority of the members of the governing body.** It is an extra security measure put in place to safeguard on-chain governance against malicious activities (e.g., exploitation of voting-contract vulnerabilities).

• **Execution** is the final phase of on-chain governance. Once a proposal has been approved by the required majority, anyone can trigger the execution of the on-chain action defined in the proposal.

![image](https://ccdn.goodq.top/caches/4e3ec9666d6eaf80311dfe1a66b1b561/aHR0cDovL3d3dy52ZWNoYWluLm9yZy9xZnktY29udGVudC91cGxvYWRzLzIwMTkvMTIvMzA0ZDhhNTQ5MjIyYWVlMmU5ZjQwMWM0MTZmYWIwMmMtODAud2VicA_p_p100_p_3D_p_p100_p_3D.webp)

At the center of the framework is **contract Executor** that is deployed both on the mainnet and testnet. Contract Executor provides functions **propose and approve** to carry out the authorization phase. Only authorized voting contracts or members of the governing body can invoke the function propose to submit a proposal in Executor. Once a proposal is logged in Executor, members of the governing body are given a **one-week time to authorize** it.

The _execution_ phase is implemented simply by function execute of contract Executor. Once a proposal has been approved by the required majority (two thirds by default) of members of the governing body, Anyone can invoke function execute to trigger the execution of the on-chain action.

**A voting contract must be authorized** before it can call function propose to submit proposals.  Executor provides functions attachVotingContract and detachVotingContract to manage the list of authorized voting contracts.

#### Built-in Smart Contracts
----
There are **seven built-in smart contracts** deployed on the VeChainThor blockchain. They are called the built-in contracts not only because they are shipped together with the Thor source code, but because **many of their methods are implemented natively in Go** rather than in Solidity for the sake of efficiency. In fact, all functions whose names begin with native are such methods.

##### 1. authority.sol
Contract Authority provides methods to deal with the Authority Masternodes (AMs). Users can use functions get to query the status of a particular AM and use first and next to iterate existing AMs. It also provides functions **add and revoke to authorize and deauthorize an AM**. **These two functions can only be invoked by contract Executor via on-chain governance.** 

##### 2. energy.sol
Contract Energy defines the interface for **operations on VTHO**. 

##### 3. executor.sol
Contract Executor provides methods to facilitate **on-chain governance** on the VeChainThor blockchain.

##### 4. extension.sol
Contract Extension is implemented to allow contract code to **query information of a previous block or be aware of the runtime information of the current TX**. For the former purpose, it provides methods blockID, blockTotalScore, blockTime and blockSigner while for the latter purpose, it provides methods totalSupply, txProvedWork, txID, txBlockRef and txExpiration. It is also invoke the natively implemented Blake2 hash function via method blake2b256.

##### 5. extension-v2.sol
Contract ExtensionV2 is an extension of contract Extension. It defines a new method to **query the actual gas payer of the current TX**. 

##### 6. params.sol
Contract Params provides methods **get and set to check and set the global network parameters.** There are two such  parameters: the **reward ratio** and **base gas price** that are indexed by keys in the system, respectively. The keys are required as the input to the above two functions and are used to locate the parameters in the blockchain state. **Function set can only be invoked by contract Executor via on-chain governance**.

##### 7. prototype.sol
Contract Prototype is implemented to **facilitate MPP** and query information of a particular account. For the former purpose, it provides methods master, setMaster, creditPlan, setCreditPlan, isUser, userCredit, addUser, removeUser, sponsor, unsponsor, isSponsor, selectSponsor and currentSponsor. To query account information, it provides methods balance, energy, hasCode and storageFor.

