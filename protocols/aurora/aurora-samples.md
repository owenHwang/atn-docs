---
description: Aurora nodes accept HTTP requests using the JSON-RPC 2.0 specification.
---

# Aurora Samples

## eth\_blockNumber

Returns most recent block number

#### Request

{% tabs %}
{% tab title="Curl" %}
```shell
curl https://aurora-mainnet-rpc.allthatnode.com/'YOUR-API-KEY' \
--request POST \
--header "Content-Type: application/json" \
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
    "result": "0x425fef3",
    "id": 1
}
```
