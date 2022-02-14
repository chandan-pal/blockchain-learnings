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

