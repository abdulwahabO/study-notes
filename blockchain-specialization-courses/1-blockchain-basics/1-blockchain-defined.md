## Blockchain Defined

A blockchain is an autonomous decentralized application technology which was originally created to support Bitcoin, a digital currency system. It has since evolved on it's own to support other use cases. 

Bitcoin enabled a peer-to-peer transfer of value without relying on a central authority. This is possible because a blockchain: 

* Enables peer-to-peer transactions in a decentralized network.
* Establishes trust among unknown peers.
* Records transactions in a distributed immutable ledger.

Validation, verification, consensus and immutable recording, lead to the trust and security of a blockchain.

## Bitcoin Blockchain Structure

A block has a header and a list of transactions. The header contains metadata e.g., the hash of the previous block.

Miners are computers that execute operations defined by the blockchain protocol. They are 
responsible for verifying blocks and adding them to the blockchain.

There are two major types of participants in the bitcoin blockchain: 

* Those that initiatiate transfer of value i.e by creating transactions.
* Miners who verify and broadcast transactions, create a block, find consensus by validating the block, broadcast the new block, and confirm transactions.

Miners are incentivized to do this work using bitcoin. Transaction validation is carried out independently by all miners. Invalid transactions are rejected and not broadcast. Valid transactions are added to a pool of _unconfirmed transactions_. Miners select a set of transactions to create a block. To earn the right to add the next block to the chain, miners must solve a puzzle that is CPU intensive(hard to solve, easy to verify). Once a miner solves the puzzle, the block is broadcast to the network, and added to blockchain once other participants verify it and reach a consensus to add it to the chain. The algorithm for reaching consensus is called proof-of-work.

See [UTXO](https://academy.binance.com/en/glossary/unspent-transaction-output-utxo)

The first transaction in every block does not have any input UTXO, and is known as the _coinbase transaction_. This is created by the miner and generates their fee for the transaction. This is how new bitcoin is minted. 

_NOTE: Wallet applications provide the user interface to transfer value through the Bitcoin blockchain_

## Beyond Bitcoin

Bitcoin supports a special(and optional) feature called 'Scripts for conditional transfer of value'. The Ethereum blockchain extended this scripting feature into a code execution framework for 'smart contracts'. Smart contracts allo business logic to be embedded on the blockchain.

Three major types of blockchains exist today:

* Those that support only a crypocurrency. e.g., The Bitcoin Blockchain.
* Those that support cryptocurrency and business logic execution e.g., The Ethereum Blockchain.
* Those that support only business logic execution e.g., Hyperledger.

Anyone one can read or write to a _public blockchain_. A _private blockchain_ is strictly controlled by a single entity, and only approved nodes can participate. A _consortium/permissioned blockchain_ allows approved participants from a larger pool than a private blockchain. This could be a blockchain for a particular industry, government organizations, or any group of different but related entities.
