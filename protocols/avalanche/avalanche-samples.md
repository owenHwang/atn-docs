---
description: Avalanche nodes accept HTTP requests using the JSON-RPC 2.0 specification.
---

# Avalanche Samples

## eth\_blockNumber

Returns most recent block number

#### Request

{% tabs %}
{% tab title="Curl" %}
```shell
curl https://avalanche-mainnet-rpc.allthatnode.com/ext/bc/C/rpc \
--header "x-allthatnode-api-key: 'YOUR-API-KEY'" \
--request POST \
--header 'content-type:application/json;' \
--data '{ "jsonrpc":"2.0", "method":"eth_blockNumber","params":[],"id":1}'
```
{% endtab %}

{% tab title="Postman" %}

{% endtab %}
{% endtabs %}

#### Response

```json
{
    "jsonrpc": "2.0",
    "result": "0x1062f20",
    "id": 1
}
```
