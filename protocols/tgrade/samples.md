---
description: For more information on Tgrade RPC APIs, see the official documentation.
---

# Tgrade Samples

## \[GET] /node\_info

The properties of the connected node

#### Request

{% tabs %}
{% tab title="Curl" %}
```shell
curl https://tgrade-mainnet-rpc.allthatnode.com:1317/node_info \
--header "x-allthatnode-api-key: 'YOUR-API-KEY'"
```
{% endtab %}

{% tab title="Postman" %}

{% endtab %}
{% endtabs %}

#### Response

```json
{
  "node_info": {
    "protocol_version": {
      "p2p": "8",
      "block": "11",
      "app": "0"
    },
    "id": "768c8d3ed1398d19691fc89894c35d266ba18404",
    "listen_addr": "tcp://0.0.0.0:26656",
    "network": "tgrade-mainnet-1",
    "version": "0.34.19",
    "channels": "40202122233038606100",
    "moniker": "apple",
    "other": {
      "tx_index": "on",
      "rpc_address": "tcp://0.0.0.0:26657"
    }
  },
  "application_version": {
    "name": "tgrade",
    "server_name": "tgrade",
    "version": "1.0.1",
    "commit": "b5a6faf3ae2ceca15b3c506ca64e866c4bcfd914",
    "build_tags": "netgo,ledger",
    "go": "go version go1.18.2 linux/amd64",
    "build_deps": [
      "filippo.io/edwards25519@v1.0.0-beta.2",
      "github.com/99designs/keyring@v1.1.6 => github.com/cosmos/keyring@v1.1.7-0.20210622111912-ef00f8ac3d76",
      "github.com/ChainSafe/go-schnorrkel@v0.0.0-20200405005733-88cbf1b4c40d",
      "github.com/CosmWasm/wasmd@v0.27.0",
      "github.com/CosmWasm/wasmvm@v1.0.0",
      "github.com/Workiva/go-datastructures@v1.0.53",
      "github.com/armon/go-metrics@v0.3.10",
      "github.com/beorn7/perks@v1.0.1",
      "github.com/bgentry/speakeasy@v0.1.0",
      "github.com/btcsuite/btcd@v0.22.0-beta",
      "github.com/cespare/xxhash/v2@v2.1.2",
      "github.com/coinbase/rosetta-sdk-go@v0.7.0",
      "github.com/confio/ics23/go@v0.7.0",
      "github.com/cosmos/btcutil@v1.0.4",
      "github.com/cosmos/cosmos-sdk@v0.45.5",
      "github.com/cosmos/go-bip39@v1.0.0",
      "github.com/cosmos/iavl@v0.17.3",
      "github.com/cosmos/ibc-go/v3@v3.1.0",
      "github.com/cosmos/interchain-accounts@v0.1.0",
      "github.com/cosmos/ledger-cosmos-go@v0.11.1",
      "github.com/cosmos/ledger-go@v0.9.2",
      "github.com/davecgh/go-spew@v1.1.1",
      "github.com/desertbit/timer@v0.0.0-20180107155436-c41aec40b27f",
      "github.com/dvsekhvalnov/jose2go@v0.0.0-20200901110807-248326c1351b",
      "github.com/felixge/httpsnoop@v1.0.1",
      "github.com/fsnotify/fsnotify@v1.5.1",
      "github.com/go-kit/kit@v0.12.0",
      "github.com/go-kit/log@v0.2.0",
      "github.com/go-logfmt/logfmt@v0.5.1",
      "github.com/godbus/dbus@v0.0.0-20190726142602-4481cbc300e2",
      "github.com/gogo/gateway@v1.1.0",
      "github.com/gogo/protobuf@v1.3.3 => github.com/regen-network/protobuf@v1.3.3-alpha.regen.1",
      "github.com/golang/protobuf@v1.5.2",
      "github.com/golang/snappy@v0.0.3",
      "github.com/google/btree@v1.0.0",
      "github.com/google/gofuzz@v1.2.0",
      "github.com/google/orderedcode@v0.0.1",
      "github.com/gorilla/handlers@v1.5.1",
      "github.com/gorilla/mux@v1.8.0",
      "github.com/gorilla/websocket@v1.5.0",
      "github.com/grpc-ecosystem/go-grpc-middleware@v1.3.0",
      "github.com/grpc-ecosystem/grpc-gateway@v1.16.0",
      "github.com/gsterjov/go-libsecret@v0.0.0-20161001094733-a6f4afe4910c",
      "github.com/gtank/merlin@v0.1.1",
      "github.com/gtank/ristretto255@v0.1.2",
      "github.com/hashicorp/go-immutable-radix@v1.3.1",
      "github.com/hashicorp/golang-lru@v0.5.4",
      "github.com/hashicorp/hcl@v1.0.0",
      "github.com/hdevalence/ed25519consensus@v0.0.0-20210204194344-59a8610d2b87",
      "github.com/improbable-eng/grpc-web@v0.14.1",
      "github.com/klauspost/compress@v1.13.6",
      "github.com/lib/pq@v1.10.4",
      "github.com/libp2p/go-buffer-pool@v0.0.2",
      "github.com/magiconair/properties@v1.8.6",
      "github.com/mattn/go-colorable@v0.1.12",
      "github.com/mattn/go-isatty@v0.0.14",
      "github.com/matttproud/golang_protobuf_extensions@v1.0.1",
      "github.com/mimoo/StrobeGo@v0.0.0-20181016162300-f8f6d4d2b643",
      "github.com/minio/highwayhash@v1.0.2",
      "github.com/mitchellh/mapstructure@v1.4.3",
      "github.com/mtibben/percent@v0.2.1",
      "github.com/pelletier/go-toml@v1.9.4",
      "github.com/pkg/errors@v0.9.1",
      "github.com/pmezard/go-difflib@v1.0.0",
      "github.com/prometheus/client_golang@v1.12.1",
      "github.com/prometheus/client_model@v0.2.0",
      "github.com/prometheus/common@v0.32.1",
      "github.com/prometheus/procfs@v0.7.3",
      "github.com/rakyll/statik@v0.1.7",
      "github.com/rcrowley/go-metrics@v0.0.0-20200313005456-10cdbea86bc0",
      "github.com/regen-network/cosmos-proto@v0.3.1",
      "github.com/rs/cors@v1.8.2",
      "github.com/rs/zerolog@v1.27.0",
      "github.com/spf13/afero@v1.8.2",
      "github.com/spf13/cast@v1.5.0",
      "github.com/spf13/cobra@v1.4.0",
      "github.com/spf13/jwalterweatherman@v1.1.0",
      "github.com/spf13/pflag@v1.0.5",
      "github.com/spf13/viper@v1.11.0",
      "github.com/stretchr/testify@v1.7.2",
      "github.com/subosito/gotenv@v1.2.0",
      "github.com/syndtr/goleveldb@v1.0.1-0.20200815110645-5c35d600f0ca",
      "github.com/tendermint/btcd@v0.1.1",
      "github.com/tendermint/crypto@v0.0.0-20191022145703-50d29ede1e15",
      "github.com/tendermint/go-amino@v0.16.0",
      "github.com/tendermint/tendermint@v0.34.19",
      "github.com/tendermint/tm-db@v0.6.7",
      "github.com/zondax/hid@v0.9.0",
      "golang.org/x/crypto@v0.0.0-20220411220226-7b82a4e95df4",
      "golang.org/x/net@v0.0.0-20220412020605-290c469a71a5",
      "golang.org/x/sys@v0.0.0-20220412211240-33da011f77ad",
      "golang.org/x/term@v0.0.0-20210927222741-03fcf44c2211",
      "golang.org/x/text@v0.3.7",
      "google.golang.org/genproto@v0.0.0-20220407144326-9054f6ed7bac",
      "google.golang.org/grpc@v1.45.0 => google.golang.org/grpc@v1.33.2",
      "google.golang.org/protobuf@v1.28.0",
      "gopkg.in/ini.v1@v1.66.4",
      "gopkg.in/yaml.v2@v2.4.0",
      "gopkg.in/yaml.v3@v3.0.1",
      "nhooyr.io/websocket@v1.8.6"
    ],
    "cosmos_sdk_version": "v0.45.5"
  }
}
```



## \[GET] /blocks/latest

Get the latest block

#### Request

{% tabs %}
{% tab title="Curl" %}
```shell
curl https://tgrade-mainnet-rpc.allthatnode.com:1317/blocks/latest \
--header "x-allthatnode-api-key: 'YOUR-API-KEY'"
```
{% endtab %}
{% endtabs %}

#### Response

```shell
{
  "block_id": {
    "hash": "3830479E2915271F3D9E1B8554959878BAF3B2BC14314E45783FFDDB877EC4FF",
    "parts": {
      "total": 1,
      "hash": "0D1F1D055B087B711CA4ECB0015E34904895656146BB4FB1030090643B1CE74F"
    }
  },
  "block": {
    "header": {
      "version": {
        "block": "11"
      },
      "chain_id": "tgrade-mainnet-1",
      "height": "206426",
      "time": "2022-07-11T10:00:36.11544248Z",
      "last_block_id": {
        "hash": "51A6E2CF0782CA465DE576BB1EC72329E29FCF00CAF90B5A0537077484DFE2F8",
        "parts": {
          "total": 1,
          "hash": "BF83BEE005B0C3D6868F056B39317C50CBA09C36C6B79F18AE8EEB8BEEFBEB55"
        }
      },
      "last_commit_hash": "703ADD133D7919C46DD646C4974179BB4A5275A9556AB61F651E993883D445C3",
      "data_hash": "E3B0C44298FC1C149AFBF4C8996FB92427AE41E4649B934CA495991B7852B855",
      "validators_hash": "3E02DD27F2CD36C3BCF9F98A09CBD9AB069C171CFACE221F5C6AF9FFD7B57E53",
      "next_validators_hash": "3E02DD27F2CD36C3BCF9F98A09CBD9AB069C171CFACE221F5C6AF9FFD7B57E53",
      "consensus_hash": "990017FD433AD8244173E5D761BF0CE889F62CFC308C4864C865BE091B8E213E",
      "app_hash": "4100F48D18EACD22DC80CEC9893AF4A63BB224F1B40554FB1F1CD3A206C84A98",
      "last_results_hash": "E3B0C44298FC1C149AFBF4C8996FB92427AE41E4649B934CA495991B7852B855",
      "evidence_hash": "E3B0C44298FC1C149AFBF4C8996FB92427AE41E4649B934CA495991B7852B855",
      "proposer_address": "E88ADE7A6552F9CF9D3BF9F2666F7F63939C152F"
    },
    "data": {
      "txs": []
    },
    "evidence": {
      "evidence": []
    },
    "last_commit": {
      "height": "206425",
      "round": 0,
      "block_id": {
        "hash": "51A6E2CF0782CA465DE576BB1EC72329E29FCF00CAF90B5A0537077484DFE2F8",
        "parts": {
          "total": 1,
          "hash": "BF83BEE005B0C3D6868F056B39317C50CBA09C36C6B79F18AE8EEB8BEEFBEB55"
        }
      },
      "signatures": [
        {
          "block_id_flag": 2,
          "validator_address": "3407E8830E033C1E8B318688276A8D11ABEC2244",
          "timestamp": "2022-07-11T10:00:36.293092735Z",
          "signature": "aWlZuvNwp+5SfgCvtj5gxfnQivLbBAo0FPsyHuAre+M8dJ8ACqaYXt1/cDCVnD8a078KRTfWFpwOjrxLuGP/Cw=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "B2D505C5208CA66BC88A00143462C5CFEDCFD37C",
          "timestamp": "2022-07-11T10:00:36.073072782Z",
          "signature": "9fL9IBlVXCa1QXjpwYJJfknLS8R81a/Be949uOOG7puixJbZV7Yuj1Qu3GjCmByqC4wniJmKP2Y6Y7sN1hUgAg=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "ABDA84DB6AB233B1599B91C4BB8F51ABCC6A2540",
          "timestamp": "2022-07-11T10:00:36.235879067Z",
          "signature": "7CXk9Wkh3lx0+GLIj4QA253exp7HQjFYycWWPKSUzv1hiOOqzroZ93cSGoL1ffNvVetjqIRx5fnTq2veWK0vDw=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "1DAF2ED599EAAE61D9492EFEE57F28099E54657C",
          "timestamp": "2022-07-11T10:00:36.138074132Z",
          "signature": "CKj9psxWRnPzbwHgkzzzmAUrpAjA0CaeXfgc5hh+gTDvkKoi1NnFwJc0xxFRkrbRC/XNRZ/JGlHc3saEr8FXAQ=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "EA6FD5E4FF8C7BBCCA171DB96927DE549BDA8C63",
          "timestamp": "2022-07-11T10:00:36.11544248Z",
          "signature": "AHesIZHXRkOqSbL/QPBdBHM7eGurO+m9gTUXOO30ooJYr9hrPT6+BE2Tpr3dru0kEXVAdgwiQB96d1Z1br5IBA=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "BF79DCC7980E75EF84B3275A1835D04E4996C139",
          "timestamp": "2022-07-11T10:00:36.121954302Z",
          "signature": "ObV6uBPrESgxU5qDhQ/cqpgm3mJEdJjLH1TvOES2tPePE83fSXSn/8PNbsFE1ddddV3zzJv2hIDl1DDthWJcDQ=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "CD604D20C92A9B84BE4A190E0D4B48D69D4852C1",
          "timestamp": "2022-07-11T10:00:36.104113163Z",
          "signature": "RRQxnjxC3L/yDhjwJWcSasiGtxThF2UdPh/qIWiaOYXiJOYlxyl2QjZ2+2iZT9U0fZ/SSBmXPwYB5tPSH4/jDw=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "EB3AFEDB4C058849DE49674023A41A8E4E855DF6",
          "timestamp": "2022-07-11T10:00:36.109669688Z",
          "signature": "fBk6FJGB/W2N4QyGyWpur+c8gSwmGWzEYh139oC0byvN+KUIckQFivmgCF8JmyaptRsf9fX0/s9RiAw/xCuNAQ=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "58E06D9B53BD76450843E646AD85884CE25CD13E",
          "timestamp": "2022-07-11T10:00:36.117135827Z",
          "signature": "ntlp9sJ7OxDPpQqJwpI5YKjbeptIZUki7EPE0CNI0EcDrhtHBNwnzpM1BlVs5NAJ2S5HCKLkQmkOB5QdnRILDg=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "8AA8A5B43732E77E812DC0EB91ED104F1AA6696A",
          "timestamp": "2022-07-11T10:00:36.196136866Z",
          "signature": "GjShJz6REwCriE4XbD5TNe0alYCZN6RzbE0/+ScShgHQiw6jWt8djYRw+JmThQ7xjEVcfdpimTtwRrrBRpzzBQ=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "1FA2873EEAFD47947B8D4070D600BD37C81EBF94",
          "timestamp": "2022-07-11T10:00:36.103152976Z",
          "signature": "ZFw5S6Q3SdEd8EDUU/4FhVIapOK5pGBB9/eM3yiAzX7R/rvc9FQRiLN7k8mGaORrtK5Es4g3e0nJZSIHan2pCQ=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "3489F020A600ACF46653F97F28333566F43976A6",
          "timestamp": "2022-07-11T10:00:36.115522253Z",
          "signature": "32ddIrRgSTgXrXQwzS/ivC6lPRvn84oKWLAOoVG587UQwpeTUjdNRpx9fMr3h5ycrfE1tdbW1GFoYzgSgB9tDA=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "B8EF3B3699640B47C5C0ADA352EC2F235F58D688",
          "timestamp": "2022-07-11T10:00:36.120391251Z",
          "signature": "359VFtsvuhCNpppWU2bjxPAObwP4+fQPM5lq5uPOG0JwTjvggux6K0Ta+FIrqNEK8kO839gMxUYDyAsQ9tdTAg=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "26B495E7B47A9FE6CB6E882B069B2EF20E94EC52",
          "timestamp": "2022-07-11T10:00:36.107958358Z",
          "signature": "jDx1G8kTUO/Ax8YIUNtcqRG5UBKDwgPyOi/j+B6ZTk34Bc/FeKjOUNRBjDwYaLYs0bM5zMkOYca+fGsWwpJsAg=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "4692D7BDCB00A6922A909044E99BE17D0C83B26F",
          "timestamp": "2022-07-11T10:00:36.107631756Z",
          "signature": "wbiRiaUSZnlW1KK3SvNkH69kzwsBegJAV8qcvOpwjuQ5sFP4rmB63B1PHqOQG9P7XGXSAdYVsfFWS45tsxznCQ=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "A01D3668B101AF9DFDA6051F8610C49549BC09C7",
          "timestamp": "2022-07-11T10:00:36.124271393Z",
          "signature": "ct9PE0V2Us4w+dqKMSV4SgXCgokPAtFBV0vnT3cdECN6FXLm7+3F8vgTqo/D8onpZYtdxSijlDl4BR9v4H5qAg=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "83D84565D3BB8ECADE83B548050177FC3609774D",
          "timestamp": "2022-07-11T10:00:36.083549735Z",
          "signature": "OdAf0lItBrTwdtMQvjNTtY9PnjJsoG4rjt/0RjQ7JAPj9kj3iKRll8+rt2nM7p1dTPSGEAFmhys00V+89f/ODw=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "6D9F8A56433FCAB0B63CE71F257C654181A8CEA3",
          "timestamp": "2022-07-11T10:00:36.222214662Z",
          "signature": "6F3SCJxtYo3tlStHSIFLZBN4ij73BC1EDjDyaWe9mxb8dB0kBVC0Qn//Cs2NWfbw49OqK0EtXxJZGWKbdnidDQ=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "002EC63BD81F1905CF83BA7198D77D397E2F25D2",
          "timestamp": "2022-07-11T10:00:36.201325362Z",
          "signature": "R7MCYVeOF4g4uDysVjz8UTJ0wfRonm1rzTQnBTAYr98yUC+6sf6p+Z9SxgTu1aVIpOqU7Rr1Mv1g6caouTOFAw=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "14375F8C4659F9E3B8543CB1989C03D8F30F6FD4",
          "timestamp": "2022-07-11T10:00:36.090670677Z",
          "signature": "QRL+JuBNmGe0TgtXz076Ny/+EuuBF8T1IWDLDRDxNczzvxaJE17ABlyfaHRkXMNyyKAeO3O3RymSmipGuEvpAA=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "2451A1FAD47A67075619BE409FA6DADD3549F077",
          "timestamp": "2022-07-11T10:00:36.168338678Z",
          "signature": "8XZ7P/z25szjBpRWPbuMXO+NhL/iHRGImW6KHOPNuYE/vDXIwWtN+6PeOAxV6JTzzMcI9+ei6QGPoi7bHH+7BQ=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "29EB5342BC2408E9C43A67A4E12E9DEF39D46E4E",
          "timestamp": "2022-07-11T10:00:36.109217723Z",
          "signature": "zQEACqbc8IzwhFqGLjTyvk87g7d/ui4ft9QqCaEK+UH1VY19nNGA6VVENqV319N/d79pSqp9OIoz3lubmn6HDw=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "3252A6706504C1973DF69C5BED1FC544C140C685",
          "timestamp": "2022-07-11T10:00:36.108302711Z",
          "signature": "TwXz5dwZlN/bk5n9O0588Ft+lXZmuy2dA29bxmIfp7q94hQ/WLrWLIcQ6xF+/XfKWPg87QDOQKIpVMbh1B1eAA=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "3AC353EA0F012F682DE566E421F088914832BD55",
          "timestamp": "2022-07-11T10:00:36.205622464Z",
          "signature": "6lup40p6AhF+ZiXYIPD0jRig8ofFMXa1cnX2ie0ZsKSUBo7ce2alR4n+31w9qPmc5H3M7+XFubbmdAIuvDjfBg=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "3D87BDE493E259063EE68563501429654A9C4AC6",
          "timestamp": "2022-07-11T10:00:36.113598133Z",
          "signature": "NUKWGWm8FbYTCxjP2CUtxdlfnyAe9omnwOEniLpWv0D3hz27HmmavJ8Sw5LzIxOX/fQ94t5T/rcr12TT5yfECw=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "456BA9DF0BA9D1C84B15F4D6FD36D43D9CE9D89C",
          "timestamp": "2022-07-11T10:00:36.114239114Z",
          "signature": "Aya6D5QmUyxfXfwBzDkHGxefaukRaeB66V9slMvmA+y8KzgrzKUpXos8k3FwsVLFeR+P0nzs+kSUwGXTJhvWAA=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "47E6545FC99824DDBCD499F4BFADDDFD7DCD238B",
          "timestamp": "2022-07-11T10:00:36.109754327Z",
          "signature": "vML5HXlL5EGbz2wSrhqQUunBGzPAPxLzHA8obeO01kYkpSDl0kSg02DzXzLFpTUZKr1XfTXwHOg8q3s9LYo8Aw=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "4AD344F60FEBAF62A674528E7BDA6505F871D48A",
          "timestamp": "2022-07-11T10:00:36.124655378Z",
          "signature": "qQggNVdXVfiLKtxQJ/Spqfj++Jp/ZzSzxEiJ2sMvI2fHX92iANJfyh3yh+Hn3imsWJQW4MPt6iYsY7CTOc3cCA=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "4B637C81F0FFF7B9692E6DE83E20886E5BB4881F",
          "timestamp": "2022-07-11T10:00:36.104017339Z",
          "signature": "U0i/eYGl1QBjs4ET6CPOjlGgW+g9JAsZCbxc1BjnvuIzm79tIkNQPLPl+5w3Ra9TShg1WKCy+3dXk6OkHbDHBA=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "4BBD38017F317F9DEC7B9732FACC76D2F8B28A9C",
          "timestamp": "2022-07-11T10:00:36.145142483Z",
          "signature": "R+qz1b4N1W01G9zZCqef3AsG8rxSSQZis6RB3emyZXSgHcNQeFp9zX1T51SEHSpwSNB06Q3sAU53j5ZZiLRkAQ=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "554034521A0AB9180CDA23D6ABFAD2185B1EAC6D",
          "timestamp": "2022-07-11T10:00:36.104393946Z",
          "signature": "U3lxd21zwQgxN0SNiFM3wsoCNNgcXcur9czog6flxYIepqD3iE3cKyi6LujE81kivaoCy/fojzbWX4REmnz4Bw=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "6E645E336946ECC45B87BA08E08912AB8E53A0F2",
          "timestamp": "2022-07-11T10:00:36.117452617Z",
          "signature": "I81ADW99+fjtEb0lV2b2TwxqjVaFxI8Cb2Gsgo+1r8JjFpZRID/E5O/6ZzcKpgmlH8EVFTrSqNJfbUYZjEGZBw=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "746DE3413C4FABF7F76362934B9905D9E49190B0",
          "timestamp": "2022-07-11T10:00:36.10711526Z",
          "signature": "MjylNsg6MwKVUVMdpA/IPnHJe/2lZ5l7P+wuwp8uQQrJ0vgXNVE2Rb95NGDv10W+qSb8x+6sCj+QC5U9Pbb/Aw=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "77EBFC90F4BE26A7B978972C760039BF8042E8A4",
          "timestamp": "2022-07-11T10:00:36.116428674Z",
          "signature": "w5VzIGt9yLXn9UZBgQXlr0K8XcXvuu2Nb8ErmP6B99c5YsRqR/mLsOkG4QsUMUYRuQhpMJdl6cVEYgXVWOsKBw=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "798ECDDBCC1C8F1733B32AFA880C247F78C29111",
          "timestamp": "2022-07-11T10:00:36.154892825Z",
          "signature": "PPteeeAIIYF58Fn/6s8Yz8O5QJoCnkyJkS4Kc4WgdzAzACU4A2eIFu6Y07A9lIBarPX+2nGVWwNhTOIfRSoQCA=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "7AA0D3BF7B3F0700BA578F22E68D0BE71336FEC9",
          "timestamp": "2022-07-11T10:00:36.186530066Z",
          "signature": "Q2dP/tLS24vRVFCQffEvv4JzfGoBdk+1PShgJmqkyvQgO2y9Rcxqq858VNggrTCKYCj2mZaHPLSjMcc2K6ULAA=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "806F770F747301142C49AB24B9304C95C6C6A842",
          "timestamp": "2022-07-11T10:00:36.113531008Z",
          "signature": "3WL5Mj8P1jc3yfe5R/Ey4npyHVGU4VYIQgnTiv+Wn26IEsaxHmvEQsYr31d3tCEkUDhvFH4aLDlTPai4otwxCg=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "9151D1CFF91B257373235172A61540C995B66C06",
          "timestamp": "2022-07-11T10:00:36.076443262Z",
          "signature": "Ao+l69xv8AbxFXu1PWIlHxTiwL5HcPNO84WjlMFv2Ng5kf//bVwnT6bH5HIZs/Cfx0XWRMZFWq+TjP2GNRdEDQ=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "95D80C63030F498FF7C94B755ADE529C9E8B5D42",
          "timestamp": "2022-07-11T10:00:36.107940408Z",
          "signature": "Ubmd0UAm7CQ9/JnB1whe6JvvGtxoE3Z2tqlZ7WVGC0+b4orQpjhiIcTGJCSu/UokJxN6f9fJhG/7QahRBZ9iDg=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "97969B836256A31E16FDB5485C43F5D0F6A2D04A",
          "timestamp": "2022-07-11T10:00:36.194167282Z",
          "signature": "V8KG9D3ZLrQAX9tLQPyyru9AtaD9weODdGSOHGqGT0pwiv8EWI5as1QzcalA2ldKTvW1Mgj6JECEUl3y0oD1DA=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "A3F17E3F5297ADD9625FCA5B18A54C18EEA46B83",
          "timestamp": "2022-07-11T10:00:36.124507022Z",
          "signature": "ZA8r+6dG8uGnOj81MfXV/VRFdN8eveSDDJ14ahIA6Jc7QHj43LelyGihRD4XzjJjbEOK3qU9y9a4DoUuP+LMCQ=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "AC2EB45FDE07420445A3E6804B4AF13A8D07FC45",
          "timestamp": "2022-07-11T10:00:36.129983321Z",
          "signature": "2cBG5xofBxGyEqfWQef7T9kR4mPqDR/02tFNmdjY0+8rJmKajyxVJ9ZqTAN7T7cR/0N8mNleuUspASYsyrHRCw=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "ACD764C3A97F3A7BBA0B04DE6A22F3A5D8CF620C",
          "timestamp": "2022-07-11T10:00:36.103665269Z",
          "signature": "VBjbur6Izd1hLD21FrQ7DQ5NL4FYzimEZBTBSDM/GVNu41/5LZgLqU7rezZn2pnf0F6TtmLDWiZ8LcYpwK5ACA=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "AD7CC6A6C55909362CCA1B8FE468DF96B5D15D5B",
          "timestamp": "2022-07-11T10:00:36.108132871Z",
          "signature": "HG6SgUimFNWC44Lo4jUJZ1DjZFlWYQIXVEWEorLYqHZFpJ9UIUz2LtZiU/xtUzFlN5AP9KehzmKUlR7e1RtQDQ=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "AE4A26DAE79AD12444E8D39E4175282CD8B0816E",
          "timestamp": "2022-07-11T10:00:36.145868395Z",
          "signature": "wraNRO1ECbRYraRt4iQBI52VlDYISjgzwO6QhP2hZmL3PgIMxae/Ka0t+EjCOrE1dGTO/OB12VSw68BztcYDDA=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "B9F39399E99519B75D4F81711D1C6F5EFA6C7A34",
          "timestamp": "2022-07-11T10:00:36.191601316Z",
          "signature": "lmQYLSX+jWjlphKF/BYgGBWtt278vuJPBXAsXPZBVuEvaMPYflOfbsLfQFEVfnQ/KKWRQ5oFcB4WtuN7ClMRCA=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "BD6A51E9B907E70B520AE006BDBFD37604EFAFED",
          "timestamp": "2022-07-11T10:00:36.264634674Z",
          "signature": "4omzVKK65eq9jU5v6qLyHdeNDYZbh+BVIOmgMNbhd7Qx82MXqCgASUiNccqxKqUF/Bdtho/Q34WC9fp9Fx4/CQ=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "CDA7E96E3BBB6E390335D9F91A29FD0A7E0254BC",
          "timestamp": "2022-07-11T10:00:36.119664419Z",
          "signature": "X+fFJnEKEU3jZV5RlzYlRk/GtK+X34HHw4tli/jxpuZx5Iq4yKnpNRykdjDVJktQsd4jyk3YMH5vNyXIC67GCQ=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "D51B48D27EBC2AF7C995D055F7BCAF839A1F79A7",
          "timestamp": "2022-07-11T10:00:36.193471646Z",
          "signature": "z09JLtOKlET6ydnoa9AsixCkI/ghGeTDD/MnLtqpK69seqWuGqnB833s1c5RYUzxZMcbnZKqIKrH/o5WJ4EhAw=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "E346BA9D260D8A73EF9074FAC90083891E07A731",
          "timestamp": "2022-07-11T10:00:36.101306107Z",
          "signature": "TkLighJvNLDcAULM1gDJ40qRuGpkNuMTyIoYrbI5rR+/2DI99irWcLjzfH4a0dhETPuYcn60bkg4MV24oQWvBg=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "E633F31ABC07EA7B0B0992E6C63537561F0504BA",
          "timestamp": "2022-07-11T10:00:36.120116548Z",
          "signature": "e6WDovHNgMhhzy04NsrHA4cFXsbMHBK79roV24d7F3kvUyUqkM+huQDRcq9Vw0j/8OrmxpLMQ6o3OmKAvuUMCw=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "E7CEA74F413C9C12EE74B27616B5E381B41B175D",
          "timestamp": "2022-07-11T10:00:36.110751112Z",
          "signature": "oSduKUH7cqflapd3dz8v5qAkci63t3ya7RZZyn07cP0ojRSwQ3w6hM7v0KZtsn0jTM7GTxrWdWn5j6Osfr0qAA=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "E88ADE7A6552F9CF9D3BF9F2666F7F63939C152F",
          "timestamp": "2022-07-11T10:00:36.094482383Z",
          "signature": "VCogrpp/ylG4tz1CzaWTqQB8VIjL2KkhVgtgO6ogFmJ0MXTw61pwCLwGFmYen6LzDT1pz7aUec6iNf6hMH16Dw=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "E97C2A115C3C49E76A45BFCCB5211A2AB0C4BB7A",
          "timestamp": "2022-07-11T10:00:36.109659829Z",
          "signature": "Kr+9ugXzAsBNzgtR4effuG5RDSoF9UJNL95fho5QGYoUk/kzNHDDiGQQwpbDE2mfn0jAHAzE+Pfm1iSyybxzDA=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "EC7CEBA4D85B2B2ACA61B289FB0F7CEB5BA4DE8B",
          "timestamp": "2022-07-11T10:00:36.087413789Z",
          "signature": "VKDjL5DRxH9P6xA2K1h69iePs5Ysvjd8mNmaKmAIsW8ReEx7MbA+j15nHCbGuqqDzcExjWE/DTPXafu3ShkvCw=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "EE4AAF8436EAC19D2C8D5ECEF50BACAA8E8E452E",
          "timestamp": "2022-07-11T10:00:36.119273761Z",
          "signature": "fHw9lI0na19U31C4y7s9trhR1cHsb4dvC8f+igIHfwSmmHu/y26xStQAvbAoTolm6XPv3xYOu8dTnYPRedaqAw=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "EFBFF5C83C772ED89D9EC9CEE0404816FF508001",
          "timestamp": "2022-07-11T10:00:36.11414592Z",
          "signature": "rbnTOrx9isN/eW1YxXIh7QY3i/WCklVache4eiopsp7mC+bSxG/OSg9YdXXVAJLewXsuXYi3tH11Xw3mxGuBCQ=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "FBAC1ECAF278123EE2F22BF9EEA0F75D001B98A1",
          "timestamp": "2022-07-11T10:00:36.084284816Z",
          "signature": "VtSQGY+J3aOSj5r5B9tsHd71tNHhkVp2i7wYZROA1FaV+R8vcufYUuC0JOoA+90T/3FGZqGzKretgX2yR6uBDQ=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "42616207399876A204BEE1B6EBF4F6F233EF390E",
          "timestamp": "2022-07-11T10:00:36.09993242Z",
          "signature": "xp3Ph3oKn8GAgtUr4+g8Ik+yAuUUT9a1fdSci9H9baxY5tNeVOlmokNr5xOkWTUYnTlfi+pMW2VFgLJZg4OMBw=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "482EB996A835C5B9DCFCBC47D72196BE480CA88C",
          "timestamp": "2022-07-11T10:00:36.134038562Z",
          "signature": "KIRyJt0eZGvMRolg8IuW1vdH6B2mnPGWeuQPjqvgi6pYViLB8qlNdN0qe5UFvEm7m44IwcHhOVHTzWzXbjdKDg=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "5F66E049A374AA8BC06D815D028C42098C6D6254",
          "timestamp": "2022-07-11T10:00:36.081841565Z",
          "signature": "BLkvqo0kl0ZJwcodQh1o88uKfULddeTbjwFmfVlEx673eR7W/pcbDRizunMp1OkkWE9hIacDSJbf4vO94Aj+CA=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "4D9395DF1A5468EBE97CAFD93669A0C0CA688921",
          "timestamp": "2022-07-11T10:00:36.215158449Z",
          "signature": "Ybta82nDl/7tFNoq/Nw0mU+BM6Ver5qoAfSe9sVmka54qcaAsicthje+kaPI+WN+1qzy0a5jNilUXtekuxWNCQ=="
        }
      ]
    }
  }
}
```
