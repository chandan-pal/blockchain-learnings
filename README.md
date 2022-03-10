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
- Nonce is usually a 32bit number which can go from 0 to 2^32

---------------------------------------------
# BITCOIN - a blockchain technology implementation
- Bitcoin is a decentralized digital currency based on **blockchain technology**, without a central bank or single administrator, that can be sent from user to user on the peer-to-peer bitcoin network without the need for intermediaries.
- The Bitcoin crypto-currency was invented in 2008 by an unknown person or group of people using the name Satoshi Nakamoto.
- The Bitcoin currency came to use in 2009.

## Bitcoin Protocol
There is a defined protocol for bitcoin to work as a crypto-currency based on blockchain technology. The bitcoin protocol states following points

### Decentralized Network
Bitcoin uses distributed ledger technology. Decentralized P2P network of nodes help to verify transactions in bitcoin.

### Proof of work consensus
Bitcoin uses proof of work consensus mechanism to rresolve conflicts in the distributed blockchain ledger. The node or group of nodes which wants to add a block (containing transactions) to the distributed blockchain ledger of bitcoin, need to solve a mathematical eqaution in oder to provide proof of work.\
This process is known as mining of blocks (in general cryptocurrency mining).

### BTC - Native currency of Bitcoin
- Each unit of currency in bitcoin blockchain is referred to as a bitcoin (BTC)
- The bitcoin miners get rewards in BTC units for successfully adding a block in the ledger.
- The bitcoin network is designed in such a way that only 21 million BTC will ever exist with the last expected to mined(created) around year 2140.
- The rate of BTC generated through cryptocurrency mining is programmed to cut in half every four years (known as the halving).
- The above point makes BTC a deflationary asset unlike many other crypto-currencies.
