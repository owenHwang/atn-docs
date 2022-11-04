---
description: >-
  This tutorial introduces you to interact with All That Node product to deploy
  sample ERC20 smart contract to Ethereum Network.
---

# A simple ERC20 Smart Contract

### Prerequisites

* Install [Node.js](https://nodejs.org/en/download/) LTS version (v16.15.0)
* Sign up to All That Node (ATN) and secure your account
* Download your own IDE - recommend [Visual Studio Code](https://code.visualstudio.com/)
* An Ethereum account with [Metamask](https://metamask.io/) or other equivalent wallet
* Install `Git` on your computer

## Step 0: Faucet - Fund your Ethereum Account

This tutorial uses Ethereum Kovan Network, which allows for developers to test the contract before deployment on the main Ethereum network. AllThatNode supports the feature called _**Faucet**_ for giving away some Kovan Ether (kETH) that can be only used in the testnet.

To claim your small amounts of testnet Ether, click to the [_**Faucet**_](https://www.allthatnode.com/faucet/ethereum.dsrv) button on the top of the ATN site.

![](<../.gitbook/assets/Frame 1.png>)

As of April 2022, _**AllThatNode Faucet**_ currently supports the following protocols and testnets. The faucet has planned to support more networks in that ATN plans to become the faucet aggregator which fully supports the multi-chain ecosystem development.

* Ethereum: Goerli Testnet, Kovan Testnet, Rinkeby Testnet, and Ropsten Testnet.
* Terra: Bombay Testnet
* Celo: Alfajores Testnet
* Solana: Devnet, Testnet
* Polygon: Mumbai Testnet
* Klaytn: Baobab Testnet

Choose your preferred network below. In this tutorial, you are expected to deploy the test contract to Kovan test network. Input your Ethereum Address to the form below, then click `Claim your tokens` below. The prompt will show up and require you to pass the CAPTCHA process.

![](<../.gitbook/assets/Frame 4.png>)

The faucet is required to keep a certain amount of balance to maintain the service, so please consider donating your remaining testnet Ether after finishing your testing and troubleshooting.

Please note that you cannot request to claim your testnet Ether once a day per network due to the limited resources as stated above.

You are shown succeeded transaction hash after clicking Claim your tokens button. To see the network status, please click the given link to the Etherscan address. When it comes to Kovan testnet, you are given **0.1 Kovan testnet** Ether from the Faucet.

The amount you are given could be differed from each network according to current status and remaining balance.

![](<../.gitbook/assets/Frame 5.png>)

![](<../.gitbook/assets/Frame 9-1.png>)

### If your Metamask does not connect to the Kovan testnet,&#x20;

you should manually enable the option to show test network. If you click `Show/hide test networks` button, you are shown the wallet preferences that can turn on seeing test networks.

After turning the option, you can now view the activated testnets if pressing the `Ethereum Mainnet` oval icon at the right top. Please toggle to `Kovan Test Network` to access the net. You will be able to see some micro-amount of testnet Ether for testing your contract in the testnet.



## Step 1: Setting up your development environments

We will use `Hardhat` framework to set up the development project that helps to build Ethereum based project easily. To note, please name your Hardhat project you are now presently working on, as this tutorial gives a general setup guide.

We'll use the `npm` CLI to install Hardhat. The Node.js package manager is a JavaScript package management and online repository.

Run the following commands in a new terminal.

```
mkdir hardhat-tutorial
cd hardhat-tutorial
npm init --yes
npm install --save-dev hardhat

npx hardhat
```

Select `Create a sample project` option to proceed.

```
$ npx hardhat

888    888                      888 888               888
888    888                      888 888               888
888    888                      888 888               888
8888888888  8888b.  888d888 .d88888 88888b.   8888b.  888888
888    888     "88b 888P"  d88" 888 888 "88b     "88b 888
888    888 .d888888 888    888  888 888  888 .d888888 888
888    888 888  888 888    Y88b 888 888  888 888  888 Y88b.
888    888 "Y888888 888     "Y88888 888  888 "Y888888  "Y888

Welcome to Hardhat v2.0.0

? What do you want to do? …
❯ Create a sample project
  Create an empty hardhat.config.js
  Quit
```

Please note that if you are in Mac or Linux environment, Hardhat will automatically ask you to install Ethers.js and Waffle plugins that help you to interact with Ethereum blockchain.

If you are in Windows environment, you should manually install the dependencies. Please refer to the command below if you wishes to install the dependencies in a manual fashion.

```
npm install --save-dev @nomiclabs/hardhat-ethers ethers @nomiclabs/hardhat-waffle ethereum-waffle chai
```

Hardhat looks for the closest `hardhat.config.js` file starting in the current working directory when it is launched. The `hardhat.config.js` will be initialized as shown below.

```javascript
// hardhat.config.js

require("@nomiclabs/hardhat-waffle");

/**
 * @type import('hardhat/config').HardhatUserConfig
 */
module.exports = {
  solidity: "0.7.3",
};
```

You are recommended to install [Solidity + Hardhat plugin in VSCode](https://marketplace.visualstudio.com/items?itemName=NomicFoundation.hardhat-solidity) or [Hardhat plugin in Intellij](https://plugins.jetbrains.com/plugin/18551-hardhat) to render IDE to highlight the grammar syntax.



## Step 2: Create a simple ERC20 smart contract

In this tutorial, we're going to make a basic smart contract that implements a transferrable token that follows ERC20 compliance. The most common purpose of token contracts is to trade or store value. The tutorial won't go through the contract's Solidity code in detail.

The contract will have the following logic.

* The entire supply of tokens is fixed and cannot be modified.
* The full supply is assigned to the contract's deployment address.
* Tokens can be given to anyone.&#x20;
* Tokens can be transferred by anyone who has at least one token.
* The token isn't divisible. You are allowed to transfer token in an `Integer` fashion.

The [ERC20](https://ethereum.org/en/developers/docs/standards/tokens/erc-20/) establishes a standard for Fungible Tokens, which means that each Token has a trait that makes it identical to another Token (in terms of type and value). An ERC-20 Token, for example, functions similarly to ETH, meaning that one Token is and will always be equal to all other Tokens.

We will use [the OpenZeppelin framework](https://docs.openzeppelin.com/contracts/4.x/erc20) to build the sample token that conforms to ERC20 standard. The OpenZeppelin Framework offers security technologies for developing, automating, and running decentralized applications. The framework is a library for creating safe smart contracts. Build on a strong foundation of code that has been verified by the community.

Install [OpenZeppelin library](https://docs.openzeppelin.com/contracts/4.x/) using `npm` or `yarn` package manager to use the boilerplate contracts.

```
npm install @openzeppelin/contracts
```

Once you have installed, create a new directory `contracts`, and then a file `ATNToken.sol` within that directory.

You are supposed to alter the file name to something more appropriate for you. Be sure that you have node\_modules directory in root folder and it includes `@openzeppelin/contracts` that you had installed earlier.

```solidity
// contracts/GLDToken.sol
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
import "hardhat/console.sol";

contract ATNToken is ERC20 {
    constructor(uint256 initialSupply) ERC20("AllThatNode", "ATN") {
        // initialSupply to 1000 tokens, input 1000 * (10 ** 18)
        // since it is 18 decimals
        console.log("You can debug here");
        _mint(msg.sender, initialSupply);
    }
}
```

Note that contracts are used via inheritance, and we're using ERC20 for both the basic standard implementation and the optional extensions for name, symbol, and decimals.

The contract also creates an initialSupply of tokens, which will be assigned to the contract's deployment address. ERC20 utilizes a decimal value of 18 by default. You must override the `decimals()` method in your contract to utilize a different number.

Unless you have a compelling reason not to, you'll generally want to utilize a de-facto standard that designates a decimals value of `18`, as Ether and other ERC20 token contracts do. You are expected to provide a number property `1000 * (10 ** 18)` when minting 1000 tokens.

To see how the code is organized, look at the [OpenZeppelin documentation](https://docs.openzeppelin.com/contracts/4.x/erc20).



## Step 3: Compiling a contract

Run `npx hardhat compile` in your terminal to compile the contract. Compile is an example of a built-in task.

```
$ npx hardhat compile
Compiling 1 file with 0.8.0
Compilation finished successfully
```

When you compile your contracts, the contract was translated to the bytecode in order to operate on the Ethereum Virtual Machine (EVM) by full nodes. During compilation, the function names and input arguments are hashed. As a result, in order for another account to invoke a function, the function name and parameters must first be provided.

A list of the contract's functions and parameters is known as the [ABI](https://github.com/ethereum/wiki/wiki/Ethereum-Contract-ABI), Application Binary Interface in JSON format. The ABI is used by an account that wants to utilize a smart contract's function to hash the function specification and generate the EVM bytecode needed to invoke the function.&#x20;

This is then included in a transaction's data field, and interpreted by the EVM at the destination account using the code. Each contract would have a ABI file, and ABI files are stored in artifacts directory in JSON type.

![example of artifacts & JSON abis](<../.gitbook/assets/image (5).png>)



## Step 4: Testing a contract

Create a new directory called `test` inside our project root directory and create a new file called `ATNToken-test.js`. The example test for the contract above is as follows.

To get further explanation, recommend to see [medium article](https://yuichiroaoki.medium.com/testing-erc20-smart-contracts-in-typescript-hardhat-9ad20eb40502) and [official documentation](https://hardhat.org/tutorial/testing-contracts.html).

```javascript
// ATNToken-test.js

const { expect } = require("chai");
const { ethers } = require("hardhat");

describe("Token contract", function () {

	let ATNToken;
	let owner;
	let addr1;
	let addr2;
	let addrs;

	beforeEach(async function () {
		[owner, addr1, addr2, ...addrs] = await ethers.getSigners();
		const ATNTokenFactory = (await ethers.getContractFactory("ATNToken"));
		ATNToken = await ATNTokenFactory.deploy(1000);

	});

	describe("Deployment", function () {
		it("Should assign the total supply of tokens to the owner", async function () {
			const ownerBalance = await ATNToken.balanceOf(owner.address);
			expect(await ATNToken.totalSupply()).to.equal(ownerBalance);
		});
	});

	describe("Transactions", function () {
		it("Should transfer tokens between accounts", async function () {
			// Transfer 50 tokens from owner to addr1
			await ATNToken.transfer(addr1.address, 50);
			const addr1Balance = await ATNToken.balanceOf(addr1.address);
			expect(addr1Balance).to.equal(50);

			// Transfer 50 tokens from addr1 to addr2
			// We use .connect(signer) to send a transaction from another account
			await ATNToken.connect(addr1).transfer(addr2.address, 50);
			const addr2Balance = await ATNToken.balanceOf(addr2.address);
			expect(addr2Balance).to.equal(50);
		});

		it("Should fail if sender doesn’t have enough tokens", async function () {
			const initialOwnerBalance = await ATNToken.balanceOf(owner.address);

			// Try to send 1 token from addr1 (0 tokens) to owner (1000 tokens).
			// `require` will evaluate false and revert the transaction.
			await expect(
				ATNToken.connect(addr1).transfer(owner.address, 1)
			).to.be.revertedWith("ERC20: transfer amount exceeds balance");

			// Owner balance shouldn't have changed.
			expect(await ATNToken.balanceOf(owner.address)).to.equal(
				initialOwnerBalance
			);
		});

		it("Should update balances after transfers", async function () {
			const initialOwnerBalance = await ATNToken.balanceOf(owner.address);

			// Transfer 100 tokens from owner to addr1.
			await ATNToken.transfer(addr1.address, 100);

			// Transfer another 50 tokens from owner to addr2.
			await ATNToken.transfer(addr2.address, 50);

			// Check balances.
			const finalOwnerBalance = await ATNToken.balanceOf(owner.address);
			expect(finalOwnerBalance).to.equal(initialOwnerBalance.sub(150));

			const addr1Balance = await ATNToken.balanceOf(addr1.address);
			expect(addr1Balance).to.equal(100);

			const addr2Balance = await ATNToken.balanceOf(addr2.address);
			expect(addr2Balance).to.equal(50);
		});
	});
});
```

On your terminal run `npx hardhat test`. You should see the following output.

If you run test command without compiling contract precedingly, Hardhat automatically compiles the contract and testing the contract.

```
$ npx hardhat test

  Token contract
    ✓ Should assign the total supply of tokens to the owner
    ✓ Should transfer tokens between accounts
    ✓ Should fail if sender doesn’t have enough tokens
    ✓ Should update balances after transfers


  4 passing
```



## Step 5: Deploy to Local Network

Hardhat is pre-installed with a local Ethereum development network. You may use it to deploy contracts, perform tests, and debug your code. It's the default network for Hardhat, so you don't have to do anything to make it function.

Create a new directory called `scripts` inside our project root directory and create a new file called `deploy.js`. The example test for the contract above is as follows.

> Make sure that your contract name is to be the same as the parameter which is to be injected in `getContractFactory`. In addition, do not forget to use async/await pattern when running main function to properly handle potential errors.

```javascript
// deploy.js

const hre = require("hardhat");

async function main() {
  // deploying ERC20 token
  const [owner, addr1] = await ethers.getSigners();

  const MyToken = await hre.ethers.getContractFactory("ATNToken");
  console.log('Deploying ATNToken...');
  const token = await ATNToken.deploy();
  await token.deployed();
  console.log("Token deployed to:", token.address);
}

// We recommend this pattern to be able to use async/await everywhere
// and properly handle errors.
main()
  .then(() => process.exit(0))
  .catch((error) => {
    console.error(error);
    process.exit(1);
  });

```

Executing a script without the `—network` flag causes the code to execute against an embedded instance of Hardhat Network. Please be aware that resulting in the deployment being terminated of a local network when Hardhat scripts end.

```
$ npx hardhat run scripts/deploy.js
Deploying contracts with the account: 0xf39Fd6e51aad88F6F4ce6aB8827279cffFb92266
Account balance: 10000000000000000000000
Token address: 0x5FbDB2315678afecb367f032d93F642f64180aa3
```



## Step 6: Deploy to Live Network

To deploy to a remote network such as a mainnet or any testnet, you need to add a network entry to your `hardhat.config.js` file. We’ll use Kovan for this example.

To deploy to live network, you are required to export AllThatNode API KEY in a AllThatNode dashboard and wallet private key from Metamask.

Make sure your API KEY and private key aren't exposed to the internet (e.g. commit to the GitHub). Anyone with your private keys can steal any assets held in your account. In this tutorial, you are going to use `dotenv` framework to hide your secrets and inject the information in runtime.

```javascript
// hardhat.config.js

require("@nomiclabs/hardhat-waffle");
require('dotenv').config();

module.exports = {
  solidity: "0.8.0",
  networks: {
    kovan: {
      url: `${ALLTHATNODE_API_URL}`,
      accounts: [`${PRIVATE_KEY}`]
    }
  }
};
```

### Getting AllThatNode API KEY

1. Go to [AllThatNode](https://www.allthatnode.com/main.dsrv) site and click to protocols.

![](<../.gitbook/assets/Frame 2-1.png>)

2\. On protocol page, click `Ethereum` and `Create New Project` button.

![](<../.gitbook/assets/Frame 3 (1).png>)

3\. Name the project with your preferred title and create new project.

![](<../.gitbook/assets/Frame 10 (1).png>)

4\. Recheck your plan and create new project. AllThatNode is free for all developers and it supports 10,000 daily request per a day.

![](<../.gitbook/assets/Frame 11.png>)

5\. You will be able to see new Ethereum project on Dashboard. Click the Ethereum project.

![](<../.gitbook/assets/Frame 19.png>)

6\. Scroll down the page on Dashboard. You are able to check API Key and RPC URL. Click to copy the RPC URL of Kovan test network (the URL includes API Key)

![](<../.gitbook/assets/Frame 12 (1).png>)

### Getting Metamask Private Key

We need to add the account on a hardhat configuration to use for deploying the contract. To access the wallet, your private key should be injected. Note again, be careful with your private key, it gives access to your wallet and will spend its testnet Ether to deploy the contract.

![](<../.gitbook/assets/Frame 17.png>)

1. Open up your Metamask wallet extension, and click three dots at the upper right corner.
2. Click on the “Account Details” button.
3. Click “Export Private Key”.
4. Enter your password and click “Confirm”.
5. Your private key is revealed. Click to copy it, and save it somewhere safe.
6. Click “Done” to close the screen.

### Setting up `.env` <a href="#step-5--set-up--env" id="step-5--set-up--env"></a>

1. Install `dotenv` dependencies using npm or yarn library.

```
npm install dotenv
```

1. In your project's root folder, create a file `.env`
2. Open the `.env` file and copy-paste the following contents:

```javascript
// .env

ALLTHATNODE_API_URL="copy and paste your kovan api url here"
PRIVATE_KEY="input your private key here"
```

> Please note that .env file should not be revealed to anywhere (e.g. push it to GitHub)

3\. Any file that loads the `.env` file by placing at the top will have access to the variables in that file by using `process.env`which implies `hardhat.config.js` will now work and load the `.env` variables and values correctly.

```javascript
// hardhat.config.js

require('dotenv').config();
```

### Deploy to Kovan testnet network&#x20;

Finally, run the following command. If everything went well, you should see the deployed address.

```
npx hardhat run scripts/deploy.js --network kovan
```



## Step 7: Verifying your contracts to Etherscan

### Why Verification?

Users dealing with smart contracts benefit from source code verification because it gives transparency. [Etherscan](https://etherscan.io/) will compare the compiled bytecode to the deployed bytecode on the blockchain when you submit the source code. A smart contract, should provide end users additional information about what they are "digitally signing" for and allow them to audit the code to independently verify that it performs what it says it does.

You are required to install additional dependencies to help your contracts to be verified at Etherscan. Run the command as the following.

```
npm install @nomiclabs/hardhat-etherscan
```

If the installation is done, making a modest change to the file `hardhat.config.js`. We must additionally load the module using the `require()` method after the plugin has been installed. There should already be a `require()` function call at the top of the file; all we have to do now is add `require("@nomiclabs/hardhat-etherscan");` beneath it. Refer to the following code.

```javascript
// hardhat.config.js

require("@nomiclabs/hardhat-waffle");
require("@nomiclabs/hardhat-etherscan");
require('dotenv').config();

module.exports = {
  solidity: "0.8.0",
  networks: {
    kovan: {
      url: `${ALLTHATNODE_API_URL}`,
      accounts: [`${process.env.PRIVATE_KEY}`]
    }
  }
};
```

You are required to retrieve API Key from Etherscan. Sign up to [Etherscan](https://etherscan.io/register) here and create your account. After logged into Etherscan, click your profile and scroll down to access [API Key page](https://etherscan.io/myapikey).

![](<../.gitbook/assets/Frame 21.png>)

In API Key page, you might be able to see `+Add` button. Click the button to create new API Key.

![](<../.gitbook/assets/Frame 22 (1).png>)

After creating new API Key, click the Key to copy the secret. Then, open up your `.env` file and paste your API Key on the file.

```
// .env

ALLTHATNODE_API_URL="copy and paste your kovan api url here"
PRIVATE_KEY="input your private key here"
ETHERSCAN_APIKEY="input your API key here"
```

Then, add the Etherscan property on `hardhat.config.js` file as follows.

```javascript
// hardhat.config.js

require("@nomiclabs/hardhat-waffle");
require('dotenv').config();

module.exports = {
  solidity: "0.8.0",
  networks: {
    kovan: {
      url: `${ALLTHATNODE_API_URL}`,
      accounts: [`${PRIVATE_KEY}`]
    }
  },
  etherscan: {
    apiKey: `${ETHERSCAN_APIKEY}`
  }
};
```

We now have everything we need to validate our smart contract, having accomplished all of the previous processes of building a smart contract, a deployment script, and modifying the config file. Let's run following command to deploy our contract on the Kovan test network.

You should designate which network to be deployed on after `--network` flag. The name should be pre-declared on the networks property at `hardhat.config.js`.

```
npx hardhat verify YOUR_CONTRACT_ADDRESS --network kovan
```



## That's It! What's next?

That's all there is to it; congrats! With Hardhat and AllThatNode, you've created, deployed, and validated your own ERC20 smart contract!

You may use the same contract code on AllThatNode to deploy it on any other EVM-compatible chains, such as [Polygon](https://www.allthatnode.com/polygon.dsrv) and [Avalanche](https://www.allthatnode.com/avalanche.dsrv), in the same way you did on the Ethereum test network.\
