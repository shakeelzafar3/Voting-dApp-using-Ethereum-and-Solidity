## Head tag
```html
<head>
	<title>Voting dApp</title>
  <meta charset="utf-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link href="css/bootstrap.min.css" rel="stylesheet">
	<script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
	<script src="./app.js"></script>
</head>
```
## Explanation
The `head` tag is used to define the head section of the HTML document, which contains information about the document such as its title, character encoding, and links to external resources. In this code snippet, the following elements are included in the head section:

- `title`: This tag defines the title of the web page, which is displayed in the browser's title bar or tab.
- `meta`: These tags provide metadata about the web page, such as its character encoding and compatibility with specific browsers.
- `link`: This tag is used to link external resources such as stylesheets, which are used to apply visual styles to the web page.
- `script`: These tags are used to include JavaScript files in the web page.

Specifically, the `meta` tags in this code snippet specify that the document's character encoding is UTF-8, and that it should be displayed using the latest version of Internet Explorer. The `link` tag links to an external CSS stylesheet, and the `script` tags link to external JavaScript files.

The `jquery` script is loaded from a remote server using the `script` tag with a `src` attribute pointing to the jQuery library hosted on the code.jquery.com domain. This library is used to simplify JavaScript programming and provide a more powerful and flexible API for manipulating HTML documents.

The `app.js` script is also loaded using the `script` tag. This script likely contains custom JavaScript code for the voting application, such as functions to start a poll, cast a vote, and display the results.

## Setting the duration of the voting perio
  
```
<body>
	<h1>Voting dApp</h1>
	<div>
		<h3>Setting the duration of the voting period</h3>
		<p>Please enter the duration of the voting period (in seconds):</p>
		<input type="number" id="pollDuration" placeholder="Enter duration in seconds">
		<button id="startPollBtn" onclick="startPoll()">Start Poll</button>
	</div>
	<hr>
```

- The <body> tag: This tag is used to define the body section of the HTML document, which contains the visible content of the web page.

- The <h1> tag: This tag is used to define the heading of the web page, in this case "Voting dApp".

- The <div> tag: This tag is used to group together elements and apply styles to them as a group.

- The <h3> tag: This tag is used to define a sub-heading on the web page, in this case "Setting the duration of the voting period".

- The <p> tag: This tag is used to define a paragraph of text on the web page, in this case "Please enter the duration of the voting period (in seconds):".

- The <input> tag: This tag is used to create an input field where the user can enter data, in this case the number of seconds for the voting period.

- The type="number" attribute: This attribute is used to specify that the input field should only accept numeric input.

- The id="pollDuration" attribute: This attribute is used to give the input field a unique identifier, which can be used to access and manipulate its value using JavaScript.

- The placeholder="Enter duration in seconds" attribute: This attribute is used to provide a hint to the user about what they should enter in the input field.

- The <button> tag: This tag is used to create a button on the web page.

- The id="startPollBtn" attribute: This attribute is used to give the button a unique identifier, which can be used to access and manipulate it using JavaScript.

- The onclick="startPoll()" attribute: This attribute is used to specify that the startPoll() function should be called when the button is clicked.

- The <hr> tag: This tag is used to create a horizontal line on the web page, to visually separate different sections of content.
 
 ## Allowing users to cast their votes during the voting period
  
 ```html
 <div>
		<h3>Allowing users to cast their votes during the voting period</h3>
		<p>Please cast your vote:</p>
		<button id="yesBtn" onclick="castVote(true)" disabled>Yes</button>
		<button id="noBtn" onclick="castVote(false)" disabled>No</button>
		<p id="voteStatus"></p>
	</div>
	<hr>
 ```
  
  
This code creates a section on the HTML page that allows users to cast their votes during the voting period. It includes two buttons with the IDs "yesBtn" and "noBtn" that allow users to cast their votes for "Yes" or "No". These buttons are initially disabled until the voting period begins. When a user clicks on one of the buttons, it triggers the "castVote()" function with the argument of "true" for the "Yes" button and "false" for the "No" button.

Additionally, there is a paragraph with the ID "voteStatus" that displays the current vote status. This is also initially hidden and will only be displayed when the user casts their vote. The code is wrapped in a div tag for organization purposes and there is a horizontal rule (<hr>) element separating this section from the previous one.
  
## Preventing users from voting after the voting period has ended
```html
	<div>
	<h3>Preventing users from voting after the voting period has ended</h3>
		<p>Voting period ends in: <span id="timeRemaining"></span></p>
	</div>
	<hr>
	<div>
		<h3>Tallying the results and displaying them for all to see</h3>
		<p>Results:</p>
		<p>Yes votes: <span id="yesVotes"></span></p>
		<p>No votes: <span id="noVotes"></span></p>
	</div>
  <script src="https://ajax.googleapis.com/ajax/libs/jquery/1.12.4/jquery.min.js"></script>
    <!-- Include all compiled plugins (below), or include individual files as needed -->
    <script src="js/bootstrap.min.js"></script>
    <script src="js/web3.min.js"></script>
    <script src="js/truffle-contract.js"></script>
    <script src="js/app.js"></script>
</body>
```
  
 The first feature is "Preventing users from voting after the voting period has ended". It displays the time remaining in the voting period, and uses the "timeRemaining" span to show the remaining time.
The second feature is "Tallying the results and displaying them for all to see". It displays the total number of Yes and No votes in two separate spans, "yesVotes" and "noVotes" respectively.
The code also includes the necessary JavaScript libraries required to run the dApp, including jQuery, Bootstrap, web3, truffle-contract, and the app.js file which contains the logic for the dApp.

