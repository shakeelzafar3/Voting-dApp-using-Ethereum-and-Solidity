In this tutorial, we'll be walking through the steps of building a simple voting smart contract in Solidity. This contract will allow users to vote on a simple yes/no question and display the results of the vote. Let's get started!

## Step 1: Setting up the Contract
The first thing we need to do is set up our contract. We'll start by defining our contract and setting up some basic variables:
```solidity
pragma solidity ^0.8.0;

contract Voting {
    address public owner;
    uint public pollDuration;
    uint public pollEnd;
    bool public pollActive;
    uint public yesVotes;
    uint public noVotes;
    mapping(address => bool) public hasVoted;
}
```
In this code, we've defined our contract, called "Voting". We've also set up some basic variables that we'll be using throughout the contract. These include the contract owner's address, the duration of the poll, the end time of the poll, whether the poll is currently active, and the number of "yes" and "no" votes.

We've also set up a mapping that will allow us to keep track of which addresses have voted.

## Step 2: Setting up the Constructor

Next, we'll set up the constructor for our contract. The constructor is a special function that gets called when the contract is first created. In our constructor, we'll set some initial values for our variables:

```solidity
constructor(uint _duration) {
    owner = msg.sender;
    pollDuration = _duration;
    pollEnd = block.timestamp + pollDuration;
    pollActive = true;
}
```

In this code, we're setting the contract owner's address to the address of the person who created the contract (i.e. the "msg.sender"). We're also setting the poll duration to the value that's passed in as an argument to the constructor, and calculating the end time of the poll by adding the poll duration to the current block timestamp.

Finally, we're setting the pollActive variable to "true", since the poll is active when it's first created.

## Step 3: Adding the Vote Function

Now we'll add the function that allows users to vote. This function will take a single argument, a boolean value indicating whether the user is voting "yes" or "no":
```solidity
function vote(bool _vote) public {
    require(pollActive, "Voting period has ended.");
    require(!hasVoted[msg.sender], "You have already voted.");
    
    if(_vote) {
        yesVotes++;
    } else {
        noVotes++;
    }
    
    hasVoted[msg.sender] = true;
}
```
In this code, we're first checking to make sure that the poll is still active and that the user hasn't already voted. If both of those conditions are met, we'll increment either the "yesVotes" or "noVotes" variable, depending on the user's vote.

Finally, we'll set the "hasVoted" mapping for the user's address to "true", to indicate that they've already voted.

## Step 4: Adding the End Poll Function

Next, we'll add a function that allows the contract owner to end the poll:

```solidity
function endPoll() public {
    require(msg.sender == owner, "Only the contract owner can end the poll.");
    require(pollActive, "Poll is already inactive.");
    
    pollActive = false;
}
```

In this code, we're first checking to make sure that the person calling the function is the contract owner. We're also checking to make sure that the poll is still active. If both of those conditions are met, we'll set the 
