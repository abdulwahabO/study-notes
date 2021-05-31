## Ethereum Smart Contract Basics

Smart contracts are immutable. Once deployed on the blockchain, they cannot change. Only way to implement change is to deploy a new contract and redirect traffic there somehow.

Smart contract store persistent data in _state variables_. An address is needed to deploy a smart contract, and it is gotten by hashing the account number and nonce of the EOA that creates the contract. The address is used by transactions to invoke the smart contract.

A smart contract is compiled to bytecode for execution on the Ethereum Virtual Machine. An ABI(Application Binary Interface) is generated for web apps to interact with the smart contract.

Smart contract creation is sent as a transaction to a unique target account. The payload of the transaction is the bytecode that creates the smart contract. The smart contract code is deployed to all the full nodes on the block chain.

Smart contracts and blockchains are usually part of larger distributed system. Analyze application data and separate them into on-chain and off-chain data. Only use smart contracts for the parts of an application's business logic that require decentralized consensus.

The design of smart contracts should be simple, coherent and auditable.

The blockchain is NOT a data repository. Instead of keeping huge amounts of data on-chain, it's better to keep the data off-chain and store metadata on-chain. E.g., Instead of sending the entire contents of a legal documents in a transaction, the document can be hashed and the hash value kept on chain while the original text is kept elsewhere.

Smart contracts can access info(like number and timestamp) about the block into which the current transaction will be added. 

### Storage, Memory and the Stack

Every smart contract has three areas where it can store data. 

1. **Storage:** A key-value store that maps 256-bit keys to 256-bit values. Costly to read and to modify. 

2. **Memory::** A new instance is created for every message call. A message call occurs when one smart contract calls another, or sends Ether to non-contract account. Memory is a linear data structure. The cost of reading from memory increases as it grows. 

3. **Stack:** Since the EVM is a stack machine. All EVM computations are performed here. 


See [Introduction to Smart Contracts](https://docs.soliditylang.org/en/latest/introduction-to-smart-contracts.html)