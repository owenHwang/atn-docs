---
description: For more information on Polygon APIs, see the official documentation.
---

# Polygon Samples

## JSON RPC Samples

### eth\_syncing

Returns syncing status

#### Request

{% tabs %}
{% tab title="Curl" %}
```shell
curl https://polygon-mainnet-rpc.allthatnode.com:8545/'YOUR-API-KEY' \
-X POST \
-H "Content-Type: application/json" \
-d '{ "jsonrpc":"2.0", "method":"eth_syncing", "params":[], "id":1 }' 
```
{% endtab %}

{% tab title="Postman" %}
```json
URL: https://polygon-mainnet-rpc.allthetnode.com:8545/'YOUR-API-KEY'
RequestType: POST
Body: 
{
    "jsonrpc":"2.0",
    "method":"eth_syncing",
    "params":[],
    "id":1
}
```
{% endtab %}
{% endtabs %}

#### Response

```json
{
    "jsonrpc": "2.0",
    "result": false,
    "id": 1
}
```



### eth\_getBalance

Returns address balance

#### Request

{% tabs %}
{% tab title="Curl" %}
```shell
curl https://polygon-mainnet-rpc.allthatnode.com:8545/'YOUR-API-KEY' \
-X POST \
-H "Content-Type: application/json" \
-d '{ "jsonrpc":"2.0", "method":"eth_getBalance", "params":[ "0x829bd824b016326a401d083b33d092293333a831", "latest" ], "id":1 }'
```
{% endtab %}

{% tab title="Postman" %}
```json
URL: https://polygon-mainnet-rpc.allthetnode.com:8545/'YOUR-API-KEY'
RequestType: POST
Body: 
{
    "jsonrpc":"2.0",
    "method":"eth_getBalance",
    "params":[ "0x829bd824b016326a401d083b33d092293333a830", "latest" ],
    "id":1
}
```
{% endtab %}
{% endtabs %}

#### Response

```json
{
    "jsonrpc": "2.0",
    "result": "0x0",
    "id": 1
}
```



### eth\_blockNumber

Returns most recent block number

#### Request

{% tabs %}
{% tab title="Curl" %}
```shell
curl https://ethereum-mainnet-rpc.allthatnode.com/'YOUR-API-KEY' \
-X POST \
-H "Content-Type: application/json" \
-d '{"jsonrpc":"2.0","method":"eth_blockNumber","params":[],"id":1}'
```
{% endtab %}

{% tab title="Postman" %}
```json
URL: https://polygon-mainnet-rpc.allthetnode.com:8545/'YOUR-API-KEY'
RequestType: POST
Body: 
{
    "jsonrpc":"2.0",
    "method":"eth_blockNumber",
    "params":[],
    "id":1
}
```
{% endtab %}
{% endtabs %}

#### Response

```json
{
    "jsonrpc": "2.0",
    "result": "0xceda4c",
    "id": 1
}
```



## REST API Samples

### \[GET] /node\_info

The properties of the connected node

#### Request

{% tabs %}
{% tab title="Curl" %}
```shell
curl https://polygon-mainnet-rpc.allthatnode.com:1317/node_info \
--header "x-allthatnode-api-key: 'YOUR-API-KEY'"
```
{% endtab %}

{% tab title="Postman" %}

{% endtab %}
{% endtabs %}

Response

```json
{
  "node_info": {
    "protocol_version": {
      "p2p": "7",
      "block": "10",
      "app": "0"
    },
    "id": "368c7cd2b5175c6cf693b9d1033ca203ea1d2b94",
    "listen_addr": "tcp://0.0.0.0:26656",
    "network": "heimdall-137",
    "version": "0.32.7",
    "channels": "4020212223303800",
    "moniker": "atnrpc1",
    "other": {
      "tx_index": "on",
      "rpc_address": "tcp://0.0.0.0:26657"
    }
  },
  "application_version": {
    "name": "heimdall",
    "server_name": "heimdalld",
    "client_name": "heimdallcli",
    "version": "0.2.9",
    "commit": "7d44d4541cd36ec8c754bb3ed46ed0933e535ca2",
    "build_tags": "",
    "go": "go version go1.18.3 linux/amd64"
  }
}
```

