Get a brief overview of a simple hello world smart and try to absorb the notations and struture of the contract. 

## Hello World Smart Contract
```solidity
pragma solidity ^0.8.0;

contract HelloWorld {
  string public message;

  constructor(string memory _message) {
    message = _message;
  }

  function setMessage(string memory _message) public {
    message = _message;
  }
}
```

## Explanation
Let's break down what this contract does:

- The first line `pragma solidity ^0.8.0` specifies the version of Solidity that the contract uses. In this case, it is version 0.8.0 or higher.
- The `contract` keyword is used to define a new contract. In this case, we name it `HelloWorld`.
- The contract contains one string variable named `message`. The `public` keyword makes it readable to other contracts and outside of the contract.
- The `constructor` function is executed when the contract is deployed to the blockchain. It takes a string `_message` as input, which is used to set the initial value of the `message` variable.
- The `setMessage` function takes a string `_message` as input and sets the `message` variable to its value. This function is declared `public`, which means that it can be called from outside the contract.
- Since `message` is a public variable, it automatically generates a `message()` function that can be used to read its value.

So, this contract is basically a simple "Hello World" program where you can set a message and read it. When the contract is deployed, it takes an initial message as input and stores it in the `message` variable. You can then change the message using the `setMessage` function and read the current message using the `message()` function.

Let's finish this introductory stuff and jump to create our voting app and work on that in [next lesson](https://github.com/shakeelzafar3/Voting-dApp-using-Ethereum-and-Solidity/blob/main/6%20-%20Creating%20the%20dApp.md).
