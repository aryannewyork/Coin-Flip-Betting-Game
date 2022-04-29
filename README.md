
# Coin Flip Betting Game

In this game a user bets an amount on an unknown coin flip (toss).
The user does this by providing an integer either 0 or 1, 
representing heads or tails respectively and an amount that they want to place as bet, the amount should be a positive non-zero integer less than or equal to 100.
If the user guesses the coin flip correctly, then they get double the amount they placed as bet, and on an incorrect guess the user will not get the bet amount back.
The code for the game is written is Solidity language and it is deployed on the [Harmony One test network](https://explorer.pops.one/). The code uses [Harmony VRF (Verifiable Random Function)](https://docs.harmony.one/home/developers/tools/harmony-vrf) to generate verifiably random guesses (either 0 or 1, interpreted as heads or tales respectively). The user guesses are then run against these randomly generated guesses for evaluation.
After evaluation is completed an event is emitted that displays the user's address and their final balance after placing the bet.


## Authors

- [Aryan Shukla](https://www.github.com/aryannewyork)


## Deployment

To deploy this project
- Login to your MetaMask and make sure you are on the Harmony test network.

 _After setting up, your MetaMask wallet should look something like this_

![METAMASK](https://user-images.githubusercontent.com/79625246/166065143-ee13a0bf-7683-4a66-be55-b5198ad63a08.jpg)


- Make sure you account is funded, if not go to this [Harmony Testnet Faucet](https://faucet.pops.one/) and get your account funded with some Harmony testnet tokens.
- Open [remix IDE](https://remix.ethereum.org) on your web browser and make a new solidity file.
- Copy the solidity code from Contract.sol (from src folder) and paste it in your newly created solidity file on Remix IDE.
- Copy the following testnet deployment address (contract adress)

```bash
  0xdf60ad6c4d1df27ec4c797fb5cc9fc24c1180a8e
```
- Paste this address in the Remix deployment pane in the __At Address__ field.

![makebet2](https://user-images.githubusercontent.com/79625246/165965419-b563c95c-a317-4d47-9fd5-f48edc75f314.jpeg)


- After __At Address__ field is filled the __At Address__ button should become active, press the button, it will fetch the already deployed contract using its address.
- After this you should be able to make bets using the ```makeBet``` function, in the deployment pane itself

- Make sure the ```makeBet(bet, amount)``` function values in the input field are separated by a comma, __bets__ value should be an integer either 0 or 1 (representing heads or tales respectively) and __amount__ should be a non-zero integer between 0 and 100 (including 100).
- After making the bet (by pressing on the orange makeBet button, and confirming the transaction pop up on your MetaMask), you may click on the ```rewardBets()``` function (confirm the MetaMask pop up) to know if you won the bet and your final available balance.

__NOTE:__ After evaluation of your bet, your balance will be set to zero again, before you make the second bet.



## Testing

- 2 Bets were made for testing puroposes from different accounts.
- __Account 1:__ ```0x5e2d17cA3F75FD3B96bC49b283484A5B2bB4dB07```
- __Account 2:__ ```0xf7602E9d455127AB0Aa6835427104AaD7Dc734c6```

__NOTE:__ Account 1 has originally deployed the contract, and is also one of the players in the game. Account 2 was on a different node (system/computer) and it is the second player in the game.

__Bet 1__ 

![makebet1](https://user-images.githubusercontent.com/79625246/165966468-fc15838c-def0-4ce6-b852-34ffc8a6b95b.jpg)

_Transaction details of makeBet1_

![makebet1_log](https://user-images.githubusercontent.com/79625246/165966743-b4a5d5ac-1be3-48e0-9c55-237186a76987.jpg)


__Bet 2__ 

![makebet2](https://user-images.githubusercontent.com/79625246/165966875-685fc7f5-96b8-4a8d-bff1-c9af9d2e6749.jpeg)

_Transaction details of makeBet2_

![makebet2_log](https://user-images.githubusercontent.com/79625246/165967034-9542c92b-aecf-4e96-b7b7-437e034e1752.jpeg)

- After all the bets (2 in this case) have been made, Account 1 calls the rewardBets function that evaluates all the bets recorded thus far.

_Transaction details for rewardBet function call_

![reward1_log](https://user-images.githubusercontent.com/79625246/165967802-b1fbdd8c-abfd-4502-b4dd-70beb7a734c6.jpg)

- Account 1 (user 1) placed a bet of 57 on tales (1) and Account 2 (user 2) placed a bet of 90 on tales as well. As it is evident in the emit displayed, both users (players) lost the bet,
 and thus the points that they placed as bet are not returned to them, and thus the final balance of user 1 is 43 (100-57, as initially both players get 100 points to begin with) and final balance of user 2 is 10 (100-90), as expected.

- __The emit message__

![emit_message](https://user-images.githubusercontent.com/79625246/165969209-3fd6c778-df7b-4e08-9139-a9e9911425ad.jpg)


- All the transactions can be looked up at and verified on the [Harmony testnet block explorer](https://explorer.pops.one/)

![testnetransrecord](https://user-images.githubusercontent.com/79625246/165968368-f870dc49-4be5-4e0a-934c-c97e6eebe3cd.jpg)


- The contract deployment details can be looked up at the test net block explorer using this transaction hash
```0xd316a13c41d808c71b2b69aa224286bfb61ef31e426a5807ff8b5e348e7504ae```


![testnettransaction_proof_contract_deployment](https://user-images.githubusercontent.com/79625246/165968797-7d87e6e0-778a-4e95-86dd-124355cb3199.jpg)
