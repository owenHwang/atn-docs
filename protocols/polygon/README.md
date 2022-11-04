---
description: Below you can find the endpoints and the samples
cover: ../../.gitbook/assets/polygon_docs.png
coverY: 0
---

# Polygon

_Polygon is a platform and framework, built to support and scale Ethereum-compatible blockchains by offering a suite of L2 scaling solutions like zk-rollups, plasma, sidechains and more._



For more information on Polygon APIs, see the [_**official documentation**_](https://docs.polygon.technology/).



Polygon Official Website : [https://polygon.technology/](https://polygon.technology/)

Polygon Official Document :[https://docs.polygon.technology/](https://docs.polygon.technology/)

Polygon Github : [https://github.com/maticnetwork/matic-docs](https://github.com/maticnetwork/matic-docs)



If you don't have the API key, [_**Create New Polygon Project**_](https://www.allthatnode.com/nodes.dsrv?protocol=polygon).



## Polygon RPC Endpoints

#### Mainnet

* JSON RPC _(Bor)_:\
  `https://polygon-mainnet-rpc.allthatnode.com:8545/'YOUR-API-KEY'`
* REST API: \
  `https://polygon-mainnet-rpc.allthatnode.com:1317 \`\
  `--header "x-allthatnode-api-key: 'YOUR-API-KEY'"`
* Tendermint RPC: \
  `https://polygon-mainnet-rpc.allthatnode.com:26657/'YOUR-API-KEY'`

#### Mumbai (Testnet)

* JSON RPC _(Bor)_:\
  `https://polygon-testnet-rpc.allthatnode.com:8545/'YOUR-API-KEY'`
* REST API:\
  `https://polygon-testnet-rpc.allthatnode.com:1317 \`\
  `--header "x-allthatnode-api-key: 'YOUR-API-KEY'"`
* Tendermint RPC: \
  `https://polygon-testnet-rpc.allthatnode.com:26657/'YOUR-API-KEY'`



Find `'YOUR-API-KEY'` by going to the **** [_**Dashboard**_](https://www.allthatnode.com/dashboard.dsrv) **** menu (Dashboard > All Projects > Project Detail Page).

{% hint style="info" %}
Or you can use the public Polygon nodes without the API key. \
_(i.e._`https://polygon-mainnet-rpc.allthatnode.com:8545/`_)_

But Public endpoints are not intended for DApp building. Please use private / dedicated RPC servers when you launch your application, drop NFTs, etc.
{% endhint %}

{% hint style="warning" %}
**Put your ‘API-KEY’ with the endpoint in the correct place**(Check out the samples on the next page!).&#x20;

Otherwise, it means you are using the public endpoint we offer, therefore, we cannot count the API calls of your project nor make the request report for you.
{% endhint %}







## Polygon Samples







{% swagger method="post" path="" baseUrl="latestblock" summary="" %}
{% swagger-description %}

{% endswagger-description %}
{% endswagger %}

