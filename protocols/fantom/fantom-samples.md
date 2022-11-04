---
description: Fantom nodes accept HTTP requests using the JSON-RPC 2.0 specification.
---

# Fantom Samples

## eth\_blockNumber

Returns most recent block number

#### Request

{% tabs %}
{% tab title="Curl" %}
```shell
curl https://fantom-mainnet-rpc.allthatnode.com/'YOUR-API-KEY' \
-X POST \
-H "Content-Type: application/json" \
-d '{"jsonrpc":"2.0","method":"eth_blockNumber","params":[],"id":1}'
```
{% endtab %}

{% tab title="Postman" %}
```json
URL: https://fantom-mainnet-rpc.allthetnode.com/'YOUR-API-KEY'
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
