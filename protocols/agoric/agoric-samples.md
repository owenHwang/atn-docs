---
description: For more information on Agoric RPC APIs, see the official documentation.
---

# Agoric Samples

## \[GET] /node\_info

The properties of the connected node

#### Request

{% tabs %}
{% tab title="Curl" %}
```shell
curl https://agoric-mainnet-rpc.allthatnode.com:1317/node_info \
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
    "id": "01c3a56aa6e69c59161a9e4ae1037388c8931367",
    "listen_addr": "tcp://0.0.0.0:26656",
    "network": "agoric-3",
    "version": "v0.34.13",
    "channels": "40202122233038606100",
    "moniker": "agoric-rpc1",
    "other": {
      "tx_index": "on",
      "rpc_address": "tcp://0.0.0.0:26657"
    }
  },
  "application_version": {
    "name": "ag0",
    "server_name": "ag0",
    "version": "HEAD-a2a0dc089ca98b9eae50802d8ed866bf8c209b06",
    "commit": "a2a0dc089ca98b9eae50802d8ed866bf8c209b06",
    "build_tags": "netgo,ledger",
    "go": "go version go1.17.2 linux/amd64",
    "build_deps": [
      "filippo.io/edwards25519@v1.0.0-beta.2",
      "github.com/99designs/keyring@v1.1.6",
      "github.com/ChainSafe/go-schnorrkel@v0.0.0-20200405005733-88cbf1b4c40d",
      "github.com/Workiva/go-datastructures@v1.0.52",
      "github.com/armon/go-metrics@v0.3.9",
      "github.com/beorn7/perks@v1.0.1",
      "github.com/bgentry/speakeasy@v0.1.0",
      "github.com/btcsuite/btcd@v0.22.0-beta",
      "github.com/cespare/xxhash/v2@v2.1.1",
      "github.com/coinbase/rosetta-sdk-go@v0.6.10",
      "github.com/confio/ics23/go@v0.6.6",
      "github.com/cosmos/btcutil@v1.0.4",
      "github.com/cosmos/cosmos-sdk@v0.44.5 => github.com/agoric-labs/cosmos-sdk@v0.44.5-alpha.agoric.ag0.5",
      "github.com/cosmos/go-bip39@v1.0.0",
      "github.com/cosmos/iavl@v0.17.3",
      "github.com/cosmos/ibc-go/v2@v2.0.2",
      "github.com/cosmos/ledger-cosmos-go@v0.11.1",
      "github.com/cosmos/ledger-go@v0.9.2",
      "github.com/davecgh/go-spew@v1.1.1",
      "github.com/desertbit/timer@v0.0.0-20180107155436-c41aec40b27f",
      "github.com/dvsekhvalnov/jose2go@v0.0.0-20200901110807-248326c1351b",
      "github.com/felixge/httpsnoop@v1.0.1",
      "github.com/fsnotify/fsnotify@v1.5.1",
      "github.com/go-kit/kit@v0.10.0",
      "github.com/go-logfmt/logfmt@v0.5.0",
      "github.com/godbus/dbus@v0.0.0-20190726142602-4481cbc300e2",
      "github.com/gogo/gateway@v1.1.0",
      "github.com/gogo/protobuf@v1.3.3 => github.com/regen-network/protobuf@v1.3.3-alpha.regen.1",
      "github.com/golang/protobuf@v1.5.2",
      "github.com/golang/snappy@v0.0.3",
      "github.com/google/btree@v1.0.0",
      "github.com/google/orderedcode@v0.0.1",
      "github.com/gorilla/handlers@v1.5.1",
      "github.com/gorilla/mux@v1.8.0",
      "github.com/gorilla/websocket@v1.4.2",
      "github.com/gravity-devs/liquidity@v1.4.0",
      "github.com/grpc-ecosystem/go-grpc-middleware@v1.3.0",
      "github.com/grpc-ecosystem/grpc-gateway@v1.16.0",
      "github.com/grpc-ecosystem/grpc-gateway/v2@v2.0.1",
      "github.com/gsterjov/go-libsecret@v0.0.0-20161001094733-a6f4afe4910c",
      "github.com/gtank/merlin@v0.1.1",
      "github.com/gtank/ristretto255@v0.1.2",
      "github.com/hashicorp/go-immutable-radix@v1.0.0",
      "github.com/hashicorp/golang-lru@v0.5.4",
      "github.com/hashicorp/hcl@v1.0.0",
      "github.com/hdevalence/ed25519consensus@v0.0.0-20210204194344-59a8610d2b87",
      "github.com/improbable-eng/grpc-web@v0.14.1",
      "github.com/klauspost/compress@v1.11.7",
      "github.com/libp2p/go-buffer-pool@v0.0.2",
      "github.com/magiconair/properties@v1.8.5",
      "github.com/mattn/go-isatty@v0.0.14",
      "github.com/matttproud/golang_protobuf_extensions@v1.0.1",
      "github.com/mimoo/StrobeGo@v0.0.0-20181016162300-f8f6d4d2b643",
      "github.com/minio/highwayhash@v1.0.1",
      "github.com/mitchellh/go-homedir@v1.1.0",
      "github.com/mitchellh/mapstructure@v1.4.2",
      "github.com/mtibben/percent@v0.2.1",
      "github.com/pelletier/go-toml@v1.9.4",
      "github.com/pkg/errors@v0.9.1",
      "github.com/pmezard/go-difflib@v1.0.0",
      "github.com/prometheus/client_golang@v1.11.0",
      "github.com/prometheus/client_model@v0.2.0",
      "github.com/prometheus/common@v0.29.0",
      "github.com/prometheus/procfs@v0.6.0",
      "github.com/rakyll/statik@v0.1.7",
      "github.com/rcrowley/go-metrics@v0.0.0-20200313005456-10cdbea86bc0",
      "github.com/regen-network/cosmos-proto@v0.3.1",
      "github.com/rs/cors@v1.7.0",
      "github.com/rs/zerolog@v1.23.0",
      "github.com/spf13/afero@v1.6.0",
      "github.com/spf13/cast@v1.4.1",
      "github.com/spf13/cobra@v1.2.1",
      "github.com/spf13/jwalterweatherman@v1.1.0",
      "github.com/spf13/pflag@v1.0.5",
      "github.com/spf13/viper@v1.8.1",
      "github.com/stretchr/testify@v1.7.0",
      "github.com/subosito/gotenv@v1.2.0",
      "github.com/syndtr/goleveldb@v1.0.1-0.20200815110645-5c35d600f0ca",
      "github.com/tendermint/btcd@v0.1.1",
      "github.com/tendermint/crypto@v0.0.0-20191022145703-50d29ede1e15",
      "github.com/tendermint/go-amino@v0.16.0",
      "github.com/tendermint/tendermint@v0.34.14 => github.com/tendermint/tendermint@v0.34.13",
      "github.com/tendermint/tm-db@v0.6.4",
      "github.com/zondax/hid@v0.9.0",
      "golang.org/x/crypto@v0.0.0-20210817164053-32db794688a5",
      "golang.org/x/net@v0.0.0-20210903162142-ad29c8ab022f",
      "golang.org/x/sys@v0.0.0-20210903071746-97244b99971b",
      "golang.org/x/term@v0.0.0-20201126162022-7de9c90e9dd1",
      "golang.org/x/text@v0.3.6",
      "google.golang.org/genproto@v0.0.0-20210828152312-66f60bf46e71",
      "google.golang.org/grpc@v1.42.0 => google.golang.org/grpc@v1.33.2",
      "google.golang.org/protobuf@v1.27.1",
      "gopkg.in/ini.v1@v1.63.2",
      "gopkg.in/yaml.v2@v2.4.0",
      "gopkg.in/yaml.v3@v3.0.0-20210107192922-496545a6307b",
      "nhooyr.io/websocket@v1.8.6"
    ],
    "cosmos_sdk_version": "v0.44.5"
  }
}
```
