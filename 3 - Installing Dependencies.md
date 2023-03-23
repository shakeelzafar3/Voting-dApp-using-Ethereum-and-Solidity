Let's have detailed overview of the developement environment and understand what is required to build a decentralized application. 

## List of dependencies
Before we start building our dApp, we need to install some dependencies. A brief list of the depencies is as follows:
1. Node Package Manager (NPM)
2. Truffle Framework
3. Ganache
4. Metamask
5. Solidity compiler
6. Text Editor

Let's cover one by one each of the above mentioned dependency. 
### 1. Node Package Manager (NPM)
One of the dependencies we need is [Node Package Manager (NPM)](https://nodejs.org/en), which comes bundled with Node.js. To check whether Node.js is already installed on your computer, you can open your terminal and type:

```
node -v
```
### 2. Truffle
To build our decentralized voting application, we will need to install the [Truffle](http://truffleframework.com/) Framework. This framework is essential for building decentralized applications on the Ethereum blockchain. It provides a set of tools that allow us to write smart contracts using Solidity programming language, test and deploy them to the blockchain. In addition, it also gives us a development environment to create our client-side application. To install Truffle, open your command line and enter the following command.
```
npm install -g truffle
```

### 3. Ganache
Next, we will need to install [Ganache](http://truffleframework.com/ganache), which is a local in-memory blockchain. You can download Ganache from the Truffle Framework website. Once installed, it will provide us with ten external accounts that have addresses on our local Ethereum blockchain. Each account is preloaded with 100 fake ether, which we can use for testing our smart contracts.
The Ganache after fresh installation looks like this:
![image](https://github.com/shakeelzafar3/images/blob/main/ganache.JPG)
### 4. Metamask 
To use the Ethereum blockchain for our decentralized voting application, we need to connect to it using a special browser extension. The [Metamask extension](https://chrome.google.com/webstore/detail/metamask/nkbihfbeogaeaoehlefnkodbefgpgknn?hl=en) for Google Chrome allows us to connect to the blockchain with our personal account and interact with our smart contract. You will need to install the Google Chrome browser if you don't have it already and then search for the Metamask Chrome plugin in the Google Chrome web store. 
After installation it should appear in your extensions, you can pin the metamask extension which will look like:
![image](https://github.com/shakeelzafar3/images/blob/main/top-nav.JPG)

Once installed, make sure that it is checked in your list of extensions. You'll see the fox icon in the top right-hand side of your Chrome browser when it's installed. 
Please go ahead and check the metamask by clicking the icon, it will appear like this:

![image](https://github.com/shakeelzafar3/images/blob/main/metamask.JPG)

### 5. Solidity
[Solidity](https://docs.soliditylang.org/en/v0.4.21/) is a programming language specifically designed for writing smart contracts on the Ethereum blockchain. Since our decentralized voting application requires a smart contract to manage the voting process and store the voting results, we need to use Solidity to write the code for our smart contract. Solidity provides the necessary functionality and syntax to write secure and reliable smart contracts that can be executed on the Ethereum blockchain. Without Solidity, we wouldn't be able to write the smart contract needed for our voting application.

### 6. Text Editor
We need a text editor for the development of the decentralized voting application because we will be writing code in several programming languages, including Solidity for the smart contract and JavaScript for the web3 application that interacts with the smart contract. A text editor provides a convenient way to create, edit, and organize the code for our application. It also provides features such as syntax highlighting, auto-completion, and error checking, which can help us write code more efficiently and with fewer errors.
 I am going to use [VS Code](https://code.visualstudio.com/) for writing code for both solidity smart contract and javascript application. 
 
 
 Let's start our learning with exploring the basics of the Solidity in the [next lesson](https://github.com/shakeelzafar3/Voting-dApp-using-Ethereum-and-Solidity/blob/main/4%20-%20Solidity%20Basics.md). 
