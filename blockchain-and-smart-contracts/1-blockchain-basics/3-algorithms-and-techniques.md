A combination of hashing and encryption are used for securing a blockchain.

### Public-key Cryptography

Where public-key cryptograhy(or asymetric cryptography) is needed, Bitcoin and Ethereum blockchains use Elliptic Curve Cryptography and not RSA. ECC encryption is stronger and more efficient than RSA.

### Hashing 

Hashing transforms input data of arbitary length into a unique fixed-length value. A good hash function is one-way. I.e., the original data cannot be derived from the hash.

In Ethereum, hashing functions are used to generate: Account addresses, digital signatures, transaction hash, state hash, etc.

When there is variable number of items to be hashed, e.g., state changes in a block(as a result smart contract execution), A tree-structured hash is used (Merkle tree.)

### Transaction Integrity

Account addresses are generated using public-key cryptography as follows:

* A 256-bit hash is generated. This is the private key.
* Elliptic-curve cryptography is applied to the private key to generate the public key.
* The public key is hashed to generate the address(20 bytes).

The process of digitally signing a transaction:

* The data fields of the transaction are hashed.
* The hash value is encrypted using the private key of the account sending the transaction.
* The encrypted hash value is added to the transaction as one of it's fields.

The process of verifying the digital signature:

* Decrypt the encrypted hash value using the sender's public key.
* Recompute the hash of the transaction.
* Compare the computed hash with the received hash. If the match the signature is valid.

### Blockchain Security

In Ethereum, the block hash is computed using a variant of SHA-3 algorithm called Keccak. The block hash is the hash of all the elements in the block header, and it serves two important purposes:
 
* Verifies the integrity of the block and its transactions.
* Embedding the previous block hash in the current block header and thus linking them. This makes it impossible to tamper with a block without being detected and thus enforces the immutability of the chain.
