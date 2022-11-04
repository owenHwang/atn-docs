---
description: Moonriver nodes accept HTTP requests using the JSON-RPC 2.0 specification.
---

# Moonriver Samples

## eth\_blockNumber

Returns most recent block number

#### Request

{% tabs %}
{% tab title="Curl" %}
```shell
curl https://moonriver-mainnet-rpc.allthatnode.com:9933/'YOUR-API-KEY' \
-X POST \
-H "Content-Type: application/json" \
-d '{"jsonrpc":"2.0","method":"eth_blockNumber","params":[],"id":1}'
```
{% endtab %}

{% tab title="Postman" %}
```json
URL: https://moonriver-mainnet-rpc.allthetnode.com:9933/YOUR-API-KEY
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
    "result": "0x5b338f4",
    "id": 1
}
```
