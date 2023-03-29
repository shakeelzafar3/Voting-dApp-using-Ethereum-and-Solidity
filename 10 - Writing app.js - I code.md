Let's get introduced with Web3 and TruffleContract and how to use them to communicate with the Ethereum network and deploy smart contracts.
## Object Definition

```js
const App = {
  web3Provider: null,
  contracts: {},
  account: '0xB598E55d95CC046d38C9409225d93fa56aee8292',
  votingInstance: null,
  pollDuration: null,
  pollEndTime: null,

```
This part defines an object App that will contain various properties and functions for the voting application. The properties being initialized are:

- web3Provider: Will hold the Web3 provider instance used to interact with the blockchain.
- vcontracts: Will hold the Truffle contract instances for the Ballot and Voting contracts.
- account: Will hold the account address of the user.
- votingInstance: Will hold an instance of the deployed Voting contract.
- pollDuration: Will hold the duration of the poll in seconds.
- pollEndTime: Will hold the end time of the poll in seconds.


## Initialization
```js
  init: async function() {
    await this.initWeb3();
    await this.initContract();
    return this.bindEvents();
  },
```
This function initializes the application by calling three other functions: `initWeb3()`, `initContract()`, and `bindEvents()`. It uses the `await` keyword to wait for each function to complete before proceeding.

##  Web3 Initialization
```
  initWeb3: async function() {
    if (typeof web3 !== 'undefined') {
      this.web3Provider = web3.currentProvider;
      web3 = new Web3(web3.currentProvider);
    } else {
      this.web3Provider = new Web3.providers.HttpProvider('http://localhost:8545');
      web3 = new Web3(this.web3Provider);
    }
  },

```

The initWeb3 function is responsible for initializing the web3 instance which is used to communicate with the Ethereum network. The function first checks if the web3 instance is already defined in the browser. If web3 is defined, it sets the web3Provider property of the App object to the current provider and sets web3 to a new Web3 instance using the same provider.

If web3 is not defined, it creates a new web3Provider using the HttpProvider and sets web3 to a new Web3 instance using the same provider. The HttpProvider is the URL of a node on the Ethereum network, which is used to send and receive messages.

Overall, this function checks if web3 is already defined and sets up a provider to connect to the Ethereum network if it is not already defined.


## Contract Initialization
```js
  initContract: function() {
    $.getJSON('Voting.json', function(data) {
      const VotingArtifact = data;
      App.contracts.Voting = TruffleContract(VotingArtifact);
      App.contracts.Voting.setProvider(App.web3Provider);

      // Initialize the Ballot contract -- We will discuss this later
      $.getJSON('Ballot.json', function(data) {
        const BallotArtifact = data;
        App.contracts.Ballot = TruffleContract(BallotArtifact);
        App.contracts.Ballot.setProvider(App.web3Provider);

        // Set the account and initialize the contracts
        web3.eth.getCoinbase((err, account) => {
          if (err === null) {
            App.account = account;
            App.contracts.Voting.deployed().then((instance) => {
              App.votingInstance = instance;
              return App.contracts.Ballot.deployed();
            }).then((instance) => {
              App.ballotInstance = instance;
              return App.bindEvents();
            }).catch((err) => {
              console.log(err.message);
            });
          }
        });
      });
    });
  },

```


The initContract function is responsible for initializing the contracts used in the application.

First, it uses the jQuery method getJSON to load the Voting.json file, which contains the contract's ABI (Application Binary Interface). The data parameter in the callback function contains the parsed JSON data. The function then assigns this data to a constant VotingArtifact.

Next, the function uses TruffleContract to create a contract object for VotingArtifact and sets the provider to App.web3Provider.

The same steps are then repeated for the Ballot.json file, with the resulting object being assigned to a constant BallotArtifact.

The function then calls web3.eth.getCoinbase to get the user's account. If successful, it assigns the account to App.account. It then deploys the Voting contract instance and sets App.votingInstance to the deployed instance.

It then deploys the Ballot contract instance and sets App.ballotInstance to the deployed instance. Finally, it calls the bindEvents function to bind events to the UI elements of the application.

If any errors occur during the process, the function logs the error message to the console.


## Binding Events

```js
 bindEvents: function() {
    $('#startPollBtn').click(this.startPoll.bind(this));
    $('#yesBtn').click(() => this.castVote(true));
    $('#noBtn').click(() => this.castVote(false));
  },
```

The bindEvents function binds event handlers to the DOM elements of the user interface. In this case, the function binds the click event to three different buttons on the UI.

The $('#startPollBtn') selector matches the element with id equal to startPollBtn, which is a button that starts the poll. The click event on this button is bound to the startPoll function using the bind method. The bind method sets the this keyword inside the startPoll function to the current this object, which is the App object.

The $('#yesBtn') selector matches the element with id equal to yesBtn, which is a button that registers a "yes" vote. The click event on this button is bound to an arrow function that calls the castVote function with an argument of true. The arrow function preserves the this value inside the App object.

The $('#noBtn') selector matches the element with id equal to noBtn, which is a button that registers a "no" vote. The click event on this button is bound to an arrow function that calls the castVote function with an argument of false. The arrow function preserves the this value inside the App object.

Overall, bindEvents is responsible for setting up the user interface and connecting it to the underlying logic of the application.


## Setting up contact instance

```js
  setup: function() {
    App.contracts.Voting.deployed().then(instance => {
      App.votingInstance = instance;
    });
  },
```

The setup function is a method of the App object that is called when the web page is loaded. It is responsible for initializing the votingInstance property of the App object, which is used to interact with the deployed instance of the Voting contract.

The deployed() function is provided by the truffle-contract library and returns a promise that resolves to the deployed instance of the contract. The then() function is called on the resolved promise and takes a callback function that is passed the instance as an argument. In this case, the callback function sets the votingInstance property of the App object to the instance returned by deployed().

Overall, this function initializes the votingInstance property of the App object with the deployed instance of the Voting contract.


We will move to [next lesson](https://github.com/shakeelzafar3/Voting-dApp-using-Ethereum-and-Solidity/blob/main/11%20-%20Writing%20app.js%20-%20II%20code.md) for the detail of the other functions which are actuall responsibe of our functionalities. 
