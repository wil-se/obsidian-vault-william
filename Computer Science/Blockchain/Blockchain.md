---
alias: []
tags: []
---

# Blockchain
----
A blockchain is a type of [[Distributed Ledger|Distributed Ledger Technology]] that consists of a growing list of records, called blocks, that are securely linked together using cryptography. Each block contains a cryptographic hash of the previous block, a timestamp and transaction data.
The transaction data is generally represented as a Merke tree, where data nodes are represented by leafs.
The timestamp proves that the transaction data existed when the block was created. Since each block contains information about the block previous to it, thei effectively form a chain, with each block linking to the one before of it. Consequently, blockchain transactions are irreversible because the data in a block cannot be altered without altering retroactively all subsequent blocks.
Blockchains are tipically managed by a peer to peer computer network, whick uses a consensus algorithm to add and validate new transaction blocks.

Logically, a blockchain can be seen as consisting of several layers:
- **infrastructure** (hardware)
- **networking** (node discovery, information propagation and verification)
- **consensus** (proof of work, proof of stake)
- **data** (blocks, transactions)
- **applications** (smart contracts/decentralized applications, if applicable)

A blockchain can be considered as a state machine.