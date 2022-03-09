# blockchain-learnings

## Origin
Stuart Haber & W. Scott Stornetta - paper on how to timestamp a digital document

## What is blockchain ?
A blockchain is a growing list of records (called blocks) that are linked together with cryptography.
Each block contains a cryptographyic hash of the previous block, a timestamp and the current blocks data.

- As each block contains the information about the block previous to it, they form a chain, with each additional block reinforcing the ones before it. Therefore blockchains are resistant to modification, because once recorded, the data in any given block cannot be altered retroactively without altering all subsequent blocks.

## Block
- Data
- Perviuos hash
- current hash
- timestamp

### Genesis Block
The first block of a blockchain. It does not have a previous hash.

## Hashing
Hashing is a function to map data of arbitarary size to a fixed size.
Hashing function requirements :
- One way
- deterministic : for a given input value it must always generate the same hash value.
- Fast Computation
- The avalanche effect (must in cryptography)
- Must withstand collisions

### SHA256 cryptography (Hashing algorithm)
- Scecure Hash Algorithm + 256 bits memory it takes
- it is a hexadecimal hash (possible characters are 0-9 and A-F)
- The SHA hash is always 64 characters long (64 * 4 bits for each char = 256 bits )
- The alogorithm works for any type of data like text, imagesm video etc.

## Immutable Ledger
- A ledger is typically a book or collection of accounts in which account transactions are recorded.
- The word Immutable means “cannot be changed.” 

## Distributed P2P (Peer to Peer) network
- P2P is a decentralized network communications model.
- It consist of a group of devices (nodes) that collectively store and share files where each node acts as an individual peer.
- P2P communication is done without any central administration or server. All nodes have equal power and perform same tasks.
- P2P architecture of blockchain removes the need of any middle-man or central server.
- With the P2P network anyone who wishes to participate in the process of verifying and validating blocks can setup a node.

P2P pros :
- As P2P is decentralized, it is highly available due to decentralization.
- P2P networks offer greater security compared to traditional client-server systems

## Byzantine fault tolerance
A fundamental problem in distributed computing and P2P systems is to achieve overall system relaibility in presence of number of faulty processes.  
This often requires processes to agree on some data value that is needed for computing.  
This is called consensus.

- Byzantine Fault Tolerance is the characteristic which defines a system that tolerates the class of failures that belong to the Byzantine Generals’ Problem.

## Consensus Protocol
There are several protocols to achieve consensus in P2P network.
- Proof-of-Work (PoW)\
Proof of Work provides a powerful stamp that says ‘this history cannot be changed without doing a lot of work.
- Proof-of-Stake (PoS)

## Nonce
- Nonce (Number only used once) is a number added to a hashed - or encrypted block in blockchain that, when rehashed, meets the dificulty level restrictions. The nonce is the number the blockchain miners are solving for, in order to receive cryptocurrency.

