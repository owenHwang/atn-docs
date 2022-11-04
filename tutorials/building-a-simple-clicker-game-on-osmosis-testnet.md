# Building a Simple Clicker Game on Osmosis Testnet

This tutorial introduces you to interact with All That Node product to deploy Wasm smart contract to Osmosis Testnet (`osmo-test-4`), and to create a simple clicker game. You might be able to test the things that we are going to build on the [following deployed site](https://yoon-suji.github.io/cosmwasm-clicker-game/).

![A full screenshot of Clicker Game (1)](<../.gitbook/assets/image (19).png>)

![A full screenshot of Clicker Game (2)](../.gitbook/assets/2022-07-01\_6.01.48.png)

![A full screenshot of Clicker Game (3)](../.gitbook/assets/2022-07-01\_1.54.09.png)

#### Prerequisites

* Sign up to All That Node (ATN) and secure your account
* Download your own IDE - recommend [Visual Studio Code](https://code.visualstudio.com/)
* Install `Git` on your computer
* install `[rustup](<https://rustup.rs/>)`

### Step 0: Setting up your environments

#### Set up Rust

Rust is the main programming language used for CosmWasm smart contracts. While WASM smart contracts can theoretically be written in any programming language, CosmWasm libraries and tooling work best with Rust.

First, [install rustup](https://rustup.rs/).

Then run the following commands:

```bash
# 1. Set 'stable' as the default release channel:

rustup default stable

# 2. Add WASM as the compilation target:

rustup target add wasm32-unknown-unknown

# 3. Install the following packages to generate the contract:

cargo install cargo-generate --features vendored-openssl
cargo install cargo-run-script
```

#### Setup Osmosis Testnet

You can easily set up an Osmosis Testnet environment using the [Osmosis Installer](https://github.com/osmosis-labs/osmosis-installer).

![](<../.gitbook/assets/스크린샷 2022-05-19 오후 3.13.44 (1).png>)

![](<../.gitbook/assets/스크린샷 2022-05-19 오후 3.14.10.png>)

![](<../.gitbook/assets/스크린샷 2022-05-19 오후 3.19.05.png>)

Run the following and choose option #2 (Client Node) and #2 (Testnet) in order.

```bash
curl -sL <https://get.osmosis.zone/install> > i.py && python3 i.py
```

Now you have successfully completed setting up an Osmosis client node in Testnet. In order to use `osmosisd` from the cli, either reload your terminal or refresh your profile with : `‘source ~/.profile’`

***

### Step 1: Faucet - Fund your Osmosis Account

#### Create Wallet

To begin, use the following command to generate a wallet for deployment.

```bash
osmosisd keys add wallet
```

#### Faucet using AllThatNode

![using Osmosis faucet provided by ATN](<../.gitbook/assets/스크린샷 2022-06-20 오후 2.30.38.png>)

To receive a free airdrop from Osmosis Testnet for testing purposes, you must first join Osmosis Discord. [Link](https://www.allthatnode.com/faucet/osmosis.dsrv) Meanwhile, utilizing the AllThatNode faucet makes your developer life much easier. Go to this link, enter your wallet address, and then click the Claim Your Tokens button. If you succeed, you may be able to obtain a transaction value.

The address of the wallet can be found through the `osmosisd keys show -a wallet` .

After requesting the faucet, use the command below to check the balance.

```bash
osmosisd query bank balances $(osmosisd keys show -a wallet)
```

### Step 2: Compile a WebAssembly code

#### Clone repository

We'll use a straightforward counter contract code. The code is kept in the following [repository](https://github.com/DSRV-DevGuild/cosmwasm-clicker-game).

Let's download the code with the following command:

```bash
cargo generate --git <https://github.com/DSRV-DevGuild/cw-template> --name my-first-contract
cd my-first-contract
```

#### Compile the wasm contract with stable toolchain

To deploy smart contracts, you must compile the code and make it an executable wasm binary file. We will compile the wasm contract with stable toolchain.

Compile using the command below:

```bash
# Set 'stable' as the default release channel:
rustup default stable
cargo wasm
```

After this compiles, it should produce a file in `target/wasm32-unknown-unknown/release/my_first_contract.wasm`. If you check the size of the file by using the `ls -lh` command, it shows around `1.8M`. This is a release build, but not stripped of all unneeded code. To produce a much smaller version, you can run this which tells the compiler to strip all unused code out:

```bash
RUSTFLAGS='-C link-arg=-s' cargo wasm
```

This produces a file about `155K`. To reduce gas costs, the binary size should be as small as possible. This will result in a less costly deployment, and lower fees on every interaction.

Also, if you don’t use compilation optimization, CosmWasm smart contract will not be deployed well due to `exceeds limit` error.

#### Optimized Compilation

You can do further optimization using [rust-optimizer](https://github.com/CosmWasm/rust-optimizer). **rust-optimizer** produces reproducible builds of CosmWasm smart contracts and does heavy optimization on the build size, using binary stripping and `wasm-opt`.

```bash
sudo docker run --rm -v "$(pwd)":/code \\
    --mount type=volume,source="$(basename "$(pwd)")_cache",target=/code/target \\
    --mount type=volume,source=registry_cache,target=/usr/local/cargo/registry \\
    cosmwasm/rust-optimizer:0.12.6
```

Binary file will be at `artifacts/my_first_contract.wasm` folder and its size will be about `130K`, which is more smaller than when only RUTFLAGS was used.

### Step 3: Deploying a contract

#### Uploading a binary code

We require the RPC Endpoint address of the Osmosis Testnet in order to distribute the produced Wasm binary code, and we will utilize the reliable RPC endpoint given by All That Node (ATN).

To begin, navigate to the protocol's Osmosis page and choose **New Project** to establish the project that will get the API key.

![](<../.gitbook/assets/스크린샷 2022-06-20 오후 3.33.55.png>)

![](<../.gitbook/assets/스크린샷 2022-06-20 오후 3.34.19.png>)

![](<../.gitbook/assets/스크린샷 2022-06-20 오후 3.34.26.png>)

Then you can see the projects on **DASHBOARD** that you have just created. To enter, click the Osmosis tab.

![](<../.gitbook/assets/스크린샷 2022-06-20 오후 3.42.50.png>)

The API key and Testnet endpoint may then be verified as follows:

![](<../.gitbook/assets/image (20).png>)

The `$NODE` variable contains the RPC endpoint address of the Osmosis Testnet for ease of deployment, and the `$TXFLAG` variable saves the following gas cost information: At this stage, you must copy and paste your API keys after the RPC endpoint location.

```bash
# bash
export NODE="--node <https://osmosis-testnet-rpc.allthatnode.com:26657/>{API KEY}"
export TXFLAG="${NODE} --chain-id osmo-test-4 --gas-prices 0.025uosmo --gas auto --gas-adjustment 1.3"

# zsh
export NODE=(--node <https://osmosis-testnet-rpc.allthatnode.com:26657/>{API KEY})
export TXFLAG=($NODE --chain-id osmo-test-4 --gas-prices 0.025uosmo --gas auto --gas-adjustment 1.3)
```

Now, post the code to the chain and use the following command to extract the `CODE_ID`: If the `$CODE_ID` value is logged normally, the upload was successful.

```bash
RES=$(osmosisd tx wasm store artifacts/my_first_contract.wasm --from wallet $TXFLAG -y --output json -b block)

CODE_ID=$(echo $RES | jq -r '.logs[0].events[-1].attributes[0].value')
echo $CODE_ID
```

#### Instantiate a new contract

In Osmosis Testnet, there are two ways to establish a contract instance: using `osmosisd` or using the GUI at [https://osmosis-contracts.web.app/](https://osmosis-contracts.web.app/).

We're going to use `osmosisd`. To create an instance of a contract, set the initial state and run the instantiate command.

```bash
INIT='{"count":2}'

osmosisd tx wasm instantiate $CODE_ID "$INIT" \\
    --from wallet --label "my first contract" $TXFLAG -y --no-admin
```

If the run was successful, you can check the deployment in Osmosis Explorer by searching for the output `txhash` value.

As a result of looking for transactions in Osmosis Explorer using hash values.

![As a result of looking for transactions in Osmosis Explorer](../.gitbook/assets/스크린샷\(743\).png)

### Step 4: Execute a contract

Let us now test how well the contract we works without any hurdles. To begin, use the command below to obtain the address of the deployed contract.

```bash
CONTRACT=$(osmosisd query wasm list-contract-by-code $CODE_ID --output json | jq -r '.contracts[0]')
echo $CONTRACT
```

#### get\_count

If you use the get count query to examine the value, you will see the original state `{"data":{"count":2}}` written in its entirety.

```bash
QUERY='{"get_count":{}}'
osmosisd query wasm contract-state smart $CONTRACT "$QUERY" --output json
```

#### increment

By running the `get_count` query again after the transaction below has failed, you can see that the value has increased by one from the previous count value.

```bash
TRY_INCREMENT='{"increment": {"count": 1}}'
osmosisd tx wasm execute $CONTRACT "$TRY_INCREMENT" --from wallet $TXFLAG -y
```

#### reset

After the transaction below is lost, check the value again through the `get_count` query to confirm that the count value has been reset to the specified value.

```bash
RESET='{"reset": {"count": 123}}'
osmosisd tx wasm execute $CONTRACT "$RESET" --from wallet $TXFLAG -y
```

***

### Step 5: Communicate with frontend

Let's now look at how to communicate smart contracts placed on the Osmosis Testnet using CosmJS on the front end via a simple Clicker game.

The Clicker game is a basic game in which you click the **CosmWasm** symbol that appears on the screen for 15 seconds to get a score, and then you drop a transaction to the contract to record the score once the game is done.

#### Clone repository

You may play the game yourself by inspecting the completed code in the Step 3 branch of the repo below. Check this medium article (warning! in Korean) contains a full discussion of each implementation phase.

```bash
git clone https://github.com/DSRV-DevGuild/osmosis-clicker-game.git
cd cosmwasm-clicker-game
git checkout Step3
yarn install && yarn start
```

#### Connecting Keplr Wallet

The Keplr wallet is a wallet that supports the Cosmos ecosystem's interchain.

[Keplr Wallet](https://chrome.google.com/webstore/detail/keplr/dmkamcknogkgcdfhhbddcghachkejeap?hl=en) Let's get started by installing the extension and making an account. By default, there is no test net on the linked network when you launch the Keplr wallet. To add a network that is not available by default, you must call a separate method at the frontend, pass the network's _configuration_ value as an argument, and then request addition.

_src/wallet/connect.js_ contains the code for adding a network to the Keplr wallet.

Check the keplr object to determine if the extension is installed, then connect to the Osmosis Testnet network using the `window.keplr.experimentalSuggestChain` function. You may now obtain network information after adding a network to your Keplr wallet.

The `window.keplr.enable(chainId:string)` function allows the website to request access to the wallet from Keplr for user authorization, and then collect the wallet's detailed information to generate the Client.

Finally, provide the wallet's information value to the parent component that ran the method `connectWallet`. When React.js delivers a value from a child component to a parent, the parent can drop the function to props, and the child can pass the value to a function factor. The `getInfo` method may be found in _src/App.js_.

```jsx
// src/wallet/connect.js
import { SigningCosmWasmClient } from "@cosmjs/cosmwasm-stargate";

const connectWallet = async (chainInfo, { getInfo }) => {
  // verify whether Keplr extension is installed on user's web browser
  if (!window.getOfflineSigner || !window.keplr) {
    alert("Please install keplr extension");
  }
  // Keplr wallet to be added on network
  if (window.keplr.experimentalSuggestChain) {
    try {
      await window.keplr.experimentalSuggestChain(chainInfo);
    } catch {
      alert("Failed to suggest the chain");
    }
  } else {
    alert("Please use the recent version of keplr extension");
  }
  // to request Keplr wallet to access into chainId
  await window.keplr.enable(chainInfo.chainId);
  // retreive OfflineSigner using chainId
  const offlineSigner = window.getOfflineSigner(chainInfo.chainId);
  // return address & public key pair array
  const accounts = await offlineSigner.getAccounts();
  // SigningCosmWasmClient object creating
  const client = await SigningCosmWasmClient.connectWithSigner(
    chainInfo.rpc,
    offlineSigner
  );
  // getting a balance
  const balance = await client.getBalance(
    accounts[0].address,
    chainInfo.stakeCurrency.coinMinimalDenom
  );
  // a function to pass values to parent component
  getInfo(client, accounts[0].address, balance, chainInfo.chainId);
};

export default connectWallet;
```

`ChainInfo` that must be passed as a factor in `window.keplr.experimentalSuggestChain` can be found in `src/wallet/network_info.js`. This information is required to be communicated except that the Optional annotation has been processed, otherwise an error will occur.

```jsx
// factory pattern
const chainInfo = (chainId, chainName, rpc, rest, coinDenom, coinMinimaldenom, coinDecimals, bech32) => {
    return {
        // chain Id
        chainId: chainId,
        // chain Name
        chainName: chainName,
        // chain RPC endpoint address
        rpc: rpc,
        // chain REST endpoint address
        rest: rest,
        // staking coin info
        stakeCurrency: {
            // denomination
            coinDenom: coinDenom,
            // uatom, uosmo
            coinMinimalDenom: coinMinimaldenom,
            // coin decimals
            coinDecimals: coinDecimals,
        },
        // BIP44 paths
        bip44: {
            // BIP44 standard
            // 'purpose' to fbe fixed as 44
            // 'coinType' to use 118 for Cosmos Hub
            coinType: 118,
        },
        // Bech32 information
        bech32Config: {
            bech32PrefixAccAddr: bech32,
            bech32PrefixAccPub: bech32 + "pub",
            bech32PrefixValAddr: bech32 + "valoper",
            bech32PrefixValPub: bech32 + "valoperpub",
            bech32PrefixConsAddr: bech32 + "valcons",
            bech32PrefixConsPub: bech32 + "valconspub"
        },
        // all coins/tokens list
        currencies: [{
            // denomination
            coinDenom: coinDenom,
            // coin minimal denomination
            coinMinimalDenom: coinMinimaldenom,
            // coin decimals
            coinDecimals: coinDecimals,
        }],
        // tokens to be paid as fee list
        feeCurrencies: [{
            // denomination
            coinDenom: coinDenom,
            // coin minimal denomination
            coinMinimalDenom: coinMinimaldenom,
            // coin decimals
            coinDecimals: coinDecimals,
        }],
				// (Optional) Information used only to import addresses from ENS should match the coinType in BIP44        coinType: 118,
        // Set (low: 0.01, average: 0.025, high: 0.04) to default unless otherwise specified
        // Keplr does not yet support dynamic calculations based on on on-chain data
        // It should be higher than the minimum gas price set by the RPC/REST endpoints and the validators in the chain.
        gasPriceStep: {
            low: 0.01,
            average: 0.05,
            high: 0.25
        }
    }
}

const networkInfo = {
    "malaga-420" : chainInfo("malaga-420", "Malaga", "<https://rpc.malaga-420.cosmwasm.com:443>", "<https://api.malaga-420.cosmwasm.com>", "Málaga", "umlg", 6, "wasm"),
    "osmo-test-4" : chainInfo("osmo-test-4", "Osmosis Testnet", "<https://testnet-rpc.osmosis.zone>", "<https://testnet-rest.osmosis.zone/>", "OSMO", "uosmo", 6, "osmo"),
    "uni-3" : chainInfo("uni-3", "Juno Testnet", "<https://rpc.uni.junonetwork.io:443>", "<https://api.uni.junonetwork.io/>", "JUNOX", "ujunox", 6, "juno"),
    "constantine-1" : chainInfo("constantine-1", "Archway Testnet", "<https://rpc.constantine-1.archway.tech:443>", "<https://api.constantine-1.archway.tech>", "CONST", "uconst", 6, "archway")
}

export default networkInfo;
```

_src/App.js_ implements the Network Connection button on the main screen.

When you click the **Osmosis Testnet** button, it changes to **DISCONNECT** and a **PLAY** button is generated to take you to the gameplay screen, which displays the linked wallet's address and balance underneath.

_App.js_ manages the _client, address, balance, chainId_ state with `useState`, and when using the connectWallet function, give over the `getInfo` function along with the factor and store it with `setState`.

```jsx
import "./App.css";
import { useState } from "react";
import { useNavigate } from "react-router-dom";
import networkInfo from "./wallet/network_info";
import connectWallet from "./wallet/connect";

function App() {
  // the value from connectWallet
  const [client, setClient] = useState();
  const [address, setAddress] = useState();
  const [balance, setBalance] = useState();
  const [chainId, setChainId] = useState();
  // the variable from visibility properties in PLAY button
  const [visible, setVisible] = useState("hidden");
  const navigate = useNavigate();

  // tehe function to pass to connectWallet method
  const getInfo = (client, address, balance, chainId) => {
    setClient(client);
    setAddress(address);
    setBalance(balance);
    setChainId(chainId);
    setVisible("visible");
  };

  // initialize the information given by connectWallet method
  const disconnect = (event) => {
    setClient();
    setChainId();
    setAddress();
    setBalance();
    setVisible("hidden");
  };

  // Implement DISCONNECT and CONNECT buttons for each network based on chainId.
  const renderBtn = () => {
    return Object.keys(networkInfo).map((id) => {
      if (chainId === id) {
        return (
          <button
            type="button"
            onClick={(event) => disconnect(event)}
            className="disconnect-btn"
          >
            DISCONNECT
          </button>
        );
      }
      return (
        <button
          type="button"
          onClick={(event) =>
            connectWallet(event, networkInfo[id], { getInfo })
          }
          className="connect-btn"
        >
          {networkInfo[id].chainName}
        </button>
      );
    });
  };

  // If the website is linked to a wallet, print out the address and balance.
  const showWalletInfo = () => {
    if (client) {
      return (
        <div className="wallet-info">
          <p>{`address: ${address}`}</p>
          <p>{`balance: ${balance.amount} ${balance.denom}`}</p>
        </div>
      );
    }
  };

  // navigate to /play when clicked
  const playGame = () => {
    return (
      <div className="menu">
        <button
          className="play-btn"
          onClick={() => {
            navigate("/play", {
              state: {
                address: address,
                denom: balance.denom,
                chainId: chainId
              }
            });
          }}
          style={{ visibility: visible }}
        >
          <span>PLAY</span>
        </button>
        {!client && <p>Choose your network and Connect wallet</p>}
        {client && (
          <p>Click as many CosmWasm Icon as you can within 15 seconds!</p>
        )}
      </div>
    );
  };

  return (
    <div className="App">
      <header>
        <div className="header-titles">
          <img
            alt="Cosmwasm Logo"
            className="cosmwasm-logo"
            src="/cosmwasm-logo.svg"
          />
          <h1>Clicker Game</h1>
        </div>
      </header>
      <div className="App-container">
        <div className="App-menu-container">
          {playGame()}
          <div className="connect-wallet">{renderBtn()}</div>
        </div>
        {showWalletInfo()}
      </div>
    </div>
  );
}

export default App;
```

#### Communicate with a deployed contract

You can find the address of the contract we published to Osmosis Testnet previously in the _src/contract/address.js_ file.

```jsx
const contractAddress = {
  "malaga-420":
    "wasm1v8484th79cv2vh49sq949auu20yla3jh7rypzytp50quyly552vs3a4ugd",
  "osmo-test-4":
    "osmo1sm8weyvz7ues2mx9eg6rnqu9yazjdwru5p6u7u0jkhgmk6vqt8equ8t5xp",
  "uni-3": "juno1yfp9zyx9zhqe77d05yqjx3ctqjhzha0xn5d9x8zxcpp658ks2hvqlfjt72",
  "constantine-1":
    "archway1wnuakyjhvlnepk2g9ncvvaks0zy0axgx70pet4jh2nv8lmsuff9qseuvpc"
};

export default contractAddress;
```

To query CosmJS, use the `queryContractSmart()` function. To conduct the query, the method is sent with the contract's address and message as a factor, and the resultant count number may be obtained using result.count. The code that fires the get count query can be found in _src/contract/get\_count.js_.

```jsx
import contractAddress from "./address";

const get_count = async (client, chainId) => {
    const result = await client.queryContractSmart(contractAddress[chainId], {"get_count": {}});
    return result;
}

export default get_count;
```

Because the `reset` and `increment` transactions modify the internal state of the contract, you must pay the gas cost.

You may execute a transaction by sending the `execute()` method along with the wallet address to pay for the gas, the contract address, the message, and the gas cost as a component. _src/contract/reset.js_ contains the code that sends the reset transaction.

```jsx
import { calculateFee, GasPrice } from "@cosmjs/stargate";
import contractAddress from "./address";

const reset = async (client, address, score, chainId, denom) => {
  const gasPrice = GasPrice.fromString("0.025" + denom);
  const executeFee = calculateFee(300_000, gasPrice);
  const result = await client.execute(
    address,
    contractAddress[chainId],
    { reset: { count: score } },
    executeFee
  );
  return result;
};

export default reset;
```

#### Clicker Game Implementation

We previously used _src/App.js_ to send the play button to the `/play` location.

First, add the router from the _src/index.js_ file so that when you connect to the `/play` URL, the play screen shows.

```jsx
const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(
  <React.StrictMode>
    <div className="App-header">
      <BrowserRouter>
        <Routes>
          <Route path="/" element={<App />} />
          <Route path="/play" element={<Play />} />
        </Routes>
      </BrowserRouter>

      <div className="footer-container">
        <span>Made with</span>
        <img src="./dsrv.png" id="footer-logo" alt="dsrv-logo"></img>
      </div>
    </div>
  </React.StrictMode>
);
```

`src/pages/play.js` implements the play screen that shows when you connect to the `/play` location. The final play page that we will use is as follows.

![](<../.gitbook/assets/스크린샷 2022-06-16 오전 10.28.52.png>)

The previous and current scores are displayed in the upper left corner, while the time remaining is displayed in the top right corner. In the center, there is a **GAME START** button, which turns to **TRANSACTION** after the game is over.

The symbol exists in the game container, appears at the start of the game, and then disappears. While the transaction is ongoing, a loading message is displayed.

```jsx
  // The game begins before the game begins, and the TRANSACTION button appears after the game concludes.
  const renderButton = () => {
    if (gameOver === false) {
      return (
        <button className="game-btn" onClick={(event) => startGame(event)}>
          GAME START
        </button>
      );
    } else {
      return (
        <button className="game-btn" onClick={(event) => submitScore(event)}>
          TRANSACTION
        </button>
      );
    }
  };
```

When the **GAME START** button is pushed, the `count` value acquired by calling the `get_count` function is shown in **Previous Score**, and the `reset` method is called to reset the contract's 'count' value to zero.

To communicate with the smart contract, you must first have `client`. When the screen is first shown using the `useEffect` function, use the `chainId` information from the `App.js` screen to connect to the wallet and construct 'client'. To use the information supplied from `App.js` to `state`, you must use the 'useLocation' function.

The function `SigningCosmWasmClient.connectWithSigner()` returns the [_SigningCosmWasmClient_](https://cosmos.github.io/cosmjs/latest/cosmwasm-stargate/classes/SigningCosmWasmClient.html) with the RPC endpoint address and _OfflineSigner_ as a factor retrieved from Keplr. The 'client' serves as an interface with the network.

```jsx
const location = useLocation();

// when page is rendered, the client object is created and saved
useEffect(() => {
    const getClient = async (chainId) => {
        // request access to Keplr wallet on the chainId 
        await window.keplr.enable(chainId);
				// using chainId to retreive OfflineSigner
        const offlineSigner = window.getOfflineSigner(chainId);
        // SigningCosmWasmClient 생성
        const client = await SigningCosmWasmClient.connectWithSigner(
            networkInfo[chainId].rpc,
            offlineSigner
        );
        setClient(client);
    };
    getClient(location.state.chainId);
}, []);
```

When the **GAME START** button is pushed, the startGame function reads the contract's `count` value using the previously created `get_count` method and puts it in the `previousScore`. Then, using the `reset` function, change the contract's `count` value to zero.

Begin the game after communicating with the contract. When the game begins, the `time` setting of 15 seconds should be reduced by one second each second. To implement the feature, use the `setInterval` method.

```jsx
// Execute when Game Start button is clicked
const startGame = async(event) => {
    // set loading status to true when communicating with a contract
    setLoading(true);
    // execute get_count query to retreive contract's count value
    const result = await get_count(client, location.state.chainId);
    // save count value retrieved from preiousScore
    setPreviousScore(result.count);
    // execute reset transaction to initialize count value to 0
    await reset(client, location.state.address, 0, location.state.chainId, location.state.denom);
    // set loading status to false after communicating with a contract
    setLoading(false);
    // intiialize true to Game Start value before starting a game
    setGameStart(true);
    // set a location to show up icons
    setTargetPosition({ top: "20%", left: "50%" });
    // Use the setInterval method to reduce time by 1 per second
    setTimerId(
        setInterval(() => {
            setTime((time) => (time > 0 ? time - 1 : 0));
        }, 1000)
    );
}
```

The next time you click the CosmWasm symbol that displays when the game starts, your score will be increased by one and the technique will be executed to randomize the next location. And let's make the game stop after all 15 seconds have passed and the clock reaches zero.

Set the icon's location in a randomized fashion by utilizing the `setTargetPosition` and `Math.random` methods and increasing the current score by one.

```jsx
  // A function that run when you click the CosmWasm icon
  const handleClick = () => {
    // increment current score by 1
    setScore((score) => score + 1);
    // Random set to the following position on the icon.
    setTargetPosition({
      top: `${Math.floor(Math.random() * 80 + 10)}%`,
      left: `${Math.floor(Math.random() * 80) + 10}%`
    });
  };
```

Using the `useEffect` function that detects a change in the `time` value, set the icon to disappear when `time` goes to zero and display the game end alarm window.

And use the `clearInterval` method to stop the continuously running 'setInterval' function

```jsx
// play.js (added)
// End the game when time changes and becomes zero
useEffect(() => {
    if (time === 0) {
    // Icon is not disabled.
    setTargetPosition({ display: "none" });
    // Game Exit allamchang.
    alert(
        `Game Over! Your score is ${score}. Please confirm transaction to submit score.`
    );
    // setInterval function just halted
    clearInterval(timerId);
    setGameOver(true);
    setGameStart(false);
    }
}, [time]);
```

Create the submitScore method, which is called when you click the **TRANSACTION** button after the previous game has finished. Run `increment` as many times as the user's score, and after the `increment` transaction is complete, read the contract's `count` value again through the `get_count` function and update it to `previousScore`.

Since the contract's `count` value was reset to zero in the preceding requirement No. 2, the contract's `count` value is the score acquired by the user when the `increment` method is called.

After all contact with the contract has been completed, set the `gameOver` value to `false` and the zeroed `time` value back to 15 seconds to allow the game to be continued.

```jsx
// Run when the Transaction button is pressed
const submitScore = async (event) => {
  // Set loading status to true while communicating with the contract
  setLoading(true);
	// Execute the increment transaction by the score obtained by the user to change the count value of the contract to score
  await increment(
    client,
    location.state.address,
    score,
    location.state.chainId,
    location.state.denom
  );
  // Initialize with current score of 0
  setScore(0);
	// Read the count value stored in the contract through the get_count query and update to the Previous Score
  const result = await get_count(client, location.state.chainId);
  setPreviousScore(result.count);
	// Set loading status to false after communication with contract
  setLoading(false);
  // Set the game to restart
  setGameOver(false);
  setTime(playTime);
};
```

The whole code may be obtained in [this repository](https://github.com/DSRV-DevGuild/cosmwasm-clicker-game/tree/Step3).

You can now use AllThatNode and CosmJS to publish Wasm Smart Contracts on the Osmosis Testnet and interface with Smart Contracts deployed on the front end through a simple clicker game.
