---
date: 2021-05-21T20:29
---

# Cryptocurrency: Network Concepts

## Joining the bitcoin network
- hard coded seed servers in node implementations. Set of randomly selected seeds are queried to get the address of other nodes

## broadcasting transactions
- The gossip protocol is used to broadcast transactions to all its peers.
- each receiving node checks for validity:
  - if valid, pass to its peers.
  - if invalid (or already has it), drop it.
- transaction propagation is usually a slow process: decentralization and efficiency are oft-conflicting forces.

## Storage
- currency size of the bitcoin blockchain (as of Feb 2020) - 270GBs

## Fully validating nodes
- connect to bitcoin network and act as full peers
- downloads and verifies the entrie blockchain (>24 hours to do the bootstrapping)
- verify/propagate/drop transactions received.

## SPV "lightweight" nodes
- doesn't download the transactions
- can ONLY validate transaction that "affect them", not the entire network.
- majority nodes are SPV: wallets are usually SPVs.
- pros: storage/CPU savings + reduced time to spin up a node.

## Forks
- **hard forks**: to introduce new features which were previously invalid. Can lead to chain splits.
- **soft forks**: make validation rules stricter.


## Limitations
- known implementation bugs (MULTISIG instruction popping multiple values off the stack)
- not enough transactions per second (~7 theoretically)
- fixed cryptographic hashing algorithms
- minor issues: divisibility smaller than satoshis
- some constants likely to never be modified: #bitcoins produced, mean time between blocks, block rewards/halvening
- difficult to fix these without hard fork.
