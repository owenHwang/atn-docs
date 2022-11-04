---
description: Below you can find the endpoints and the samples
cover: ../../.gitbook/assets/axelar_docs.png
coverY: 0
---

# Axelar

_Axelar is a decentralized interoperability network connecting all blockchains, assets and apps through a universal set of protocols and APIs._



For more information on Axelar APIs, see the [official documentation](https://docs.axelar.dev/).

## Axelar RPC Endpoints

#### Mainnet

* REST API _(LCD)_: \
  `https://axelar-mainnet-rpc.allthatnode.com:1317 \`\
  `--header "x-allthatnode-api-key: 'YOUR-API-KEY'"`
* Tendermint RPC _(RPC)_: \
  `https://axelar-mainnet-rpc.allthatnode.com:26657/'YOUR-API-KEY'`

#### Casablanca

* REST API _(LCD)_:\
  `https://axelar-casablanca-rpc.allthatnode.com:1317 \`\
  `--header "x-allthatnode-api-key: 'YOUR-API-KEY'"`
* Tendermint RPC _(RPC)_: \
  `https://axelar-casablanca-rpc.allthatnode.com:26657/'YOUR-API-KEY'`

#### Lisbon

* REST API _(LCD)_:\
  `https://axelar-lisbon-rpc.allthatnode.com:1317 \`\
  `--header "x-allthatnode-api-key: 'YOUR-API-KEY'"`
* Tendermint RPC _(RPC)_: \
  `https://axelar-lisbon-rpc.allthatnode.com:26657/'YOUR-API-KEY'`



Find `'YOUR-API-KEY'` by going to the **** [_**Dashboard**_](https://www.allthatnode.com/dashboard.dsrv) **** menu (Dashboard > All Projects > Project Detail Page).

{% hint style="info" %}
Or you can use the public Axelar nodes without the API key. \
_(i.e._`https://axelar-mainnet-rpc.allthatnode.com:1317/`_)_

But Public endpoints are not intended for DApp building. Please use private / dedicated RPC servers when you launch your application, drop NFTs, etc.
{% endhint %}

{% hint style="warning" %}
**Put your ‘API-KEY’ with the endpoint in the correct place**(Check out the samples on the next page!).&#x20;

Otherwise, it means you are using the public endpoint we offer, therefore, we cannot count the API calls of your project nor make the request report for you.
{% endhint %}

