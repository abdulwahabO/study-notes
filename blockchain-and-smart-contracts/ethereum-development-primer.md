### Intro: The Ethereum Network and Virtual Machine

The Ethereum Virtual Machine doesn't exist as a single physical entity but rather it is a virtual computer maintained by a network of computers running an Ethereum client(nodes). Every node on the Ethereum network maintains a copy of the current state of the EVM. Any node can broadcast a request for the EVM to perform some computation(transfer ether or execute a smart contract). This requests are known as _transaction requests_. Upon receipt of the request, other nodes in the netwok verify, validate and execute the computation(transaction). This causes an EVM state change, which is committed and propagated to the entire network.

The record of all transactions as well as the state of the EVM is stored on the Ethereum blockchain.

Developers can upload pre-compiled programs called _smart contracts_ to EVM storage. Execution of these _smart contracts_ can then be requested by sending _transaction requests_. Smart contracts are also deployed to the EVM using transaction requests. Once deployed a smart contract cannot be changed.

For every transaction request, the sender must offer a fee to the network. This fee, paid in Ether, is given to the node that verifies and validates that transaction, and adds it to a block which itself is added to the blockchain. The amount paid depends on the number of computational steps in the transaction execution. This prevents malicious participants from intentionally clogging the network with computationally intensive tasks.

All Ethereum accounts(and their balances) and smart contracts live on the EVM. The Ethereum network is an aggregate of the communications between Ethereum nodes.

### Accounts

Accounts are entities that can store Ether. There two types of accounts:

* Externally Owned Account(EOA) - controlled by anyone with the private key.
* Contract Account - controlled by a deployed smart contract.

Both account types can send and receive ether, and send transactions to smart contracts. The differences between external and contract accounts are:

* It cost nothing to create an external account. Creating a contract account comes with fees since storage is going to be needed for the smart contract code.

* Transactions between EOAs can only be Ether transfers. Transactions between EOA and contract accounts can trigger smart contract creation or execution.

* EOAs can initiate transactions, while contract accounts can only send transactions in response to receiving one.

An account has four fields:

* `nonce` - In the case of an externally owned account, this indicates the number of transactions sent from the account. For a contract account, it represents the number of new contracts created by the account.
* `balance` - The amout of Ether available in this account.
* `codeHash` - This is the hash of the smart contract bytecode stored by the EVM for a contract account. The actual code is mapped to the hash and retrieved when a transaction that invokes smart contract execution is received. This field is immutable. For an EOA it is empty.
* `storageRoot` - Also known as `storage hash`. This is the hash of the root node of the Merkle Patricia trie used to encode the contents of the accounts.

**Externally owned accounts** are secured by a public-private key pair. The first step in external account creation is to generate the private key. A 256-bit string that can be encrypted with a password. The public key is generated from the private key using the Elliptic Curve Digital Signature Algorithm. The account address is the last 20 bytes of the public key with '0x' added to the start.

It is possible to generate new public keys from the same private key.  The private key is used to sign transaction requests. Other participants can verify requests by checking the signature against the account address.

**Contract accounts** The address of a contract account is generated from the nonce and address of the account creating the contract.


### Transactions

Transactions are initiated by externally-owned accounts, and they change the state of the EVM. Transaction requests can be broadcast by node. For a transaction to become valid, it has to be verified, validated and executed by other nodes. 

A transaction request fields include the following:

  * `from`: Address of the sender.
  * `to`: Address of the recipient.
  * `gasLimit`: Max amount of gas units the transaction can use.
  * `gasPrice`: The fee to pay per unit of gas.
  * `signature`: Signature of the sender generated using their private key. 
  * `value`: Amount of Ether to transfer.
  * `data`: Optional field for arbitary data.

For smart contract execution, any gas left unused after the execution is complete gets refunded back to the sender account. 

Once a transaction request is broadcast to the network, it is kept in a pool with other unconfirmed transactions. Once it is verified and executed the transaction is added to _block_.

A block is a batch of confirmed transactions which stores the hash of the previous block, thus forming the _blockchain_. Block hashes are derived from the data of transactions. Modifying a transaction would lead to a different hash for that block, and other participants on the network would notice and reject it. This leads to the immutability of the blockchain and prevents fraud.

### Gas

Gas is the unit of computations on the EVM. Gas prices are denoted in _Gwei_(1 Gwei = 10 ^ -9 Ether).
_Gas limit_ is the max number of gas units(computational steps) the sender of a transaction is willing to pay for, and _gas price_ is the amount the sender is willing to spend on each gas unit. 
`Gas fees = gas limit x gas price`

If the gas limit is reached before the transaction has completed, the transaction fails and all changes are reverted. The miner/validator also keeps the gas fee for the work done even though transaction failed. If the transaction uses less gas than was specified, the leftover gas fee is returned to the user. Your transaction is executed faster if the gas price is high, this is because miners/validators will prioritize transactions with higher rewards.

### Nodes and Clients

An Ethereum _node_ is a network participant that can verify blocks and transactions, and carry out other operations needed by the network. An _Ethereum client_ is software that enables a computer to become an Ethereum node. Clients are implemented in a variety of programming languages but they follow a common specification.

Types of nodes:

* `Full node:` Stores the entire blockchain state and performs all network operations.
* `Light node:` Stores a few things, requests others as needed. Performs network operations.
* `Archive node:` Stores the full chain data. DOES NOT perform network operations. Useful for analytics.

Self hosted nodes provide greater security and decentralization, but they are expensive to maintain.Node-as-a-Service providers like Infura or Alchemy allow you setup and connect to nodes via an API.

See [Consensus Mechanisms](https://ethereum.org/en/developers/docs/consensus-mechanisms/)


