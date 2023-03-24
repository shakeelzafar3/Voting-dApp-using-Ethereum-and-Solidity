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

    constructor(uint _duration) {
        owner = msg.sender;
        pollDuration = _duration;
        pollEnd = block.timestamp + pollDuration;
        pollActive = true;
    }

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

    function endPoll() public {
        require(msg.sender == owner, "Only the contract owner can end the poll.");
        require(pollActive, "Poll is already inactive.");
        
        pollActive = false;
    }

    function getResults() public view returns (uint, uint) {
        require(!pollActive, "Poll is still active.");
        
        return (yesVotes, noVotes);
    }

    function isActive() public view returns (bool) {
        return pollActive;
    }

    function timeRemaining() public view returns (uint) {
        require(pollActive, "Voting period has ended.");
        
        return pollEnd - block.timestamp;
    }

}

```
