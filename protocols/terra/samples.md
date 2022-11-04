---
description: For more information on Terra RPC APIs, see the official documentation.
---

# Terra Samples

## Block Info

Returns block info

#### Request

{% tabs %}
{% tab title="Curl" %}
```bash
curl https://terra-mainnet-rpc.allthatnode.com/'YOUR-API-KEY' \
--header "Content-Type: application/json" \
--request POST \
--data '{"method": "block", "params": ["5900001"], "id": 1}' 
```
{% endtab %}

{% tab title="Postman" %}
```json
URL: https://terra-mainnet-rpc.allthatnode.com/'YOUR-API-KEY'
RequestType: POST
Body: 
{
    "method":"block",
    "params":["5900001"],
    "id":1
}
```
{% endtab %}
{% endtabs %}

#### Response

```json
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "block_id": {
            "hash": "E88E3641A488EBA3D402FC072879C6399AA2CDC7B6CC5A3061E5A64D9FFD3BDE",
            "parts": {
                "total": 1,
                "hash": "9B12141D9712125D138D94E1DA493EC635A48FB2AEF474C471513C570D17DCF3"
            }
        },
        "block": {
            "header": {
                "version": {
                    "block": "11"
                },
                "chain_id": "bombay-12",
                "height": "5900001",
                "time": "2021-09-28T09:00:00Z",
                "last_block_id": {
                    "hash": "",
                    "parts": {
                        "total": 0,
                        "hash": ""
                    }
                },
                "last_commit_hash": "E3B0C44298FC1C149AFBF4C8996FB92427AE41E4649B934CA495991B7852B855",
                "data_hash": "E3B0C44298FC1C149AFBF4C8996FB92427AE41E4649B934CA495991B7852B855",
                "validators_hash": "26BD6FCDCF7EA24EA6AFB6101463E261AF52AF205673EE7FED5BEAADA147C35D",
                "next_validators_hash": "26BD6FCDCF7EA24EA6AFB6101463E261AF52AF205673EE7FED5BEAADA147C35D",
                "consensus_hash": "439BEC479E979FA68A1987AEB26B28BC1E3B8C39E46503E9840D8C309D315FC4",
                "app_hash": "E3B0C44298FC1C149AFBF4C8996FB92427AE41E4649B934CA495991B7852B855",
                "last_results_hash": "E3B0C44298FC1C149AFBF4C8996FB92427AE41E4649B934CA495991B7852B855",
                "evidence_hash": "E3B0C44298FC1C149AFBF4C8996FB92427AE41E4649B934CA495991B7852B855",
                "proposer_address": "42823B42D99BF70FCAF54CFA419D03789368EE88"
            },
            "data": {
                "txs": []
            },
            "evidence": {
                "evidence": []
            },
            "last_commit": {
                "height": "0",
                "round": 0,
                "block_id": {
                    "hash": "",
                    "parts": {
                        "total": 0,
                        "hash": ""
                    }
                },
                "signatures": []
            }
        }
    }
}
```
