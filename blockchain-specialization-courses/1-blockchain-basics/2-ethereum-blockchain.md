
# The Ethereum Blockchain

The Ethereum blockchain introduced _smart contracts_. A _smart contract_ is code deployed on the blockchain whose execution is triggered by a transaction. The Ethereum Virtual machine allows any node on the Ethereum blockchain to execute smart contract code. Smart contracts written in Solidity or other high level language are compiled to EVM bytecode then deployed on the EVM.

Ethereum is a programmable blockchain. Ethereum allows users to create their own operations of any complexity. While Bitcoin blockchain is a list of transactions. _Accounts_ are the basic units of the Ethereum protocol. The Ethereum blockchain tracks the state of every account, and all state transistions are transfer of value from one account to another.

There are two types of Ethereum accounts:

* Externally Owned Accounts(EOAs) - controlled by private keys(by humans).
* Contract Accounts(CA) - controlled by contract code and can only be activated by an EOA.

_Smart contracts_ refer to the code in a Contract Account. They executed when a transaction is sent to that account. Miners verify and execute transactions, group them into a block and attach it to the blockchain. Transaction fees keep miners incentivized to do this work.

A _transaction_ is a message sent from one account to another. It can contain a payload of binary data, and Ether. If the target account contains code(i.e a smart contract), the code is executed and the binary data is passed as input. 

## Ethereum Structure

_Accounts_ are both source and destination of _transactions_. An EOA is required to participate in the Ethereum network. A CA represents a smart contract. Participants nodes in the ETH blockchain can send transactions that:

* Transfer Ether (ETH) or
* Execute a smart contract.

Both types of transactions require fees. An account must have the sufficient balance to pay the fees needed for a transaction to be activated. Fees paid in Wei, a lower denomination of Ether. 1 Ether = 10^18 wei. 

A transaction includes:

* The recipient
* Signature of sender
* Amount of Wei (to transfer)
* Payload for a contract (Optional)
* STARTGAS - Max number of steps the computational steps the transaction is allowed
* GASPRICE - The fee sender is willing to pay for the computations.

A Ethereum block contains:

* Hash of the parent block
* Transactions
* Gas limit.
* etc.

An Ethereum _full node_ hosts the software needed for initiation and validation of transactions, mining, block creation, and the EVM.

Smart contracts are compiled to bytecode format that can run on an EVM. There can be more than one smart contract deployed to an EVM instance. Miner nodes receive, verify, gather and execute transactions. 

Ethereum uses a memory based proof-of-work, not CPU as the Bitcoin blockchain does.

## Incentive Model

Instead of ether, _gas points_ are used to specify the fees for every action in Ethereum. Gas points allow for transaction and computation fees that are independent of the price of Ether. Every transaction in Ethereum, whether simple ether transfer or smart contract execution, requires gas points to be specified. Miners will reject any transactions with an acceptable amount of fees.

Ethereum 2.0 moves the consensus protocol from the _Proof-Of-Work_ to _Proof-of-Stake_. In the new model, they are no miners, only _validators_. 

See [Ethereum | Proof-Of-Stake](https://ethereum.org/en/developers/docs/consensus-mechanisms/pos/)
