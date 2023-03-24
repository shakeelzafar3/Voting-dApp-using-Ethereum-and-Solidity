## Creating a New Migration File
Now that we have established the basic structure of the smart contract, let's proceed with deploying it to the blockchain. To achieve this, we will have to create a new file within the migrations directory. You can create this file from the command line by executing the following command from your project's root directory:
```bash
touch migrations/2_deploy_contracts.js
```
## Assigning Numbers to Migration Files
It is important to note that we assign numbers to all the files inside the migrations directory to ensure that Truffle executes them in the correct order. Now, we can create a new migration to deploy the contract by following these steps:

```solidity
var voting = artifacts.require("./Voting.sol");

module.exports = function(deployer) {
  deployer.deploy(voting, 1000);
};
```

To begin with, we need to import the smart contract we have created and store it in a variable named "Voting" and 1000 is duration for the constructor. Afterward, we include it in the deployed contracts' manifest to guarantee that it is deployed when we execute the migrations.
## Executing the Migrations
Finally, we can run the migrations by entering the following command on the command line:
```bash
truffle migrate
```
## Opening the Truffle Console
Now that we have successfully migrated our smart contract to the local Ethereum blockchain, let's open the console to interact with the smart contract. You can open the truffle console from the command line like this:

```bash
truffle console
```
## Retrieving the Deployed Smart Contract
Now that we're inside the console, let's get an instance of our deployed smart contract and see if we can read the candidate's name from the contract. From the console, run this code:

```bash
Voting.deployed().then(function(instance) { app = instance })
```
Here `Voting` is the name of the variable that we created in the migration file. We retrieved a deployed instance of the contract with the deployed() function, and assigned it to an app variable inside the promise's callback function. 
## Checking if Vote Duration is Allowed
Now we can check that the vote duration is allowed or not like this:
```
app.isActive()
```

Congratulations! You've just written your first smart contract, deployed to the blockchain, and retrieved some of its data.
