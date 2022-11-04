---
description: Below you can find the endpoints and samples
cover: ../../.gitbook/assets/terra_docs.png
coverY: 0
---

# Terra Classic

_Terra Classic is an open-source, decentralized PoS blockchain built using the Cosmos SDK and powered by the newly renamed Luna Classic (LUNC)._

__

For more information on Terra RPC APIs, see the [official documentation](https://fcd.terra.dev/swagger).

## Terra RPC Endpoints

#### Mainnet

* REST API _(LCD)_: \
  `https://terra-mainnet-rpc.allthatnode.com:1317 \`\
  `###--header "x-allthatnode-api-key: 'YOUR-API-KEY'"`
* Tendermint RPC _(RPC)_: \
  `https://terra-mainnet-rpc.allthatnode.com:26657/'YOUR-API-KEY'`

#### Bombay

* REST API _(LCD)_:\
  `https://terra-bombay-rpc.allthatnode.com:1317 \`\
  `--header "x-allthatnode-api-key: 'YOUR-API-KEY'"`
* Tendermint RPC _(RPC)_: \
  `https://terra-bombay-rpc.allthatnode.com:26657/'YOUR-API-KEY'`



Find `'YOUR-API-KEY'` by going to the **** [_**Dashboard**_](https://www.allthatnode.com/dashboard.dsrv) **** menu (Dashboard > All Projects > Project Detail Page).

{% hint style="info" %}
Or you can use the public Terra nodes without the API key. \
_(i.e._`https://terra-mainnet-rpc.allthatnode.com:1317/`_)_

But Public endpoints are not intended for DApp building. Please use private / dedicated RPC servers when you launch your application, drop NFTs, etc.
{% endhint %}

{% hint style="warning" %}
**Put your ‘API-KEY’ with the endpoint in the correct place**(Check out the samples on the next page!).&#x20;

Otherwise, it means you are using the public endpoint we offer, therefore, we cannot count the API calls of your project nor make the request report for you.
{% endhint %}

