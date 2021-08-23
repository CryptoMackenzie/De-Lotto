De-Lotterify
=====

A basic lottery game implementation on Ethereum blockchain. Lotteries are heavily regulated by the governments, and aim of this project is to show people how easily you can build a lottery system on blockchain without trusting anyone and without spending millions of dollars for building a secure system.

## How does it work?
You need to deploy the [KriptoLottery](./contracts/KriptoLottery.sol) contract to an Ethereum network then you'll have the following features;
- Anyone can send send money to participate to the lottery as many times as they want.
- Default amount is `0.02 ether` unless you state otherwise in the contract constructor.
- Owner can set a ratio to send some or all of the money to a charity account.
- Owner can set a ratio to send some or all of the money to an affiliate account.
- Owner can call `runLottery` function to select a random winner and transfer the balance to charity, affiliate and to the winner. (See [Only owner can run the lottery section for more details](#Only-owner-can-run-the-lottery))


### User interface
Contract accepts payments and adds everyone to the list of participants. There is no user interface needed.

### Only owner can run the lottery
As the title states, only owner can run the lottery whereas  in a real **trustless** system anyone should be able to run the lottery. Even though this is very easy to implement, it's not that easy to unit test. Unfortunately, I am leaving this feature out until the tests are ready.

## Building the application
Project is using [truffle](truffleframework.com) to compile and deploy the contracts therefore you need to have Nodejs installed.

Run `npm install` to install the dependencies then you can run `npm test` to run the unit tests.

## Installing the application to an Ethereum network
Truffle commands helps you to install the contracts to a network. In this project it's slightly different but more useful. You can either use `npm run migrate` or alternatively if truffle is installed globally you can `truffle migrate` directly with the following arguments. These configurations can be updated by modifying the `./truffle-config.js`

`--network`: name of the network you want to deploy to. You can use `rinkeby` or `mainnet` depends on which one you would like to deploy the contract.

`--accessToken`: Deployment is using [infura](https://infura.io/) to deploy the contract. In order to deploy the contract you need to create an account, obtain the access token, and pass as an argument.

`--mnemonic`: 12 word mnemonic for the deployment account. Your account must have enough ether to cover the gas cost.

```
npm run migrate -- --network <<network>> --accessToken <<token>> --mnemonic <<12 word mnemonic>>
```
