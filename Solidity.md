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
- When an external application or another smart contract wants to interact with the blockchain, it needs to have some knowledge of a smart contract???s interface such as a way to identify a method and its parameters. This is facilitated by the Ethereum Application Binary Interface (ABI). 
- The ABI documents these names and types precisely, easily parseable format, doing translations between human-intended method calls and smart-contract operations discoverable and reliable.


ABI is very similar to API (Application Program Interface), a human-readable representation of a code???s interface. ABI defines the methods and structures used to interact with the binary contract, just like API does but on a lower-level.\
ABI encoder requires a description of the contract???s interface like function name and parameters which is commonly provided as a JSON.

### Elements of ABI function
- type: Defines the type of function. It can be one of the following, ???function???, ???constructor???, ???receive' (for receive ether function), or ???fallback??? (for default function).
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
```solidity
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

### Array
fixed size array and dynamic sized array.
```solidity
//SPDX-License-Identifier: UNLICENSED"
pragma solidity >=0.5.0 <0.9.0;
contract demo {
    uint[3] public arr = [10, 20, 30];
    
    function insert(uint index, uint element) public {
        arr[index] = element;
    }
    
    function len() public view returns(uint) {
        return arr.length;
    }
}
```

```solidity
//SPDX-License-Identifier: UNLICENSED"
pragma solidity >=0.5.0 <0.9.0;
contract demo {
    uint[] public arr;
    
    function pushElement(uint element) public {
        arr.push(element);
    }
    
    function popElement() public view returns(uint) {
        return arr.pop();
    }
    
    function len() public view returns(uint) {
        return arr.length;
    }
}
```
### Struct

```solidity
//SPDX-License-Identifier: UNLICENSED"
pragma solidity >=0.5.0 <0.9.0;
struct student {
    uint roll;
    string name;
}
contract demo {
    student public s1;
    
    constructor(uint _roll, string memory _name) {
        s1.roll = _roll;
        s1.name = _name;
    }
    
    function change(uint _roll, string memory _name) public {
        student memory new_student = student({
            roll: _roll,
            name: _name
        });
        s1 = new_student;
    }
}
```

### Enum

```solidity
//SPDX-License-Identifier: UNLICENSED"
pragma solidity >=0.5.0 <0.9.0;
contract demo {
    enum user {allowed, not_allowed, wait}
    user public u1 = user.not_allowed;
    
}
```

### Mappings (key - value)
```solidity
//SPDX-License-Identifier: UNLICENSED"
pragma solidity >=0.5.0 <0.9.0;
contract demo {
    mapping(uint=>string) public student;
    function input(uint _roll, string memory _name) public {
        student[_roll] = _name;
    }
    
}
```

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

### Assert, Require and Revert function
These functions are part of error handling aspect in solidity.
- **assert()** function when false, uses up all the remaining gas and reverts all the changes made.
- **require()** function when false, also reverts back all the changes made to the contract but does refund all the remaining gas fees we offered to pay.
- In general assert is used to check for internal errors, whereas require analyzes conditions.
- **revert()** function is used to conditionally undo all state changes.

## Inheritance
Inheritance in solidity is the procedure in which one contract inherits the  attributes and methods of another contract.

```solidity
//SPDX-License-Identifier: UNLICENSED"
pragma solidity >=0.5.0 <0.9.0;
contract Parent {
    string public str;
    
}
contract Child is Parennt {
    
}
```

## Abstract Contracts
Abstract contracts are contracts that have at least one function without implementation. The abstract contract defines the structure of the contract and any derived non-abstract contract inherited from it should provide an implementation for the incomplete functions.
- functions without implementation must contation **'virtual'** keyword.

```solidity
//SPDX-License-Identifier: UNLICENSED"
pragma solidity >=0.5.0 <0.9.0;
abstract contract Parent {
    string public str;
    function setter(string memory _str) public virtual;
}
contract Child is Parennt {
    function setter(string memory _str) public override {
        str = _str;
    }
}
```

## Interface
An interface is an agreement or a contract between itself and any cotract that implements it.
- Interface can only inherit from other interfaces and not other contracts.
- They cannot declare state variables
- They cannot declare constructor
- functions can be declared but not implemented. All declared functions must be external.

```solidity
//SPDX-License-Identifier: UNLICENSED"
pragma solidity >=0.5.0 <0.9.0;
interface contract Parent {
    
}
contract Child is Parennt {
    function setter(string memory _str) public override {
        str = _str;
    }
}
```

## Polymorphism
Solidity supports two types of polymorphisms
- Function Polymorphism: method overloading. multiple functions are declared having the same name within the same contract or inheriting contract.
- Contract Polymorphism: means using multiple contract instances interchangeably when they are related to each other by using inheritance.


## Visibility specifier
|| PUBLIC | PRIVATE | INTERNAL | EXTERNAL |
| ---- | ---- | ---- | ---- | ---- |
| Outside world | :heavy_check_mark: | | | :heavy_check_mark: |
| Within Contract | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | |
| Derived Contract | :heavy_check_mark: | | :heavy_check_mark: | :heavy_check_mark: |
| Other Contracts | :heavy_check_mark: | | | :heavy_check_mark: |

## function Modifier
A function modifier is a compile-time source code roll-up. It can be used to amend the semantics of functions in a declarative way.\
A modifier aims to change the behaviour of the function to which it is attached. for e.g. automatically checking a condition prior to executing a function.
- modifier can also be written with arguments.

```solidity
modifier MyModifier {
    // modifier code
}

modifier modifierWithArgs(uint a) {
    // modifier code
}
modifier onlyOwner {
    require(msg.sender == owner, "Only owner can execute the function");
    _; // resume with function execution
}

// 
function isAuthorised(address _user) public view onlyOwner returns(bool) {
    return true; 
}
```
### _; sympbol
The symbol _; is called a merge wildcard. It merges the function code with the modifier code where the _; is placed.\
The place where you write the _; symbol will decide if the function has to be executed before, in between or after the modifier code.

## Events in solidity
An event is an inheritable member of the contract, which stores the arguments passed in the transaction logs when emitted.\
Events notify the applications about the change made to the contracts and applications which can be used to execute the dependent logic.

```solidity
//SP*DX-License-Identifier: UNLICENSED"
pragma solidity >=0.5.0 <0.9.0;
contract demo {
    uint public str;
    event register(address manager, string char);
    
    function setter(string memory _str) public {
        str = _str;
        emit register(msg.sender, str);
    }
}
```

## Payable in solidity
Any function in Solidity with the modifier Payable ensures that the function can send and receive Ether.\
It can process transactions with non-zero Ether values and rejects any transactions with a zero Ether value.\
- Use the keyword payable in a function or state variable to send and receive Ether.
- Include the payable keyword in the state variable in order to withdraw from the contract
- Include the payable keyword in the constructor to be able to deposit into the contract when the contract is created/deployed
- Include the payable keyword in a function to allow deposits into the contract

- if we want to send ether to an address, the address must be payable.
- an address can be declared as payable by using keyword payable.

```solidity
//SPDX-License-Identifier: UNLICENSED"
pragma solidity >=0.5.0 <0.9.0;
contract demo {
    address payable user = payable(0x23234234293c42347877a87926557283453534534a3c)
    uint amount =0;
    function payMeMoney() public payable {  // Having this function set to payable will allow another contract to call it and send it Ether.
        amount += msg.value;
    }
    
    function check_balance() public view returns (uint) {
        return address(this).balance;
    }
    
    function payEtherToAccount() public {
        user.transfer(10 ether);
    }
}
```
### Falback function
external function with neither name, parameters, or return values. It is executed in one of following cases-
1. If a function identifier does not match any of the available functions in the smart contract.
2. if there was no data supplied along with the function call.
- there can be only one fallback function in a smart contract.
- it is compulsory to mark it external
- It should be marked payable. If not, the contract will throw an exception if it receives ether without any data.
- It is limited to 2300 gas if invoked by other functions.

```solidity
//SPDX-License-Identifier: UNLICENSED"
pragma solidity >=0.5.0 <0.9.0;
contract A {
    uint n;
    function set(uint value) external {
        n = value
    }
    
    //fallback function
    function() external payable {
        n = 0;
    }
}

contract demo {
    function callA(A a) public returns(bool) {
        //calling non-existing function
        (bool success,) = address(a).call(abi.encodeWithSignature("setter()"));
        require(success);
        
        // sending ether to A
        address payable payableA = address(uint160(address(a)));
        return (payableA.send(2 ether));
    }
}
```

## ECR20 token
Tokens are a type of cryptocurrency that represents an asset or specific use and resides on their blockchain (the blockchain from which the token was issued).\
ECR stands for **Ethereum Request for Comments**. An ERC is a form of proposal and its purpose is to define standards and practices.\
- ECR20 is a proposal that intends to standardize how a token contract should be defined, how we interact with such a token contract and how these contracts interact with each other.

## ICO (Initial Coin Offering)
An ICO is the cryptocurrency equivalant to an IPO (Initial Public Offering).\
A Web3 company seeking to raise money to create a new coin, app, or service can launch an ICO as a way to raise funds.\
Interested investors can buy into ICO to receive new crytocurrency token issued by the company. This token may have some utility related to product or service that the company is offering, or it may just represent a stake in the company or project.


## Factory pattern
A factory contract is a smart contract that pproduces other smart contracts. A factory contract is useful in cases like -
1. If you want to create multiple instances of the same contract and you're looking for a way to keep track of them and make their management easier.
2. Save gas on deplyment. You can deploy only the factory and use it later to deploy the other contracts.
3. Improve contract security.

```solidity
// factory contract
contract A {
    address bAddress;
    constructor(address b){
       bAddress = b;
    }
 
    function callHello() external view returns(string memory){
       B b = B(bAddress); // explicit conversion from address to contract type
       return b.sayHello();
    }
}
contract B {
     string greeting = "hello world";
     function sayHello() external view returns(string memory){
         return greeting;
     }
}
```

## Withdrawal Pattern
Withdrawal pattern ensures that direct transfer call is not made which poses a security threat.
problem:
```solidity
//SPDX-License-Identifier: UNLICENSED"
pragma solidity >=0.5.0 <0.9.0;
contract FindRichest {
    address payable richest;
    uint max;
    
    constructor() payable {
        richest = payable(msg.sender); // set the owner of the contract as richest initially
        max = msg.value; // set inital max value
        richest.transfer(msg.value); // transfer back the ether of the owner
    }
    
    function sendEther() payable public {
        require(msg.value>max, "You are not the richest");
        richest = payable(msg.sender);
        max = msg.value;
        richest.transfer(msg.value); // problem lies here when another contract is the caller.
    }
}

contract demo {
    function A() public {
        FindRichest.sendEther(); // assuming demo contract is calling the sendEther function.
    }
    
    fallback() payable external {
        revert(); // simulating failure
    }
}
```
In the above example, if demo contract calls the send ether function of FindRichest and the execution reaches the ```richest.transfer(msg.value)``` line then the fallback function of the demo contract will be called since 'richest' is the demo contract. If the fallback function fails then it will revert all the state changes of the FindRichest contract also.\
To solve this problem we can use **withdrawal pattern**.

```solidity
//SPDX-License-Identifier: UNLICENSED"
pragma solidity >=0.5.0 <0.9.0;
contract FindRichest {
    address payable richest;
    uint max;
    
    // store all pending withdrawals
    mapping (address => uint) pendingWithdrawals;
    
    constructor() payable {
        richest = payable(msg.sender); // set the owner of the contract as richest initially
        max = msg.value; // set inital max value
        richest.transfer(msg.value); // transfer back the ether of the owner
    }
    
    function sendEther() payable public {
        require(msg.value>max, "You are not the richest");
        richest = payable(msg.sender);
        max = msg.value;
        // richest.transfer(msg.value); // no direct transfer
        pendingWithdrawals[richest] += msg.value; // store the transfer mapping
    }
    
    // indirect withdrawal - in this case only the calling contract will fail, but this contract will not fail.
    function withdraw() public {
      uint amount = pendingWithdrawals[msg.sender];
      pendingWithdrawals[msg.sender] = 0;
      msg.sender.transfer(amount);
   }
}
```



## Mapping Iterator
The mapping type provides the ability to store and retrieve values for a particular key. However, it does not provide the ability to return an iterable list of keys.\

To solve this solidity suggests to keep track of all keys of the mapping in a separate dynamic array.
```solidity
//SPDX-License-Identifier: UNLICENSED"
pragma solidity >=0.5.0 <0.9.0;
contract demo {
    mapping(address=>uint) public values;
    address[] public arr;
    
    function pay(uint _value) public {
        values[msg.sender] = _value;
        arr.push(msg.sender);
    }
    
    function returnArray() public view returns(address[] memory) {
        return arr;
    }
}
```

## Re-entrancy Attack
A reentrancy attack occurs when a function makes an external call to another untrusted contract. Then the untrusted contract makes a recursive call back to the original function in an attempt to drain funds.\
When the contract fails to update its state before sending funds, the attacker can continuously call the withdraw function to drain the contract???s funds.
```solidity
contract A {
    function requestEther() {
        address.transfer(balance[address]);
        balance[address] = 0;
    }
}

contract B {
    fallback extrnal payable {
        requestEther();
    }
}
```
In the above dummy example, the malicious contract B can drain out all the balance of contract A by calling requestEther recursively.\
to fix this, the state changes are to be done first before any fund transfer.
```solidity
contract A {
    function requestEther() {
        uint temp = balance[address];
        balance[address] = 0;
        address.transfer(temp);
    }
}
```
