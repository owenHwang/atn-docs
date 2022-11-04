---
description: Solana nodes accept HTTP requests using the JSON-RPC 2.0 specification.
---

# Solana Samples

## getBlockHeight

Returns the current block height of the node

#### Request

{% tabs %}
{% tab title="Curl" %}
```shell
curl https://solana-mainnet-rpc.allthatnode.com/'YOUR-API-KEY' \
--request POST \
--header "Content-Type: application/json" \
--data '{"jsonrpc":"2.0","id":1, "method":"getBlockHeight"}'
```
{% endtab %}

{% tab title="Postman" %}

{% endtab %}
{% endtabs %}

#### Response

```json
{"jsonrpc":"2.0","result":127475622,"id":1}
```

