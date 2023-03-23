Let's get an overview of the basics of the Solidity programming language. 

## Overview
Solidity is a programming language used to write smart contracts on the Ethereum blockchain. Solidity has several features that make it well-suited for writing smart contracts. Some of these features include:
- Strong Typing: Solidity is a statically typed language, which means that data types are explicitly defined and checked at compile time. This helps to reduce errors and increase the security of smart contracts.
- Contract-oriented: Solidity is a contract-oriented language, which means that it is designed to write code that represents contracts, which can be executed on the Ethereum Virtual Machine. Contracts can hold and transfer funds, store data, and interact with other contracts.
- Inheritance: Solidity supports inheritance, which allows contracts to inherit properties and functions from other contracts. This makes it easier to write reusable code and reduces the amount of code duplication.
- Library: Solidity also supports libraries, which are collections of functions that can be reused across multiple contracts. Libraries can be used to reduce code size and increase modularity.
- Events: Solidity allows you to define events, which are triggered when certain actions occur in a contract. Events are useful for debugging and for building user interfaces.
- User-defined types: Solidity allows you to define complex user-defined types, including structs and enums. This makes it easier to write contracts that deal with complex data structures.

## Data types and Variables in Solidity
In Solidity, we can declare variables using the following syntax:

```dataType visibilitySpecifier variableName;```

For example, ```uint public num;``` declares a public unsigned integer variable called ```num```.

Solidity supports various data types such as:

- ```bool```: for true/false values
- ```string```: for single or double-quoted strings
- ```uint```: for unsigned integers
- ```int```: for signed and unsigned integers

## Visibility Specifiers and Readability in Solidity 
In Solidity, visibility specifiers determine where variables and functions can be accessed. The four visibility specifiers in Solidity are:

- ```public```: can be accessed by both internal and external contracts
- ```private```: can only be accessed by internal contracts
- ```external```: can only be accessed by external contracts
- ```internal```: can be accessed by internal contracts and inherited contracts

Comments work the same way as in C++. We can use ```//``` for single-line comments and ```/* */``` for multi-line comments.

## Control Structure
In Solidity, we can use the ```if-else``` statement to perform conditional checks. Here's the basic syntax:

```solidity
if (condition) {
// code block
}
else {
// code block
}
```

## Repetition Statments

We can also use a ```while``` loop to repeat code until a condition is met:

```solidity
while (condition) {
// code block
}
```

Similarly, we can use a ```for``` loop to repeat code for a specific number of times:

```solidity
for (initialization; condition; iteration) {
// code block
}
```

## Functions in Solidity

We can declare functions in Solidity using the ```function``` keyword. Here's the basic syntax:

```solidity
function functionName(parameters) visibilitySpecifier returns (returnType) {
// code block
}
```

## Access Modifiers

Solidity also supports access modifiers, which determine how functions behave and how they interact with the contract's state. Some access modifiers in Solidity include:

- ```constant```
- ```pure```
- ```view```
- ```payable```


Now we are ready to do hands on a hello world smart contract, so, let's jump to the [upcoming lesson](https://github.com/shakeelzafar3/Voting-dApp-using-Ethereum-and-Solidity/blob/main/5%20-%20Hello%20World%20smart%20contract.md). 
