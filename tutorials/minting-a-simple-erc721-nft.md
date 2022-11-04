---
description: >-
  This tutorial introduces you to interact with All That Node product to deploy
  and mint sample ERC721-based NFT (non-fungible token) smart contract to
  Rinkeby Network.
---

# Minting a simple ERC721 NFT

### Prerequisites

* Install [Node.js](https://nodejs.org/en/download/) LTS version (v16.15.0)
* Sign up to All That Node (ATN) and secure your account
* Download your own IDE - recommend [Visual Studio Code](https://code.visualstudio.com/)
* An Ethereum account with [Metamask](https://metamask.io/) or other equivalent wallet
* Install `Git` on your computer

## Step 0: Faucet - Fund your Ethereum Account

This tutorial uses Ethereum Rinkeby Network, which allows for developers to test the contract before deployment on the main Ethereum network. AllThatNode supports the feature called _**Faucet**_ for giving away some Rinkeby Ether (rETH) that can be only used in the testnet.

> We're utilizing Rinkeby Testnet since OpenSea, a centralized NFT marketplace, supports the Rinkeby Network among the testnets.

To claim your small amounts of testnet Ether, click to the [_**Faucet**_](https://www.allthatnode.com/faucet/ethereum.dsrv) button on the top of the ATN site.

![](<../.gitbook/assets/Frame 16.png>)

As of April 2022, _**AllThatNode Faucet**_ currently supports the following protocols and testnets. The faucet has planned to support more networks in that ATN plans to become the faucet aggregator which fully supports the multi-chain ecosystem development.

* Ethereum: Goerli Testnet, Kovan Testnet, Rinkeby Testnet, and Ropsten Testnet.
* Terra: Bombay Testnet
* Celo: Alfajores Testnet
* Solana: Devnet, Testnet
* Polygon: Mumbai Testnet
* Klaytn: Baobab Testnet

Choose your preferred network below. In this tutorial, you are expected to deploy the test contract to Rinkeby test network. Input your Ethereum Address to the form below, then click `Claim your tokens` below. The prompt will show up and require you to pass the CAPTCHA process.

![](<../.gitbook/assets/Frame 13.png>)

The faucet is required to keep a certain amount of balance to maintain the service, so please consider donating your remaining testnet Ether after finishing your testing and troubleshooting.

Please note that you cannot request to claim your testnet Ether once a day per network due to the limited resources as stated above.

You are shown succeeded transaction hash after clicking Claim your tokens button. To see the network status, please click the given link to the Etherscan address. When it comes to Rinkeby testnet, you are given **0.1 Rinkeby testnet** Ether from the Faucet.

The amount you are given could be differed from each network according to current status and remaining balance.

![](<../.gitbook/assets/Frame 14.png>)

![](<../.gitbook/assets/Frame 9-1 (1).png>)

### If your Metamask does not connect to the Rinkeby testnet,&#x20;

you should manually enable the option to show test network. If you click `Show/hide test networks` button, you are shown the wallet preferences that can turn on seeing test networks.

After turning the option, you can now view the activated testnets if pressing the `Ethereum Mainnet` oval icon at the right top. Please toggle to `Rinkeby Test Network` to access the net. You will be able to see some micro-amount of testnet Ether for testing your contract in the testnet.



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
  solidity: "0.8.0",
};
```

You are recommended to install [Solidity + Hardhat plugin in VSCode](https://marketplace.visualstudio.com/items?itemName=NomicFoundation.hardhat-solidity) or [Hardhat plugin in Intellij](https://plugins.jetbrains.com/plugin/18551-hardhat) to render IDE to highlight the grammar syntax.

## Step 2: Create a simple ERC721 NFT smart contract

#### What is NFT (Non-Fungible Tokens)?

NFTs are non-interchangeable, one-of-a-kind digital tokens. They are immutable data units kept on the blockchain that may be linked to almost any digital or physical asset, including images, movies, and real estate. Because they rely on digital ledgers to confirm ownership, they are a strong deterrent to fraud and plagiarism. NFTs, like cryptocurrencies, are often acquired and exchanged on-chain, maintaining their uniqueness by producing digital scarcity. Reducing the availability of a certain asset frequently increases demand and hence price.

NFTs are immutable data units that may be linked to practically any digital or physical asset, such as images, movies, or real estate, and are kept on the blockchain. Because they rely on digital ledgers to confirm ownership, they are a strong deterrent to fraud and plagiarism. NFTs are frequently purchased and traded on-chain, alongside cryptocurrencies, which maintain their exclusivity by creating digital scarcity.

In this tutorial, we're going to make a basic NFT smart contract that implements a transferrable token that follows [ERC721 compliance](https://docs.openzeppelin.com/contracts/2.x/erc721). The most common purpose of token contracts is to trade or store value. The tutorial won't go through the contract's Solidity code in detail.

Let's say if not all tokens are alike. This occurs in circumstances such as real estate or collectibles, when certain goods are more valuable than others owing to their use, rarity, and so on. ERC721 is a standard for expressing ownership of non-fungible tokens, or tokens that are distinct from one another.

ERC721 is a more sophisticated standard than ERC20, with many potential extensions and different contracts. We will use [the OpenZeppelin framework](https://docs.openzeppelin.com/contracts/2.x/api/token/erc721) to build the sample token that conforms to ERC721 standard. The OpenZeppelin Framework offers security technologies for developing, automating, and running decentralized applications. The framework is a library for creating safe smart contracts. Build on a strong foundation of code that has been verified by the community.

Install [OpenZeppelin library](https://docs.openzeppelin.com/contracts/4.x/) using `npm` or `yarn` package manager to use the boilerplate contracts.

```
npm install @openzeppelin/contracts
```

Once you have installed, create a new directory `contracts`, and then a file `DSRVNFT.sol` within that directory.

You are supposed to alter the file name to something more appropriate for you. Be sure that you have node\_modules directory in root folder and it includes `@openzeppelin/contracts` that you had installed earlier.

```solidity
// contracts/DSRVNFT.sol
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "@openzeppelin/contracts/token/ERC721/ERC721.sol";
import "@openzeppelin/contracts/utils/Strings.sol";
import "./base64.sol";
import "hardhat/console.sol";

contract DSRVNFT is ERC721 {
    uint256 private _currentNFTId = 0; // Starts from 1 when incrementing the ID

    constructor(
        string memory _name,
        string memory _symbol
    ) ERC721(_name, _symbol) {}

    function mintTo(address _to) public {
        uint256 newNFTId = _getNextNFTId();
        _mint(_to, newNFTId);
        console.log("New NFT ID:", newNFTId);
        _incrementCurrentNFTId();
    }
    
    function _getNextNFTId() private view returns (uint256) {
        return _currentNFTId + 1;
    }
    
    function _incrementCurrentNFTId() private {
        _currentNFTId++;
    }

    function tokenURI(uint256 tokenId) override public pure returns (string memory) {
        string[3] memory parts;
        parts[0] = '<svg xmlns="http://www.w3.org/2000/svg" preserveAspectRatio="xMinYMin meet" viewBox="0 0 350 350"><style>.base { fill: white; font-family: serif; font-size: 14px; }</style><rect width="100%" height="100%" fill="black" /><text x="10" y="20" class="base">';

        parts[1] = Strings.toString(tokenId);

        parts[2] = '</text></svg>';

        string memory output = string(abi.encodePacked(parts[0], parts[1], parts[2]));

        string memory json = Base64.encode(bytes(string(abi.encodePacked('{"name": "Badge #', Strings.toString(tokenId), '", "description": "A concise Hardhat tutorial Badge NFT with on-chain SVG images like look.", "image": "data:image/svg+xml;base64,', Base64.encode(bytes(output)), '"}'))));
            
        output = string(abi.encodePacked('data:application/json;base64,', json));

        return output;
    }
}
```

Note that contracts works in the following ways.

* TokenID starts at 1 and increments by 1 every time it is used.
* Anyone create an NFT token by invoking `mintTo(destinationAddress)` with the Token ID.
* Encoding SVG image file data and upload to the `storage` of a NFT account.

We'll utilize [an online base64 decoder](https://www.base64decode.org/) to obtain the original data from the encoded string. In this tutorial, we will decode the output data, and then decode the SVG image data.

Why Base64? It is to encode the string and picture for SVG format to save gas costs while deploying to on-chain. You can also take a look at the SVG file by decoding the string [here](https://www.svgviewer.dev).

When dealing with more complicated files, such as high-quality images, you have the choice of deploying your picture to a centralized cloud service, such as AWS, or a decentralized service, such as IPFS. In this lesson, we'll go through how to use SVG metadata for on-chain.

To comply with the OpenSea metadata standard, the NFT metadata needs the data attributes 1) `name`, 2) `description`, and 3) `picture` to be given, as shown below.

```json
{
  "name": "DSRV #1",
  "description": "I love DSRV and AllThatNode",
  "image": "data:image/svg+xml;base64,PHN2ZyB4bWxucz0asdSDFWEZSVvByZXNlcnZlQXNwZWN0UmF0vXEWERdhNaW5ZTWluIG1lZXQiIHZpZXdCb3g9IjAgMCAzNTAgMzUwIj48c3R5bGU+LmJhc2UgeyBmaWxsOiB3aGl0ZTsgZm9udC1mYW1pbHk6IHNlcmlmOyBmb250LXNpemU6IDE0cHg7IH08L3N0eWxlPjxyZWN0IHdpZHRoPSIxMDAlIiBoZWlnaHQ9IjEwMCUiIGZpbGw9ImJsYWNrIiAvPjx0ZXh0IHg9IjEwIiB5PSIyMCIgY2xhc3M9ImJhc2UiPjM8L3RleHQ+PC9zdmc+"
}
```

You can change this, but almost every NFT includes a name, description, and a link to anything, such as a video, image, or other resource. It can even have personalized qualities.

Be mindful of the format of your metadata; if it does not conform to the [OpenSea Requirements](https://docs.opensea.io/docs/metadata-standards), your NFT will seem broken on the website. All of this is part of the ERC721 standards, and it enables individuals to construct websites on top of NFT data.

OpenSea, for example, is a marketplace for NFTs. Furthermore, every NFT on OpenSea adheres to the ERC721 metadata standard, making it simple for anyone to buy/sell NFTs.

To see how the code is organized, look at the [OpenZeppelin documentation](https://docs.openzeppelin.com/contracts/2.x/api/token/erc721). In addition, take a look at the following tutorial on the [dev.to article](https://dev.to/0xmojo7/on-chain-svg-generation-part-1-2678).

Last but not least, the base64 contract must be imported. In the following implementation, we will make use of the [base64 library](https://github.com/Brechtpd/base64). Please copy and paste the following code into the contracts folder, which is the same directory as DSRVNFT.sol. The name should be `Base64.sol`.

```solidity
// SPDX-License-Identifier: MIT
// ./contracts/base64.sol
pragma solidity >=0.6.0;

/// @title Base64
/// @author Brecht Devos - <brecht@loopring.org>
/// @notice Provides functions for encoding/decoding base64
library Base64 {
    string internal constant TABLE_ENCODE = 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789+/';
    bytes  internal constant TABLE_DECODE = hex"0000000000000000000000000000000000000000000000000000000000000000"
                                            hex"00000000000000000000003e0000003f3435363738393a3b3c3d000000000000"
                                            hex"00000102030405060708090a0b0c0d0e0f101112131415161718190000000000"
                                            hex"001a1b1c1d1e1f202122232425262728292a2b2c2d2e2f303132330000000000";

    function encode(bytes memory data) internal pure returns (string memory) {
        if (data.length == 0) return '';

        // load the table into memory
        string memory table = TABLE_ENCODE;

        // multiply by 4/3 rounded up
        uint256 encodedLen = 4 * ((data.length + 2) / 3);

        // add some extra buffer at the end required for the writing
        string memory result = new string(encodedLen + 32);

        assembly {
            // set the actual output length
            mstore(result, encodedLen)

            // prepare the lookup table
            let tablePtr := add(table, 1)

            // input ptr
            let dataPtr := data
            let endPtr := add(dataPtr, mload(data))

            // result ptr, jump over length
            let resultPtr := add(result, 32)

            // run over the input, 3 bytes at a time
            for {} lt(dataPtr, endPtr) {}
            {
                // read 3 bytes
                dataPtr := add(dataPtr, 3)
                let input := mload(dataPtr)

                // write 4 characters
                mstore8(resultPtr, mload(add(tablePtr, and(shr(18, input), 0x3F))))
                resultPtr := add(resultPtr, 1)
                mstore8(resultPtr, mload(add(tablePtr, and(shr(12, input), 0x3F))))
                resultPtr := add(resultPtr, 1)
                mstore8(resultPtr, mload(add(tablePtr, and(shr( 6, input), 0x3F))))
                resultPtr := add(resultPtr, 1)
                mstore8(resultPtr, mload(add(tablePtr, and(        input,  0x3F))))
                resultPtr := add(resultPtr, 1)
            }

            // padding with '='
            switch mod(mload(data), 3)
            case 1 { mstore(sub(resultPtr, 2), shl(240, 0x3d3d)) }
            case 2 { mstore(sub(resultPtr, 1), shl(248, 0x3d)) }
        }

        return result;
    }

    function decode(string memory _data) internal pure returns (bytes memory) {
        bytes memory data = bytes(_data);

        if (data.length == 0) return new bytes(0);
        require(data.length % 4 == 0, "invalid base64 decoder input");

        // load the table into memory
        bytes memory table = TABLE_DECODE;

        // every 4 characters represent 3 bytes
        uint256 decodedLen = (data.length / 4) * 3;

        // add some extra buffer at the end required for the writing
        bytes memory result = new bytes(decodedLen + 32);

        assembly {
            // padding with '='
            let lastBytes := mload(add(data, mload(data)))
            if eq(and(lastBytes, 0xFF), 0x3d) {
                decodedLen := sub(decodedLen, 1)
                if eq(and(lastBytes, 0xFFFF), 0x3d3d) {
                    decodedLen := sub(decodedLen, 1)
                }
            }

            // set the actual output length
            mstore(result, decodedLen)

            // prepare the lookup table
            let tablePtr := add(table, 1)

            // input ptr
            let dataPtr := data
            let endPtr := add(dataPtr, mload(data))

            // result ptr, jump over length
            let resultPtr := add(result, 32)

            // run over the input, 4 characters at a time
            for {} lt(dataPtr, endPtr) {}
            {
               // read 4 characters
               dataPtr := add(dataPtr, 4)
               let input := mload(dataPtr)

               // write 3 bytes
               let output := add(
                   add(
                       shl(18, and(mload(add(tablePtr, and(shr(24, input), 0xFF))), 0xFF)),
                       shl(12, and(mload(add(tablePtr, and(shr(16, input), 0xFF))), 0xFF))),
                   add(
                       shl( 6, and(mload(add(tablePtr, and(shr( 8, input), 0xFF))), 0xFF)),
                               and(mload(add(tablePtr, and(        input , 0xFF))), 0xFF)
                    )
                )
                mstore(resultPtr, shl(232, output))
                resultPtr := add(resultPtr, 3)
            }
        }

        return result;
    }
}s
```

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

Create a new directory called `test` inside our project root directory and create a new file called `DSRVNFT-test.js`. The example test for the contract above is as follows.

To get further explanation, recommend to see [dev.to article](https://dev.to/yakult/a-concise-hardhat-tutorial-part-2-writing-erc721-nft-5gm6) and [official documentation](https://hardhat.org/tutorial/testing-contracts.html).

```javascript
// DSRVNFT-test.js
const { expect } = require("chai");

describe("Sample ERC721 NFT contract", function () {
  let DSRVNFTFactory;
  let DSRVNFT;
  let _name = "DSRVNFT";
  let _symbol = "DSRV";
  let account1, other_accounts;

  before(async function () {
    DSRVNFTFactoryNFT = await hre.ethers.getContractFactory("DSRVNFT");
    [owner, account1, ...other_accounts] = await hre.ethers.getSigners();

    DSRVNFT = await DSRVNFTFactoryNFT.deploy(_name, _symbol);
    await DSRVNFT.deployed();
  });

  // You can nest describe calls to create subsections.
  describe("Deployment", function () {
    it("Should have a correct name and symbol", async function () {
      expect(await DSRVNFT.name()).to.equal(_name);
      expect(await DSRVNFT.symbol()).to.equal(_symbol);
    });

    it("Should mint a token with token ID 1 and 2 to account1", async function () {
      const minter = account1.address;
      await DSRVNFT.mintTo(minter);
      expect(await DSRVNFT.ownerOf(1)).to.equal(minter);

      await DSRVNFT.mintTo(minter);
      expect(await DSRVNFT.ownerOf(2)).to.equal(minter);

      expect(await DSRVNFT.balanceOf(minter)).to.equal(2);
    });
  });
});

```

On your terminal run `npx hardhat test`. You should see the following output.

If you run test command without compiling contract precedingly, Hardhat automatically compiles the contract and testing the contract.

```
$ npx hardhat test

  Sample ERC721 NFT contract
    Deployment
      ✓ Should have a correct name and symbol
      ✓ Should mint a token with token ID 1 and 2 to account1

  2 passing
```

## Step 5: Deploy to Local Network

Hardhat is pre-installed with a local Ethereum development network. You may use it to deploy contracts, perform tests, and debug your code. It's the default network for Hardhat, so you don't have to do anything to make it function.

Create a new directory called `scripts` inside our project root directory and create a new file called `deploy.js`. The example test for the contract above is as follows.

> Make sure that your contract name is to be the same as the parameter which is to be injected in `getContractFactory`. In addition, do not forget to use async/await pattern when running main function to properly handle potential errors.

```javascript
// deploy.js

const hre = require("hardhat");

async function main() {
  const DSRVNFTFactoryNFT = await hre.ethers.getContractFactory("DSRVNFT");
  console.log('Deploying DSRVNFT ERC721 token...');
  const DSRVNFT = await DSRVNFTFactoryNFT.deploy('DSRVNFT','DSRV');

  await DSRVNFT.deployed();
  console.log("DSRVNFT deployed to:", DSRVNFT.address);
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
Deploying DSRVNFT ERC721 token...
DSRVNFT deployed to: 0xf39Fd6e51aad88F6F4ce6aB8827279cffFb92266
```

## Step 6: Deploy to Live Network

To deploy to a remote network such as a mainnet or any testnet, you need to add a network entry to your `hardhat.config.js` file. We’ll use Rinkeby for this example.

To deploy to live network, you are required to export AllThatNode API KEY in a AllThatNode dashboard and wallet private key from Metamask.

Make sure your API KEY and private key aren't exposed to the internet (e.g. commit to the GitHub). Anyone with your private keys can steal any assets held in your account. In this tutorial, you are going to use `dotenv` framework to hide your secrets and inject the information in runtime.

```javascript
// hardhat.config.js

require("@nomiclabs/hardhat-waffle");
require('dotenv').config();

module.exports = {
  solidity: "0.8.0",
  networks: {
    rinkeby: {
      url: `${ALLTHATNODE_API_URL}`,
      accounts: [`${PRIVATE_KEY}`]
    }
  }
};
```

### Getting AllThatNode API KEY

1. Go to [AllThatNode](https://www.allthatnode.com/main.dsrv) site and click to protocols.

![](<../.gitbook/assets/Frame 18.png>)

2\. On protocol page, click `Ethereum` and `Create New Project` button.

![](<../.gitbook/assets/Frame 3 (1).png>)

3\. Name the project with your preferred title and create new project.

![](<../.gitbook/assets/Frame 10 (1).png>)

4\. Recheck your plan and create new project. AllThatNode is free for all developers and it supports 10,000 daily request per a day.

![](<../.gitbook/assets/Frame 11.png>)

5\. You will be able to see new Ethereum project on Dashboard. Click the Ethereum project.

![](<../.gitbook/assets/Frame 19.png>)

6\. Scroll down the page on Dashboard. You are able to check API Key and RPC URL. Click to copy the RPC URL of Rinkeby test network (the URL includes API Key)

![](<../.gitbook/assets/Frame 12\_2.png>)

### Getting Metamask Private Key

We need to add the account on a hardhat configuration to use for deploying the contract. To access the wallet, your private key should be injected. Note again, be careful with your private key, it gives access to your wallet and will spend its testnet Ether to deploy the contract.

![](<../.gitbook/assets/Frame 19-1.png>)

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

ALLTHATNODE_API_URL="copy and paste your rinkeby api url here"
PRIVATE_KEY="input your private key here"
```

> Please note that .env file should not be revealed to anywhere (e.g. push it to GitHub)

3\. Any file that loads the `.env` file by placing at the top will have access to the variables in that file by using `process.env`which implies `hardhat.config.js` will now work and load the `.env` variables and values correctly.

```javascript
// hardhat.config.js

require('dotenv').config();
```

### Deploy to Rinkeby testnet network&#x20;

Finally, run the following command. If everything went well, you should see the deployed address.

```
npx hardhat run scripts/deploy.js --network rinkeby
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
    rinkeby: {
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

ALLTHATNODE_API_URL="copy and paste your rinkeby api url here"
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
    rinkeby: {
      url: `${ALLTHATNODE_API_URL}`,
      accounts: [`${PRIVATE_KEY}`]
    }
  },
  etherscan: {
    apiKey: `${ETHERSCAN_APIKEY}`
  }
};
```

We now have everything we need to validate our smart contract, having accomplished all of the previous processes of building a smart contract, a deployment script, and modifying the config file. Let's run following command to deploy our contract on the Rinkeby test network.

You should designate which network to be deployed on after `--network` flag. The name should be pre-declared on the networks property at `hardhat.config.js`.

```
npx hardhat verify YOUR_CONTRACT_ADDRESS --network rinkeby
```

## Step 8: See your collection on OpenSea

The NFTs you just created will be available on OpenSea's Testnet. Navigate to [testnets.opensea.io](https://testnets.opensea.io/). Search for your contract address, which is the location we deployed to and can be found in your terminal. Click the collection itself when it appears in the search results.

If your NFTs aren't appearing on OpenSea, wait a few minutes; OpenSea might take up to 5-minutes. As an alternative to OpenSea, you may utilize Rarible. Rarible, like OpenSea, is an NFT marketplace. Go to rinkeby.rarible.com and generate your url as shown below.&#x20;

```
https://rinkeby.rarible.com/token/INSERT DEPLOY CONTRACT ADDRESS HERE:INSERT TOKEN ID HERE
```

Your tokenId is expected to be zero since it was the first to be minted under that contract. If you don't see your NFT on OpenSea after a few minutes, try Rarible and Rarible URLs as an alternative.

## That's It! What's next?

That's all there is to it; congrats! With Hardhat and AllThatNode, you've created, deployed, and validated your own ERC721 smart contract!

You may use the same contract code on AllThatNode to deploy it on any other EVM-compatible chains, such as [Polygon](https://www.allthatnode.com/polygon.dsrv) and [Avalanche](https://www.allthatnode.com/avalanche.dsrv), in the same way you did on the Ethereum test network.\
