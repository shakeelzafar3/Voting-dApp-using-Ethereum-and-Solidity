## Final steps to launch the app
Let's take note of a few things that this code does:

1. Set up web3: [web3.js](https://web3js.readthedocs.io/en/1.0/) is a javascript library that allows our client-side application to talk to the blockchain. We configure web3 inside the "initWeb3" function.
2. Initialize contracts: We fetch the deployed instance of the smart contract inside this function and assign some values that will allow us to interact with it.
                          
                          
Now let's view the client-side application in the browser. First, make sure that you've migrated your contracts like this:
                          
```bash
truffle migrate --reset
```

Take out the account address and smart contract address and paste in the code where needed. 
                          

Next, start your development server from the command line like this:
```bash
npm run dev
```

This should automatically open a new browser window with your client-side application.
                          
![image](https://github.com/shakeelzafar3/images/blob/main/app.JPG)
         
         
Hurray!!! Now you can see the app is running, initially you can set the duration in seconds, which I have set to 10000 and as soon as I clicked `Start Poll` the buttons labled as `Yes` and `No` are activated, now you can cast a vote to yes or no. 
 In the bottom you will be able to see the results of each option. 
