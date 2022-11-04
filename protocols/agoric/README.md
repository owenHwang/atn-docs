---
description: Below you can find the endpoints and the samples
cover: ../../.gitbook/assets/agoric_docs.png
coverY: 0
---

# Agoric

_Agoric is an open-source development company launching an interoperable PoS chain. Agoric’s JavaScript smart contract offers developers a safe, reusable library of DeFi components to rapidly build and deploy on-chain._



For more information on Agoric APIs, see the [official documentation](https://agoric.com/documentation/getting-started/beta.html#set-up-a-wallet-agoric-solo-machine).

## Agoric RPC Endpoints

#### Mainnet

* REST API _(LCD)_: \
  `https://agoric-mainnet-rpc.allthatnode.com:1317 \`\
  `--header "x-allthatnode-api-key: 'YOUR-API-KEY'"`
* Tendermint RPC _(RPC)_: \
  `https://agoric-mainnet-rpc.allthatnode.com:26657/'YOUR-API-KEY'`

#### Devnet

* REST API _(LCD)_:\
  `https://agoric-devnet-rpc.allthatnode.com:1317 \`\
  `--header "x-allthatnode-api-key: 'YOUR-API-KEY'"`
* Tendermint RPC _(RPC)_: \
  `https://agoric-devnet-rpc.allthatnode.com:26657/'YOUR-API-KEY'`



Find `'YOUR-API-KEY'` by going to the **** [_**Dashboard**_](https://www.allthatnode.com/dashboard.dsrv) **** menu (Dashboard > All Projects > Project Detail Page).

{% hint style="info" %}
Or you can use the public Agoric nodes without the API key. \
_(i.e._`https://agoric-mainnet-rpc.allthatnode.com:1317/`_)_

But Public endpoints are not intended for DApp building. Please use private / dedicated RPC servers when you launch your application, drop NFTs, etc.
{% endhint %}

{% hint style="warning" %}
**Put your ‘API-KEY’ with the endpoint in the correct place**(Check out the samples on the next page!).&#x20;

Otherwise, it means you are using the public endpoint we offer, therefore, we cannot count the API calls of your project nor make the request report for you.
{% endhint %}

