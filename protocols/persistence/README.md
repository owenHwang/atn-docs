---
description: Below you can find the endpoints and the samples
cover: ../../.gitbook/assets/persistence_docs.png
coverY: 0
---

# Persistence

_Persistence is a Tendermint-based interoperable protocol that powers an entire DeFi ecosystem. Thanks to the Persistence SDK, developers can build a number of multi-chain products that promote liquid staking._



For more information on Persistence APIs, see the [official documentation](https://github.com/persistenceOne/persistenceSDK#readme).

## Persistence RPC Endpoints

#### Mainnet

* REST API _(LCD)_: \
  `https://persistence-mainnet-rpc.allthatnode.com:1317 \`\
  `--header "x-allthatnode-api-key: 'YOUR-API-KEY'"`
* Tendermint RPC _(RPC)_: \
  `https://persistence-mainnet-rpc.allthatnode.com:26657/'YOUR-API-KEY'`

#### Testnet

* REST API _(LCD)_:\
  `https://persistence-testnet-rpc.allthatnode.com:1317 \`\
  `--header "x-allthatnode-api-key: 'YOUR-API-KEY'"`
* Tendermint RPC _(RPC)_: \
  `https://persistence-testnet-rpc.allthatnode.com:26657/'YOUR-API-KEY'`



Find `'YOUR-API-KEY'` by going to the **** [_**Dashboard**_](https://www.allthatnode.com/dashboard.dsrv) **** menu (Dashboard > All Projects > Project Detail Page).

{% hint style="info" %}
Or you can use the public Persistence nodes without the API key. \
_(i.e._`https://persistence-mainnet-rpc.allthatnode.com:1317/`_)_

But Public endpoints are not intended for DApp building. Please use private / dedicated RPC servers when you launch your application, drop NFTs, etc.
{% endhint %}

{% hint style="warning" %}
**Put your ‘API-KEY’ with the endpoint in the correct place**(Check out the samples on the next page!).&#x20;

Otherwise, it means you are using the public endpoint we offer, therefore, we cannot count the API calls of your project nor make the request report for you.
{% endhint %}

