# Solidity
Solidity is an object oriented programing language for implementing smart contracts for ethereum EVM.

- It is high-level
- It is statically typed
- It is case sensitive

## Remix IDE
Remix IDE is a powerful open source tool that helps you write Solidity contracts straight from the browser.\
It is written in JavaScript and supports both usage in the browser, but run locally and in a desktop version.\
Remix IDE has modules for testing, debugging and deploying of smart contracts and much more.

## Solidity Compilation Process
Solidity smart contract are compiled to generate two elements.
1. contract ABI : ABI help any other application to communicate with the bytecode of the smart contract. more details below
2. Contract bytecode : bytecode is a sequence of operations

- Contract bytecode is public and stored in the block chain.
- Contract (byte code + ABI) may not be public (if the ABI is not public then it is difficult to generate back the actual contract)
- The ABI is not stored in the blockchain.

## ABI
Application Binary Interface (ABI) is an interface between two programming modules, often between Operating system and user programs.
- When a smart contract is compiled and deployed, the bytcode is stored on the blockchain, and is associated with an address (of contract account)
- For EVM, a smart contract is just a sequence of bytecode.
- But, to access specific functions defined in the smart contract, users need to translate names and arguments of functions into byte representation of the bytecode to work with it.
- Again, to interpret the response sent by the contract function execution, users need to convert back to the tuple of return values defined in higher-level languages.
- Languages that compile for the EVM maintain strict conventions about these conversions, but in order to perform them, one must know the precise names and types associated with the operations.
- When an external application or another smart contract wants to interact with the blockchain, it needs to have some knowledge of a smart contract’s interface such as a way to identify a method and its parameters. This is facilitated by the Ethereum Application Binary Interface (ABI). 
- The ABI documents these names and types precisely, easily parseable format, doing translations between human-intended method calls and smart-contract operations discoverable and reliable.


ABI is very similar to API (Application Program Interface), a human-readable representation of a code’s interface. ABI defines the methods and structures used to interact with the binary contract, just like API does but on a lower-level.\
ABI encoder requires a description of the contract’s interface like function name and parameters which is commonly provided as a JSON.

### Elements of ABI function
- type: Defines the type of function. It can be one of the following, ‘function’, ‘constructor’, ‘receive' (for receive ether function), or ‘fallback’ (for default function).
- name: Defines the name of the function.
- inputs: It is an array of objects which defines parameters; each object has:
    - name: Defines the name of the parameters.
    - type: Defines the canonical types of the parameters. For example, uint256.
    - components: Used to define tuple types, if a tuple type is reached, it is represented as type = tuple.
- outputs: It is an array of output objects similar to inputs.
- stateMutability: Defines the mutability of a function.

## Boilerplate Solidity Code
```solidity
//SPDX-License-Identifier: UNLICENSED"
pragma solidity >=0.5.0 <0.9.0;
contract demo {
    
}
```

## Constructor
used to intialize a smart contract. Gets executed only once when the contract is created. Contructor is called by the compiler. Constructor can have arguments also.
Only one constructor is allowed in a contract and that is optional. If no constructor is explictly defined, then a default constructor will be created by the compiler.
```
//SPDX-License-Identifier: UNLICENSED"
pragma solidity >=0.5.0 <0.9.0;
contract demo {
    uint public count;
    constructor(unit _count) {
        count = _count;
    }
}
```

## Datatypes in contracts
### Integers
- int : supports both signed and unsigned integers. int is an alias of int256.
- uint : supports only unsigned integers.
default value of integers is 0.\
Integers can have various sizes. int8 to int 256, also uint8 to uint256


## State variables, Local variables and Global variables
- State Variables: The variables whose value are permanently stored in a contract storage. For each stage variable being stored/changed, some gas will be used.
- Local Variables: Variables whose values are present till function is executing. Declared inside a function. They do not cost any gas.
- Global Variables: Special variables exists in the global namespace used to get information about the blockchain.

some datatypes like string by default get stored in contract storage. for that we specifically need to specify **'memory'** keyword.
``` string memory str = "test"; ```

## Functions
A function is basically a group of code which can be reused anywhere in the program.\
defined by using the 'function' keyword, followed by name. A function can also have a list of parameters containing the datatype and name of the parameter.
- the name of the function should be unique and should not match with any of the reserved keywords.

### Pure and view keywords in function
'view' keyword is used to indicate that the function will only read a state variable and not modify any state variable.\
'pure' keyword is used to indicate that the function is not reading any state variable as well as not modifying any state variable.\
when modifying a state variable in a function, neither pure nor view keyword should be used.

