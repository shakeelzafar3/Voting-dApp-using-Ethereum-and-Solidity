## Starting the Poll
```js
 startPoll: function() {
    this.pollDuration = $('#pollDuration').val();
    const startTime = Math.floor(Date.now() / 1000);
    this.pollEndTime = startTime + parseInt(this.pollDuration);

    // Disable poll duration input and start button
    $('#pollDuration').attr('disabled', 'disabled');
    $('#startPollBtn').attr('disabled', 'disabled');

    // Enable voting buttons
    $('#yesBtn').removeAttr('disabled');
    $('#noBtn').removeAttr('disabled');

    // Display time remaining
    this.updateTimeRemaining();
    setInterval(this.updateTimeRemaining.bind(this), 1000);
  },
```

This code defines a function startPoll() which is triggered when the "Start Poll" button is clicked on the web page. The function performs the following actions:

- It reads the value of the `pollDuration` input field from the web page and stores it in the `pollDuration` variable.
- It gets the current time using `Math.floor(Date.now() / 1000)` and calculates the end time of the poll by adding the pollDuration to the current time.
- It disables the `pollDuratio` input field and the "Start Poll" button to prevent further changes during the poll.
- It enables the "Yes" and "No" voting buttons to allow users to cast their votes.
- It calls the `updateTimeRemaining()` function to display the time remaining for the poll and sets up an interval to update the time every second.
In summary, this function sets up the poll by starting the poll timer, enabling the voting buttons, and updating the time remaining for the poll on the web page.


## Cast the Vote 
```js
  castVote: function(vote) {
    this.votingInstance.vote(vote, { from: this.account }).then(() => {
      this.markVoted();
    }).catch((err) => {
      console.log(err.message);
    });
  },
```

This code defines a function called castVote that is used to cast a vote in the current poll. The function takes a boolean parameter called vote that represents the choice being made (true for "yes", false for "no").

Inside the function, the `vote()` function of the votingInstance object is called with the vote parameter and the from parameter set to the current account (this.account). The `vote()` function is defined in the Voting contract and updates the vote count for the given choice.

If the vote is successfully cast, the `markVoted()` function is called, which disables the voting buttons for the current account to prevent multiple votes from the same account.

If an error occurs during the vote casting process, the error message is printed to the console.


## Update the Remaining time

```js
markVoted: function() {
    $('#voteStatus').text('Your vote has been cast. Thank you for voting!');
    $('#yesBtn').attr('disabled', 'disabled');
    $('#noBtn').attr('disabled', 'disabled');
  },

  updateTimeRemaining: function() {
    const now = Math.floor(Date.now() / 1000);
    const timeLeft = this.pollEndTime - now;
    if (timeLeft > 0) {
      $('#timeRemaining').text(`${timeLeft} seconds`);
    } else {
      $('#timeRemaining').text('Voting period has ended.');
      $('#yesBtn').attr('disabled', 'disabled');
      $('#noBtn').attr('disabled', 'disabled');
    }
  },
};
```

The `markVoted()` function is called after a user has successfully cast their vote. It updates the text displayed to the user to inform them that their vote has been cast and disables the voting buttons so that they cannot vote again.

The `updateTimeRemaining()` function is called every second to update the display of the time remaining in the voting period. It calculates the time remaining by subtracting the current time (in seconds since the Unix epoch) from the end time of the poll (also in seconds since the Unix epoch), and displays the result in the HTML element with the ID timeRemaining. If there is no time remaining, it updates the text to inform the user that the voting period has ended and disables the voting buttons.


## Finally, Initializin gthe App

```js
$(function() {
  $(window).load(() => {
    App.init();
  });
});
```

This code is using jQuery to execute a function when the page is fully loaded. The `$(function() {...})` line is shorthand for `$(document).ready(function() {...})`, which means that the enclosed function should be executed when the DOM is fully loaded.

Inside the function, `$(window).load()` is used to execute a function when all page assets (images, scripts, etc.) are loaded. The enclosed function calls `App.init()`, which initializes the application by setting up Web3, connecting to the contract, and binding event listeners.

Overall, this code ensures that the application is fully loaded and initialized before the user can interact with it.
