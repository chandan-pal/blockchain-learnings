# EVM
Ethereum Virtual Machine (EVM) is a computation engine which acts like a decentralized computer that has millions of executable projects.
- The EVM is a quasi-Turing-complete state machine. ("quasi" because all execution processes are limited to a finite number of computational steps by the amount of gas available for any given smart contract execution).
- The EVM has a stack based architecture, storing all in-memory values on a stack.
- It work with a word size of 256 bits (to facilitate native hashing and elliptic curve operation) and has several addressable data component.
- EVM operates in a limited domain as it is just a computational engine and not a complete virtual machine.
- Similar to JVM, it is designed to provide a runtime environment.
- EVM executes its own bytecode instructions set which higher level smart contract programing languages such as LLL, Serpent, Mutan or Solidity are compiled into.
- The EVM has no scheduling capability, because execution ordering is organized externally to it (through blockchain).
- EVM is single threaded like javascript, and EVM neither has any "system interface" handling or "hardware support" - there is no physical machine to interact with.
- The EVM is completely virtual.

## EVM Components
- **Immutable program code ROM** : loaded with the bytecode of the smart contract to be executed.
- **Volatile Memory** : with every location explicitly initialized to zero.
- **Permanent Storage** : part of the etehreum state, also zero initialized.

## EVM instruction set (Bytecode Operations)
The EVM instruction set offers most of the operations like :
- Arithmetic and bitwise logical operations
- Execution context inquiries.
- Stack, memory and storage access.
- Control flow operations
- Logging, calling and other operations

In addition to bytecode operations, EVM also has access to account information (e.g., address and balance) and block information (e.g. block number and current gas price).\
Some opcodes are :

- Stack-manipulating opcodes (POP, PUSH, DUP, SWAP)
- Arithmetic/comparison/bitwise opcodes (ADD, SUB, GT, LT, AND, OR)
- Environmental opcodes (CALLER, CALLVALUE, NUMBER)
- Memory-manipulating opcodes (MLOAD, MSTORE, MSTORE8, MSIZE)
- Storage-manipulating opcodes (SLOAD, SSTORE)
- Program counter related opcodes (JUMP, JUMPI, PC, JUMPDEST)
- Halting opcodes (STOP, RETURN, REVERT, INVALID, SELFDESTRUCT)

## Bytecode
In order to efficiently store opcodes, they are encoded to bytecode.\
Every opcode is alocated a byte (e.g., STOP is 0x00)

## Ethereum State
At the top level, there is **Ethereum World State** which is a mapping of ethereum addresses(160-bit values) to accounts.\
At the lower level, each Ethereum address represents :
     - an account comprising an ether balance (stored as the number of WEI owned by the account).
     - a nonce (representing the number of transactions successfully sent from this account if it is an EOA, or the number of contracts created if it is a smart contract account).
     - the account atorage (permanent data store which is only used by smart contracts)
     - the account's program code (only if the account is a smart contract account)

## EVM transaction execution flow
1. When a transaction result in smart contract code execution , an EVM is instantiated with all the information required in relation to the current block being created and the specific transaction being processed.
2. the EVM's program code ROM is loaded the code of the contract account being called.
3. the program counter is set to zero.
4. the storage is loaded from the contract account storage.
5. the memory is set to all zeros.
6. all the block and environment variables are set.
7. A key variable (gas supply for the execution) is set to the amount of gas paid by the sender at the start of the transaction.
8. As code execution progresses, the gas supply is reduced according to the gas cost of the operations executed.
9. if at any point, the gas supply is reduced to zero, we get an OOG (Out of Gas) exception. Execution immediately halts and the transaction is abandoned.
10. No changes to the ethereum state is applied, except for the sender's nonce being incremented and their ether balance going down to oay the block's beneficiary for the resources used to execute the code to the halting point.
11. It can be considered as EVM running on a sandboxed copy of the Ethereum World State, which is discarded completely if the execution cannot complete.
12. However, if the execution does complete successfully, then the actual ehereum world state is updated accordingly, including any changes to the called contact account storage data, any new contracts created, and any ether balance transfer that were initiated.

A contract can call other contracts, with each call resulting in another EVM being instantiated around the new target of the call.
- Each instantiation has its sandboxed world state inintialized from the sandbox of the EVM at level above.
- Each instantiation is also given a secified amount of supply (not exceeding the amount of gas remaining in the level above)


