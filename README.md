# blockchain-learnings

## Origin
Stuart Haber & W. Scott Stornetta - paper on how to timestamp a digital document

## What is blockchain ?
A blockchain is a growing list of records (called blocks) that are linked together with cryptography.
Each block contains a cryptographyic hash of the previous block, a timestamp and the current blocks data.
It can also be considered as a public database that is updated and shared across many computers in a network.

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
Proof-of-stake is done by validators who have staked some asset to participate in the system.\
Instead of needing to do intense computational work, you simply need to have staked your coins in the network.\
A proof-of-stake system is kept secure by the fact that you'd need 51% of the total staked coins to defraud the chain.

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
- New Bitcoins are generated when a block is added in the bitcoin distributed ledger chain.
- The bitcoin miners get the new BTC units generates as rewards for successfully adding a block in the ledger.
- The rate of BTC generated through cryptocurrency mining is programmed to cut in half every four years (known as the halving).
- Hence, The bitcoin network is designed in such a way that only 21 million BTC will ever exist with the last expected to mined(created) around year 2140.
- The above point makes BTC a deflationary asset unlike many other crypto-currencies.

### Bitcoin source code
Bitcoin Core was launched as open source software in 2009. This enables blockchain developers to continuously release new updates that improve protocol functionality.

### UTXO (Unspent Transaction Output)
- Bitcoin uses an Unspent Transaction Output (UTXO) model as a way to keep track of how funds move.
- each UTXO can only be spent once.
- When one user spends a UTXO, one or more new UTXO is created.
- In the UTXO model, one or multiple unspent outputs may be added together to reflect the total amount of funds that belong to one user.

### Bitcooin Mempool
The transactions which are sent on the Bitcoin Network are not added directly to the blockchain. All of the valid transactions have to enter a waiting area before they are accepted in a block. This waiting area is known as the mempool.

### Bitcoin Script and Opcodes
Bitcoin script is a scripting language to give Bitcoin Core instructions on how each UTXO can be spent.

### Bitcoin Private Keys
- The bitcoin protocol makes use of aysymmetric encryption.
- Users can generate private keys (secret key) and corresponding public key.
- Private Keys are meant to be kept secret, and public keys can be shared publically to receive BTC transactions.
- Only user who has access to the matching Bitcoin private key can spend funds (unlock UTXOs)
- The security of Bitcoin private keys is supported by Elliptic Curve Cryptography (ECC) and cryptographic hash functions.
- Users who want to send BTC transactions on the network can use their private key to create digital signatures. 
- A digital signature functions similarly to a one-time passcode for identity authentication. It enables the recipient of a transaction or anyone else on the network to mathematically prove with 100 percent certainty that a specific Bitcoin private key provided the signature.
<img src="private-public-key.png" width="450" height="350" />

### Bitcoin Address
- Bitcoin Addresses are a step further in the security of user with private and public keys.
- While users can receive funds via a **public key**, they can use a **Bitcoin wallet address** (also known as a public address) instead to receive BTC transactions.
- A public address is created from a corresponding public key using two hashing algorithms: the Secure Hash Algorithm 256 (SHA-256) and the RACE Integrity Primitives Evaluation Message Digest 160 (RIPEMD-160).
- Bitcoin wallet address (or public address) adds extra layer of security and freindlier UX by a shorter alphanumeric string.
<img src="bitcoinAddress-gen.png" />

### Bitcoin wallet
- A bitcoin wallet is not something where BTC units are stored.
- Instead, Bitcoin wallets simply act as secure key storage, and a communication tool with the blockchain (distributed ledger).

### Bitcoin HD wallets
- Although the private key is secure and not disclosed to the network, but while spending UTXO the public key has to be in open for verification of the transaction.
- Now since all transactions are on a publically distributed network and if everytime same public key is used for sending and receiving transactions, then it becomes deterministic. The balance and transaction history of a user can be determied from the blockchain for a particular public key.
- So, there is a need to limit the use of public keys to one transaction each, a new pair of private-public keys would need to be created for each transaction.\
**Deterministic Wallets** : In which all keys can be traced back to an original random seed (usually a set of random words). Means, The original seed is enough to recover all private and public keys.\
**Hierarchical Deterministic (HD) Wallets** : Advanced type of deterministic wallet. They contain keys in a tree structure, in which parent keys can produce children keys, which can produce grandchildren keys, and so on, infinitely. The cryptocurrency holder can use the tree structure to organize transactions by type of transaction or by entity involved, such as departments or subsidiaries. HD wallets also offer the option of creating public keys without having to access the corresponding private keys. This means they can be used on insecure servers or in a receive-only mode.
<img src="bitcoin_hdKeys.png" width="450" height="350" />

### Bitcoin Transactions : Pay to Pubkey (P2PK)
When a P2PK transaction is created and submitted to Bitcoin’s peer to peer network, the sender is sending funds from their own Bitcoin wallet to a public key of another user.\
If the recipient wants to spend those funds (spend the corresponding UTXO) at any point in the future, they only need to prove they own the public key to which the funds were sent.\
Its usage faded due to the added benefits provided by using public addresses instead of public keys.

### Bitcoin Transactions : Pay To Pubkey Hash (P2PKH)
P2PKH transactions are sent to the hash of the recipient's public key.\
Compared to a public key, a public key hash is a shorter and more manageable alphanumeric string.\
P2PKH enables error detection through a checksum feature, helping users to drastically reduce the odds of sending BTC to an invalid address.\

### Bitcoin Transactions : Pay To Script Hash (P2SH)
Pay To Script Hash (P2SH) was introduced as a payment type in 2012.\
P2SH transactions typically add constraints in addition to requiring an ordinary digital signature or pubkey verification. \
It is a type of ScriptPubKey which allows for the spending of bitcoin based on the satisfaction of a script (bitcoin script) whose hash is specified within the transaction.\
  For example, if Alice sends Bob 1 BTC in a P2SH transaction, she includes the hash of the script required to spend the bitcoin in the transaction. This script can require signatures by Bob’s private keys and/or many other qualifications. When Bob wants to spend the bitcoin he has received from Alice, he reconstructs the script whose hash Alice used to send the bitcoin, and signs the transaction with any private keys required by the script.
  
  ### Segregated Witness (SegWit)
  - In bitcoin blockchain, there is a size limit to each block (1 MB).
  - This is done to make the creation and synchronization of blocks easier over the P2P network.
  - Earlier a transaction information used to hold infomation like recipient public key, sender's public key, signature, transaction amount. signature being the largest information used to contribute about 60% of the transaction space. Thus, limiting the number of transactions one block can hold.
  - SegWit moves the signature outside of the transaction data. This reduces the size required for transaction storage.
  - It does this by splitting the transaction into two segments, removing the unlocking signature ("witness" data) from the original portion and appending it as a separate structure at the end. Thus, allowing more number of transactions to be fit in a block.
  
-------------------------------------------------------------------------------------
# Ethereum - The world computer
Ethereum is a decentralized, open source and distributed computing platform that enables the creation of smart contracts and decentralized applications (also known as dapps).

- In Ehtereum universe, there is a single, canonical computer (called the ethereum virtual machine, EVM).
- Each node in the Ethereum network keeps a compy of the state of EVM and agrrees on the state of EVM.
- Any node in the network can broadcast a request for execution.
- Whenever such request is broadcast, other nodes in the network verify, validate and execute the computation request.
- The execution causes a state change in the EVM, which is comitted and propogated throught the entire network.
- Requests for computation are called transaction request.
- The record of all transactions and the EVM's present state gets stored on the blockchain, which in turn is stored and agreed upon by all nodes.

## Smart Contracts
- In practice, participants don't write new code every time they want to request a computation on the EVM.
- Rather, application developers upload programs (reusable snippets of code) into EVM state.
- Users make request to execute those code snippets with varying parameters.
- The uploaded programs are called **Smart Contracts**.
- Any developer can create a smart contract and make it public to the network, using blockchain as its data layer, for a fee paid to the network.
- Any user can then call the smart contract to execute its code, again for a fee paid to the network.

Thus, with smart contracts, developers can build and deploy arbitrarily complex user-facing apps and services such as marketplaces, financial instruments, games, etc.

## Decentralized Applications (Dapps)
- A decentralized application (dapp) is an application built on a decentralized network that combines a smart contract and a frontend user interface.
- On Ethereum, smart contracts are accessible and transparent – like open APIs – so your dapp can even include a smart contract that someone else has written.
- A Dapp has its backend code running on a decentralized P2P network.
- A Dapp can have frontend code and user interfaces written in any language to make calls to its backend.
- The frontend can get hosted on a decentralized storage such as IPFS.

Features of Dapps :
- **Decentralized** : Dapps operate on Ehtereum, an open pulic decentralized platform where no one person or group has control.
- **Deterministic** : Dapps perform the same function irrespective of the environment in which they get execuuted.
- **Turing Complete** : Dapps can perform any action given the required resources.
- **Isolated** : Dapps are executed in a virtual environment known as Ethereum virtual machine so that if the smart contract has a bug, it won't hamper the normal functioning of the blockchain network.

Benefits of Dapps :
- **Zero downtime** : The network as a whole will always be able to serve clients looking to interact with the contract.
- **Privacy** : A real world identity is not needed to deploy or interact with the Dapp.
- **Resistance to censorship** : No single entity on the network can block users form submitting transactions, deploying dapps, or reading data from blockchain.
- **Complete Data integrity** : Data stored on the blockchain is immutable and indisputable (because of cryptographic primitives).
- **Trustless computation/verifiable behaviour** : smart contrats can be analyzed and are guaranteed to execute in predictable ways, without the need to trust a central authority.

Drawback of Dapps :
- **Maintenance** : Dapps can be harder to maintain because the code and data published to the blockchain are harder to modify.
- **Performance Overhead** : There is a huge performance overhead, and scaling is really hard. To achieve level of security, integrity, transparency and reliability, every node runs and stores every transaction. On top of this proof-of-work takes time as well.
- **Network Congestion** : When one Dapp uses too many computational resources, the entire network gets backed up.
- **User Experience** : It may be harder to engineer user-friendly experiences because the average end-user might find it too difficult to set up a tool stack necessary to interact with the blockchain in a truly secure fashion.
- **Centralization** : User-friendly and developer-friendly solutions built on top of the base layer of Ethereum might end up looking like centralized services anyways.


## Ethereum Virtual Machine
The smart contracts are executed in a virtual machine (Ethereum Virtual Machine - EVM) and not directly on nodes machine, Which protects the participants from directs threats like access to private files, or execution of malicius software directtly on particiapnts machine.
<img src="EVM.png" />

- It's the environment in which all Ethereum accounts and smart contracts live.
- At any given block in the chain, Ethereum has only one canoical state, and EVM is what defines the rules for computing a new valid state from block to block.
- Ethereum is distributed state machine.
- The EVM executes as a stack machine with a depth of 1024 items. Each item is a 256-bit word, which was chosen for the ease of use with 256-bit cryptography (such as Keccak-256 hashes or secp256k1 signatures).

## Gas
Gas refers to the unit that measures the amount of computational effort required to execute specific operations on ethereum network.\
Since each ehtereum transaction requires computational resources to execute, each transactions requires a fee.\
Gas refers to the fee required to conduct a transaction on Ethereum successfully.\
Gas fees are paid in Ethereum's native currency, ether (ETH).
- Gas prices are denoted in **gwei (giga-wei)** which itself is a denomination of ETH - 1 gwei = 0.000000001 ETH (10-9 ETH).

Gas fees help keep the ethereum network secure. By requiring a fee for every transaction executed on the network, bad actors are prevented from spamming the network.\
In order to avoid accidental or hostile infinite loops or other computational wastage in code, each transaction is required to set a limit to how many computational steps of code execution (gas) it can use.
Any gas not used in transaction is returned to the user.

### Gas Limit
Maximum amount of gas user is willing to consume on a transaction. A standard ETH transfer requires a gas limit of 21000 units of gas.\
More complicated transactions involving smart contracts require more computational work, so they require higher gas limit.

### Block Size
Ethereum earlier had a fixed block size. As a result users often had to wait for their transactions to get included in a block, leading to a poor user experience.\
After London upgrade variable block-size was introduced in Ethereum.
- Now each block has a target block size of 15 million gas.
- Size of block will increase or decrease in accordance with network demand up untill the block limit of 30M gas.
- If the block size is greater than the target block size of 15M, the ethereum protocol will increase the base fee for the following block.
- Similarly, the ethereum protocol will reduce the base fee if the block size is less than target block size.
- The amount by which the base fee is adjusted is proportional to how far the current block size is from the target.

### Base fee
Every block has a base fee which acts as a reserve price. i.e the price of the gas included in a block of target size (15M).\
The base fee is calculated by a formula that compares the size of the previous block (the amount of gas used for all the transactions) with the target size. 
When the block is mined this base fee is "burned", removing it from circulation.
The base fee will increase by a maximum of 12.5% per block if the target block size is exceeded.

### Prioroty Fee (tips)
London upgrage of Ethereum also introduced a priority fee to incentivize miners to include a transaction in the block. Under normal conditions, a small tip provides miners a minimal incentive to include a transaction. For transactions that need to get preferentially executed ahead of other transactions in the same block, a higher tip will be necessary to attempt to outbid competing transactions.

### Max Fee
TO execute a transaction on the network, users can specify a maximum limit they are willing to pay for their transaction to be executed.\
For a transaction, the max fee must exceed the sum of base fee and the tip.\
The transaction sender is refunded the difference between the max fee and the sum of the base fee and tip.

## Decentralized Autonomous Organization (DAO)
DAOs are blockchain-based organizations that operate without central authorities. Its goal is to codify the rules and decisionmaking apparatus of an organization, eliminating the need for documents and people in governing, creating a structure with decentralized control.\
It is a blockchain-based cooperative that is collectively owned by its members, with rules set and executed through code.

- A group of people write the smart contracts (programs) that will run the organization.
- There is an initial funding period in which people add funds to the DAO by purchasing tokens that represent ownership – this is called a crowdsale, or an initial coin offering (ICO) – to give it the resources it needs.
- When the funding period is over, the DAO begins to operate.
- People then can make proposals to the DAO on how to spend the money, and the members who have bought in can vote to approve these proposals.

It’s important to understand that great care has been taken not to make these tokens into equity shares – they are more like contributions that give people voting rights but not ownership. In most cases, a DAO is not owned by anyone – it’s just software running on the ethereum network.

## Soft Fork and Hard Fork
Hard forks and soft forks are essentially the same in the sense that when a cryptocurrency platform's existing code is changed, an old version remains on the network while the new version is created.\
With a soft fork, only one blockchain will remain valid as users adopt the update. Whereas with a hard fork, both the old and new blockchains exist side by side, which means that the software must be updated to work by the new rules.\
Both forks create a split, but a hard fork creates two blockchains and a soft fork is meant to result in one.


