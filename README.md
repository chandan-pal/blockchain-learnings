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
