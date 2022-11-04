---
description: >-
  This tutorial introduces you to how to write a smart contract for a
  fundraising application like Kickstarter or Wadiz using Solidity, on Ethereum
  Test Network.
---

# Building a fundraising contract on Ethereum

> The code snippets on the page are shown on [Nomad Coders](https://www.youtube.com/c/%EB%85%B8%EB%A7%88%EB%93%9C%EC%BD%94%EB%8D%94NomadCoders) - one of the well-known YouTube developer channels in Korea. You can find the video clip [here](https://www.youtube.com/watch?v=8WBvMEql6SQ) that explains while coding lively on a full display.

{% embed url="https://www.youtube.com/watch?v=8WBvMEql6SQ" %}

### Writing A Contract

In this tutorial, we are writing the fundraising contract that has the properties like the following.

* `owner` : The owner of the project is trying to fundraise, and suggesting the project.
* `targetAmount` : The amount of money the `owner` trying to raise ETH.
* `donations` : A list that maps the donator and how much they have donated in ETH. The `address` notes the person that donates to the project as an Ethereum wallet address. The ETH amount that a person invests in the project is stored as `uint256` type.
* `raisedAmount` : The accumulated total amount of all donations.
* `finishTime` : The amount of time the project to reach the target. We set 2 weeks for the fundraising period.

The specification of the fundraising contract is the following.

* If the total amount of donations is more or equal to the target amount, then all the funds in the contract will be transferred to the owner of the project.
* If the total amount of donations is less than the donation target then people inside of the donators list will be able to get a full refund.

```solidity
contract Fundraising {
    uint256 public targetAmount;
    address public owner;
    mapping(address => uint256) public donations;

    uint256 public raisedAmount = 0;
    uint256 public finishTime = block.timestamp + 2 weeks;

    constructor(uint256 _targetAmount) {
        targetAmount = _targetAmount;
        owner = msg.sender;
    }
    
    /*
        Create a function called receive and we have to say that it is external,
        which means it can only be called from outside of the contract.
        add the payable modifer to it to indicate that this can receive money.
    */
    receive() external payable {
        // `require` the block.timestamp which is a date, to be a smaller date than the finishTime of our contract.
        // if the block.timestamp is bigger, which means the current date is after the finishTime,
        // we will show an error that says "This campaign is over".
        require(block.timestamp < finishTime, "This campaign is over");
        
        // Using the global variable `msg.sender` to know who is sending money and `msg.value` to know how much they are sending
        // and we save this info in our mapping, with the sender as they key and the money amount as the value.
        donations[msg.sender] += msg.value;
        raisedAmount += msg.value;
    }
    
    
    /*
        `withdrawDonations` will check if the person calling this function is the same person that created this contract
        by checking the `msg.sender` with the owner set on the constructor, if they are not the same it will throw an error.
    */
    function withdrawDonations() external {
        require(msg.sender == owner, "Funds will only be released to the owner");
        
        // Let's check if the `raisedAmount` which is the donation counter, is more than or equals to the target of the campaing
        // and if it isn't let's throw an error using require again.
        require(raisedAmount >= targetAmount, "The project did not reach the goal");
        
        // If all these conditions are true, if the person calling withdrawDonations is the owner of the contract,
        // if the raised amount is more than the target amount, and if the campaign has finished we will release the funds to the owner.
        require(block.timestamp > finishTime, "The campaign is not over yet.");
        payable(owner).transfer(raisedAmount);
    }
    
    /*
        In the refund function we check to see if the campaign is over or now,
        if it is not over then the user won't be able to get a refund.
    */
    function refund() external {
        // If all the following conditions are true, if the campaign is over and it didn't reach the goal and if the user asking for the refund did donate to the campaign,
        // we will put the amount of donated money on a variable.
        require(block.timestamp > finishTime, "The campaign is not over yet.");
        require(raisedAmount < targetAmount, "The campaign reached the goal.");
        require(donations[msg.sender] > 0, "You did not donate to this campaign.");
        
        uint256 toRefund = donations[msg.sender];
        donations[msg.sender] = 0;
        // Then update our donations list, to make sure that the same user can't ask for a refund twice.
        payable(msg.sender).transfer(toRefund);
    }
}
```

### Deploying A Contract

Run the following on the terminal. You are expected to install `node` before running this command. If you would like to be guided with a more detailed explanation, see [here](https://docs.allthatnode.com/tutorials/a-simple-erc20-smart-contract).

```
npm init
npm install -D hardhat ethers @nomiclabs/hardhat-ethers @nomiclabs/hardhat-waffl
npx hardhat
```

Create `hardhat.config.js` on the root directory and write the following. You are required to get a free API Key on AllThatNode website. Remember the fact that you are required to get some test ETH on the [faucet](https://www.allthatnode.com/faucet/ethereum.dsrv). See a more detailed explanation [here](https://docs.allthatnode.com/tutorials/a-simple-erc20-smart-contract).

```solidity
require("@nomiclabs/hardhat-waffle");

module.exports = {
  solidity: "0.8.0",
  networks: {
   goerli: {
     url: "https://ethereum-goerli-rpc.allthatnode.com/mavG3o3f1fK9DinnMfI2tV2fkcuW3VQx",
   },
  },
};
```

Then, create a directory called `scripts` , make a file named `deploy.js` and write the following.

```solidity
async function main() {
  // Using 'ethers' which is a JavaScript library to interact with Ethereum,
  // we are grabbing the Fundraising contract, compiling it and then we are deploying it one argument.
  const Fundraising = await ethers.getContractFactory("Fundraising");
  // This is the argument that the constructor or our contract needs, the `targetAmount` of money that we want to raise in our campaign.
  const contract = await Fundraising.deploy(ethers.utils.parseEther("100.0"));
  console.log("Contract address is:", contract.address);
}

main()
  .then(() => process.exit(0))
  .catch((error) => {
    console.error(error);
    process.exit(1);
});
```

Run the following command on the terminal to deploy the contract to the goerli test network.

```
npx hardhat run scripts/deploy.js --network goerli
```

Let's check how contract receives ETH by checking the balance of it. For this we are going to create a new task in `hardhat.config.js`.

```solidity
task("check", "Check contract amounts", async () => {
  const [deployer] = await ethers.getSigners();
  const contract = "DEPLOYED_CONTRACT_HERE";
  const abi = [...]
  const fundraising = new ethers.Contract(address, abi, deployer);
  console.log(
    await fundraising.targetAmount(),
    await fundraising.raisedAmount()
  );
});
```

What we need is the `ABI` which is the Application Binary Interface. It is very similar to an `API` that we use to communicate with a server, we use the `ABI` to communicate with the binary contract.

To get the `ABI` of our contract we will go to the `artifacts` folder, then `contracts` and then `Fundraising.json`. There we will see the `abi` and as you can see it's a JSON description of our contract. We will copy paste this into our task.

```solidity
task("check", "Check contract amounts", async () => {
  const [deployer] = await ethers.getSigners();
  const contract = "DEPLOYED_CONTRACT_HERE";
+  const abi = [
+    {
+      inputs: [
+        {
+          internalType: "uint256",
+          name: "_targetAmount",
+          type: "uint256",
+        },
+      ],
+      stateMutability: "nonpayable",
+      type: "constructor",
+    },
+    {
+      inputs: [
+        {
+          internalType: "address",
+          name: "",
+          type: "address",
+        },
+      ],
+      name: "donations",
+      outputs: [
+        {
+          internalType: "uint256",
+          name: "",
+          type: "uint256",
+        },
+      ],
+      stateMutability: "view",
+      type: "function",
+    },
+    {
+      inputs: [],
+      name: "finishTime",
+      outputs: [
+        {
+          internalType: "uint256",
+          name: "",
+          type: "uint256",
+        },
+      ],
+      stateMutability: "view",
+      type: "function",
+    },
+    {
+      inputs: [],
+      name: "owner",
+      outputs: [
+        {
+          internalType: "address",
+          name: "",
+          type: "address",
+        },
+      ],
+      stateMutability: "view",
+      type: "function",
+    },
+    {
+      inputs: [],
+      name: "raisedAmount",
+      outputs: [
+        {
+          internalType: "uint256",
+          name: "",
+          type: "uint256",
+        },
+      ],
+      stateMutability: "view",
+      type: "function",
+    },
+    {
+      inputs: [],
+      name: "refund",
+      outputs: [],
+      stateMutability: "nonpayable",
+      type: "function",
+    },
+    {
+      inputs: [],
+      name: "targetAmount",
+      outputs: [
+        {
+          internalType: "uint256",
+          name: "",
+          type: "uint256",
+        },
+      ],
+      stateMutability: "view",
+      type: "function",
+    },
+    {
+      inputs: [],
+      name: "withdrawDonations",
+      outputs: [],
+      stateMutability: "nonpayable",
+      type: "function",
+    },
+    {
+      stateMutability: "payable",
+      type: "receive",
+    },
+  ];
    (... omited)
});
```

To run the task, enter the command on terminal like the following.

```
npx hardhat donate --network goerli
```
