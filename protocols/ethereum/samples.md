---
description: >-
  Ethereum nodes accept HTTP requests using the JSON-RPC 2.0 specification.For
  more information on Ethereum APIs, see the official documentation.
---

# Ethereum Samples

## eth\_syncing

Returns syncing status

#### Request

{% tabs %}
{% tab title="Curl" %}
```shell
curl https://ethereum-mainnet-rpc.allthatnode.com/'YOUR-API-KEY' \
-X POST \
-H "Content-Type: application/json" \
-d '{ "jsonrpc":"2.0", "method":"eth_syncing", "params":[], "id":1 }' 
```
{% endtab %}

{% tab title="Postman" %}
```json
URL: https://ethereum-mainnet-rpc.allthetnode.com/'YOUR-API-KEY'
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



## eth\_getBalance

Returns address balance

#### Request

{% tabs %}
{% tab title="Curl" %}
```shell
curl https://ethereum-mainnet-rpc.allthatnode.com/'YOUR-API-KEY' \
-X POST \
-H "Content-Type: application/json" \
-d '{ "jsonrpc":"2.0", "method":"eth_getBalance", "params":[ "0x829bd824b016326a401d083b33d092293333a831", "latest" ], "id":1 }'
```
{% endtab %}

{% tab title="Postman" %}
```json
URL: https://ethereum-mainnet-rpc.allthetnode.com/'YOUR-API-KEY'
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



## eth\_blockNumber

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
URL: https://ethereum-mainnet-rpc.allthetnode.com/'YOUR-API-KEY'
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
