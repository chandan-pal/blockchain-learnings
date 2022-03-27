# Solidity
Solidity is an object oriented programing language for implementing smart contracts for ethereum EVM.

- It is high-level
- It is statically typed
- It is case sensitive

## Remix IDE
Remix IDE is a powerful open source tool that helps you write Solidity contracts straight from the browser.\
It is written in JavaScript and supports both usage in the browser, but run locally and in a desktop version.\
Remix IDE has modules for testing, debugging and deploying of smart contracts and much more.

## ABI
Application Binary Interface (ABI) is an interface between two programming modules, often between Operating system and user programs.
- When a smart contract is compiled and deployed, the bytcode is stored on the blockchain, and is associated with an address (of contract account)
- For EVM, a smart contract is just a sequence of bytecode.
- But, to access specific functions defined in the smart contract, users need to translate names and arguments of functions into byte representation of the bytecode to work with it.
- Again, to interpret the response sent by the contract function execution, users need to convert back to the tuple of return values defined in higher-level languages.
- Languages that compile for the EVM maintain strict conventions about these conversions, but in order to perform them, one must know the precise names and types associated with the operations.
- The ABI documents these names and types precisely, easily parseable format, doing translations between human-intended method calls and smart-contract operations discoverable and reliable.


ABI is very similar to API (Application Program Interface), a human-readable representation of a code’s interface. ABI defines the methods and structures used to interact with the binary contract, just like API does but on a lower-level.

### Elements of ABI function
- type: Defines the type of function. It can be one of the following, ‘function’, ‘constructor’, ‘receive' (for receive ether function), or ‘fallback’ (for default function).
- name: Defines the name of the function.
- inputs: It is an array of objects which defines parameters; each object has:
    - name: Defines the name of the parameters.
    - type: Defines the canonical types of the parameters. For example, uint256.
    - components: Used to define tuple types, if a tuple type is reached, it is represented as type = tuple.
- outputs: It is an array of output objects similar to inputs.
- stateMutability: Defines the mutability of a function.
