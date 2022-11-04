---
description: For more information on Axelar RPC APIs, see the official documentation.
---

# Axelar Samples

## \[GET] /node\_info

The properties of the connected node

#### Request

{% tabs %}
{% tab title="Curl" %}
```shell
curl https://axelar-mainnet-rpc.allthatnode.com:1317/node_info \
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
    "id": "96f9ff25b37a81569d26f197aa0f04184b3004db",
    "listen_addr": "tcp://0.0.0.0:26656",
    "network": "axelar-dojo-1",
    "version": "0.34.19",
    "channels": "40202122233038606100",
    "moniker": "strawberry tart2",
    "other": {
      "tx_index": "on",
      "rpc_address": "tcp://0.0.0.0:26657"
    }
  },
  "application_version": {
    "name": "axelar",
    "server_name": "axelard",
    "version": "0.19.2",
    "commit": "23ff97c2cc1f61e7347865bca73c6cae87e6f660",
    "build_tags": "ledger",
    "go": "go version go1.18.2 linux/amd64",
    "build_deps": [
      "filippo.io/edwards25519@v1.0.0-beta.2",
      "github.com/99designs/keyring@v1.1.6",
      "github.com/ChainSafe/go-schnorrkel@v0.0.0-20200405005733-88cbf1b4c40d",
      "github.com/Workiva/go-datastructures@v1.0.53",
      "github.com/aead/siphash@v1.0.1",
      "github.com/armon/go-metrics@v0.3.11",
      "github.com/axelarnetwork/tm-events@v0.0.0-20220427211200-9114fb26a603",
      "github.com/axelarnetwork/utils@v0.0.0-20220427210315-486bfb5d7157",
      "github.com/beorn7/perks@v1.0.1",
      "github.com/bgentry/speakeasy@v0.1.0",
      "github.com/btcsuite/btcd@v0.22.1",
      "github.com/btcsuite/btcd/chaincfg/chainhash@v1.0.1",
      "github.com/btcsuite/btclog@v0.0.0-20170628155309-84c8d2346e9f",
      "github.com/btcsuite/btcutil@v1.0.3-0.20201208143702-a53e38424cce",
      "github.com/cespare/xxhash/v2@v2.1.2",
      "github.com/coinbase/rosetta-sdk-go@v0.7.0",
      "github.com/confio/ics23/go@v0.7.0",
      "github.com/cosmos/btcutil@v1.0.4",
      "github.com/cosmos/cosmos-sdk@v0.45.4",
      "github.com/cosmos/go-bip39@v1.0.0",
      "github.com/cosmos/iavl@v0.17.3",
      "github.com/cosmos/ibc-go/v2@v2.2.0",
      "github.com/cosmos/ledger-cosmos-go@v0.11.1",
      "github.com/cosmos/ledger-go@v0.9.2",
      "github.com/cpuguy83/go-md2man/v2@v2.0.1",
      "github.com/davecgh/go-spew@v1.1.1",
      "github.com/deckarep/golang-set@v1.8.0",
      "github.com/desertbit/timer@v0.0.0-20180107155436-c41aec40b27f",
      "github.com/dvsekhvalnov/jose2go@v0.0.0-20200901110807-248326c1351b",
      "github.com/ethereum/go-ethereum@v1.10.17",
      "github.com/felixge/httpsnoop@v1.0.1",
      "github.com/fsnotify/fsnotify@v1.5.1",
      "github.com/go-kit/kit@v0.12.0",
      "github.com/go-kit/log@v0.2.0",
      "github.com/go-logfmt/logfmt@v0.5.1",
      "github.com/go-stack/stack@v1.8.0",
      "github.com/godbus/dbus@v0.0.0-20190726142602-4481cbc300e2",
      "github.com/gogo/gateway@v1.1.0",
      "github.com/gogo/protobuf@v1.3.3 => github.com/regen-network/protobuf@v1.3.3-alpha.regen.1",
      "github.com/golang/protobuf@v1.5.2",
      "github.com/golang/snappy@v0.0.4",
      "github.com/google/btree@v1.0.0",
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
      "github.com/hashicorp/golang-lru@v0.5.5-0.20210104140557-80c98217689d",
      "github.com/hashicorp/hcl@v1.0.0",
      "github.com/hdevalence/ed25519consensus@v0.0.0-20210204194344-59a8610d2b87",
      "github.com/improbable-eng/grpc-web@v0.14.1",
      "github.com/kkdai/bstream@v1.0.0",
      "github.com/klauspost/compress@v1.13.6",
      "github.com/lib/pq@v1.10.4",
      "github.com/libp2p/go-buffer-pool@v0.0.2",
      "github.com/magiconair/properties@v1.8.6",
      "github.com/mattn/go-isatty@v0.0.14",
      "github.com/matttproud/golang_protobuf_extensions@v1.0.1",
      "github.com/mimoo/StrobeGo@v0.0.0-20181016162300-f8f6d4d2b643",
      "github.com/minio/highwayhash@v1.0.2",
      "github.com/mitchellh/go-homedir@v1.1.0",
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
      "github.com/rcrowley/go-metrics@v0.0.0-20201227073835-cf1acfcdf475",
      "github.com/regen-network/cosmos-proto@v0.3.1",
      "github.com/rs/cors@v1.8.2",
      "github.com/rs/zerolog@v1.26.1",
      "github.com/russross/blackfriday/v2@v2.1.0",
      "github.com/shirou/gopsutil@v3.21.4-0.20210419000835-c7a38de76ee5+incompatible",
      "github.com/smallnest/chanx@v1.0.1-0.20211205150931-349643806662",
      "github.com/spf13/afero@v1.8.2",
      "github.com/spf13/cast@v1.4.1",
      "github.com/spf13/cobra@v1.4.0",
      "github.com/spf13/jwalterweatherman@v1.1.0",
      "github.com/spf13/pflag@v1.0.5",
      "github.com/spf13/viper@v1.11.0",
      "github.com/stretchr/testify@v1.7.1",
      "github.com/subosito/gotenv@v1.2.0",
      "github.com/syndtr/goleveldb@v1.0.1-0.20210819022825-2ae1ddf74ef7",
      "github.com/tendermint/btcd@v0.1.1",
      "github.com/tendermint/crypto@v0.0.0-20191022145703-50d29ede1e15",
      "github.com/tendermint/go-amino@v0.16.0",
      "github.com/tendermint/tendermint@v0.34.19",
      "github.com/tendermint/tm-db@v0.6.7",
      "github.com/tklauser/go-sysconf@v0.3.5",
      "github.com/tklauser/numcpus@v0.2.2",
      "github.com/zondax/hid@v0.9.0 => github.com/zondax/hid@v0.9.1-0.20220302062450-5552068d2266",
      "golang.org/x/crypto@v0.0.0-20220507011949-2cf3adece122",
      "golang.org/x/exp@v0.0.0-20220428152302-39d4317da171",
      "golang.org/x/mod@v0.6.0-dev.0.20220106191415-9b9b3d81d5e3",
      "golang.org/x/net@v0.0.0-20220412020605-290c469a71a5",
      "golang.org/x/sync@v0.0.0-20210220032951-036812b2e83c",
      "golang.org/x/sys@v0.0.0-20220520151302-bc2c85ada10a",
      "golang.org/x/term@v0.0.0-20210927222741-03fcf44c2211",
      "golang.org/x/text@v0.3.7",
      "google.golang.org/genproto@v0.0.0-20220505152158-f39f71e6c8f3",
      "google.golang.org/grpc@v1.46.0 => google.golang.org/grpc@v1.33.2",
      "google.golang.org/protobuf@v1.28.0",
      "gopkg.in/ini.v1@v1.66.4",
      "gopkg.in/yaml.v2@v2.4.0",
      "gopkg.in/yaml.v3@v3.0.0-20210107192922-496545a6307b",
      "nhooyr.io/websocket@v1.8.6"
    ],
    "cosmos_sdk_version": "v0.45.4"
  }
}
```



## \[GET] /blocks/latest

Get the latest block

#### Request

{% tabs %}
{% tab title="Curl" %}
```shell
curl https://axelar-mainnet-rpc.allthatnode.com:1317/blocks/latest \
--header "x-allthatnode-api-key: 'YOUR-API-KEY'"
```
{% endtab %}
{% endtabs %}

#### Response

```shell
{
  "block_id": {
    "hash": "9B730A69C6F42516A87E17CC83A3CD0E1D2974642E4267EEB2DE41E4BDC67DB7",
    "parts": {
      "total": 1,
      "hash": "C2280C28B141962726D84B3C66E0CD59066B3F528F6665B5D8DC3946282B2F02"
    }
  },
  "block": {
    "header": {
      "version": {
        "block": "11"
      },
      "chain_id": "axelar-dojo-1",
      "height": "2940949",
      "time": "2022-07-11T10:03:27.099134313Z",
      "last_block_id": {
        "hash": "66E75F34186903F2C15BF892ED24675101430E68C368544B76F937B72FD4AEA6",
        "parts": {
          "total": 1,
          "hash": "C7EB0EBAD4EEDE94353D158F43495FEF94C718A33EFF2182034F87044F8AD82D"
        }
      },
      "last_commit_hash": "8FDE9DECA72561BCCAE429165C305535CFE9CE006DB7658920F0EEE8A3B1A9CA",
      "data_hash": "E3B0C44298FC1C149AFBF4C8996FB92427AE41E4649B934CA495991B7852B855",
      "validators_hash": "4E5EF27DEB22B758C1AE7ADEF3EA2B93D83EA246570C9C9AD30C210DABBE11CD",
      "next_validators_hash": "4E5EF27DEB22B758C1AE7ADEF3EA2B93D83EA246570C9C9AD30C210DABBE11CD",
      "consensus_hash": "048091BC7DDC283F77BFBF91D73C44DA58C3DF8A9CBC867405D8B7F3DAADA22F",
      "app_hash": "D2E0B240B22B204ABFD92865821F142CA9CC9D1A7349EFFAAE52FF202C8D062D",
      "last_results_hash": "E3B0C44298FC1C149AFBF4C8996FB92427AE41E4649B934CA495991B7852B855",
      "evidence_hash": "E3B0C44298FC1C149AFBF4C8996FB92427AE41E4649B934CA495991B7852B855",
      "proposer_address": "D82FB64AC8E00DAB4E6AC6D9370023A2281B7256"
    },
    "data": {
      "txs": []
    },
    "evidence": {
      "evidence": []
    },
    "last_commit": {
      "height": "2940948",
      "round": 0,
      "block_id": {
        "hash": "66E75F34186903F2C15BF892ED24675101430E68C368544B76F937B72FD4AEA6",
        "parts": {
          "total": 1,
          "hash": "C7EB0EBAD4EEDE94353D158F43495FEF94C718A33EFF2182034F87044F8AD82D"
        }
      },
      "signatures": [
        {
          "block_id_flag": 2,
          "validator_address": "4C3EAD0A99B1B7F7AF9C45D41B0A7F7D7CE2D67B",
          "timestamp": "2022-07-11T10:03:27.080398193Z",
          "signature": "8XGLPhT65dHj0MDQByNjE1YTIG5z/RXMfEFV3teC57dwpkEUKMhF9zqHSIQxc5BKhykckg3Co98C+nA2Vj+yAg=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "C8E7FA98EAF061E786393C94AE29A5831EDE363E",
          "timestamp": "2022-07-11T10:03:27.070097714Z",
          "signature": "Srtrqu31bf0Wk43foGNQPVTeT8HdDz/BKYVzu6QpkQGejaT9deEbHsB92PUkthVrJXkzfi8yfPhsrShCrNPlBg=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "789DD85951E7F65FB5D0A073C522E9AB063D3134",
          "timestamp": "2022-07-11T10:03:27.117453821Z",
          "signature": "DWtfIEQ/zE5/Rnvg6diPwYFwF7khRS4is58koA4sTbgwo25iLkgqLDCy3+CfYjeR7VmVJULd8EJjYBuIdJGLAA=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "1B0B32283EC8C25615E391897A3C3C6926BBBFDA",
          "timestamp": "2022-07-11T10:03:27.118147802Z",
          "signature": "crc0pJTtD7/1ohFLZh/b4kNpzmSlguA2j4eHXMslUztS8UuNsdfPARoq6egNKRYid61uLUkuA40bX42jCiiCBw=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "B3AC06F1CFAE7748FBAB70BE762855762A44227A",
          "timestamp": "2022-07-11T10:03:27.36858273Z",
          "signature": "Siv7JiKFihy5YAGOiabZxo1xuvGUjhbpLrtVS8UueAMMhODW3aNsEnv6hopp/7KVWpRJyt79dTWDlzqzMP77DQ=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "D0318CE9996528B03B2B77D9811265921D252A8F",
          "timestamp": "2022-07-11T10:03:27.155974196Z",
          "signature": "yJhBnyrkzc6JZb4oLQN4C8i4I5yqrOwzzlRWBNQIe8ipx4bKSJ86yyh/vYX7zbZG5WuleKLWA8eFgQWE1VRlAw=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "B788CDCCE6A0C47CAA3B9E795554E67D7290AFE8",
          "timestamp": "2022-07-11T10:03:27.08604125Z",
          "signature": "N3YN2QON2zduc+cfhfGYkSYe8HJplEvPRuufoicqXIBcYgFSNfjHWQY8Xx6jd49+6nkKs17C6sgZSFMXXHqkAA=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "9D9F4C875BD335C4DA679047DAF9BD2ACA09F7A9",
          "timestamp": "2022-07-11T10:03:27.121453318Z",
          "signature": "ggHofRoQmEZMsBpVu+w1rI2i1Duke+7Skz8zPJuqBSSKKEFubqL2ehmh3bwrJ7DLmTeEbeLrm3B6w66xdsigCQ=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "D82FB64AC8E00DAB4E6AC6D9370023A2281B7256",
          "timestamp": "2022-07-11T10:03:27.140931724Z",
          "signature": "LO0eSuDztkFLNoq9mi/9/Fc7S7tv4Ejv28v9h4HeAeBS0qyUPTiRI/AeC6m6I4vm3Xnf8C3mvtakD6egzXxGCg=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "8F3695E65CBFB6D9084AFC0B637935E97CB3A381",
          "timestamp": "2022-07-11T10:03:27.235950108Z",
          "signature": "1RC5NbdX9RAce5ntceIZoFawqJ6YJlYC0tOg2m1hZoBollhUdf/DQqXYCkx6msUFTbaU7CZH4riHtJQU5Eo/Aw=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "5526E315D0C8F78B9DE7A6E60F7D518B91CE023C",
          "timestamp": "2022-07-11T10:03:27.082505097Z",
          "signature": "qLl5Q6CSLllr/0gv3tqyFv6/uyle6vDj/DdB3posO0v5oMsIMg6f1TZGmVbkkIloX4KgpjWpKjpWDKqFKdOuBA=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "7EC661F40BEFD355FEF828AF6462E574F4759D0B",
          "timestamp": "2022-07-11T10:03:27.1202463Z",
          "signature": "Aj/9Q+JuzrBouFEPJWxlOHi856za41qJausZLKmmTCiOkRFvkg3wl7FzimvWkf4dTaJtIz4CrR5sKA5Y3lVJCw=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "3F9F551064F148AF6615C892C8E9E76262A9ED61",
          "timestamp": "2022-07-11T10:03:27.124240163Z",
          "signature": "tcKwq0Ge1a2RCgsKxPtmZ92iOrnCbvrwAU6j1ZKZflN+7X+Lz1Fqb0TFL4NMuUu5g14KAB6qUA8PDW05F7rAAw=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "D94070533C76A164E37C0FA62A845A427CD34E40",
          "timestamp": "2022-07-11T10:03:27.062206647Z",
          "signature": "PbfPqjg8h1dwO+JHswhGHhCqt1wmgSIvmn9btPBlW3g0hWMq5UqLLTRlEJEmafGpeipZXp/sWP4aH0qAr9bFBQ=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "B83975807B9428E001FEBC6449FD2267F0E50DFF",
          "timestamp": "2022-07-11T10:03:27.099134313Z",
          "signature": "b5Elbxu0nhMa/ZLSGQssNBJ2M8PCSBcdWIWsH6AmWnUEh4MdlgrnUPYwzKQKNrvH7fS7oXioiZlGB7ygCTcqCA=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "3AAE040478D0B916EAE5B2EAE4B2C39D5F1EFCE6",
          "timestamp": "2022-07-11T10:03:27.046976395Z",
          "signature": "qN6+g53C8+OXaK88BoHIVcjxGNcHxBvRi0D9q+JvDm/dCXY9CY+lZwgB+AL5kCSPfIEkUBKP+R70LEo5K7CADA=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "9AA1BD7F54997CF32113104393DCEA7BC3BCE836",
          "timestamp": "2022-07-11T10:03:27.073974989Z",
          "signature": "+oGiC37QxuyRgb4BSKJfy/9NUxmZojLr9R1+nrxiFZLfrYR0/nm7Sdj/Ok6tLh9W1OOEOqZFfkFlCv4Janl9AA=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "B0F07A73B0402316F406EDFAF8863CCB140C88B4",
          "timestamp": "2022-07-11T10:03:27.068643709Z",
          "signature": "y2kiSAaS2e6Jp06Zb76t9E22noi5GF/X53kMSc00eIhj2I8CKZkGDqgmSSibvnZwv3gLMtgEeLIX/2zQSL8sCw=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "D6DD062792233D1799CB85CE3ECE1D925F7FCA93",
          "timestamp": "2022-07-11T10:03:27.084952715Z",
          "signature": "EtAb8YMSAYyTBcWLlU9wYpIg0iBQNeS/JaMRtFwDffxagahGSnmDEt+orYrHV23LrddVkD7WvC8d8mQrzOXNBA=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "518D2BF6CACD34AF9A797B442090168177FF4850",
          "timestamp": "2022-07-11T10:03:27.080106658Z",
          "signature": "N7pukSAapERY4dW6f3jI3j/GBxjwF86jZxlFUJpxClj/SLTk60n59xsSkcxeddPoOuS9auZuAucYPWAWYAqZDg=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "37632D04D893FFCF3BC8DEDD45BE2694BBF9A7B4",
          "timestamp": "2022-07-11T10:03:27.117839263Z",
          "signature": "2igsKr7/+inTT24QJq2jV6kjKf+rWa0b6LWSXq7ZwKGTx2ArQF99p75CZ3/jVNPbnmHU8Rx2frr+B5Qc4Ar4AQ=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "23409AB1B4B91F75DFE30511ED0A45CA00B02181",
          "timestamp": "2022-07-11T10:03:27.117133346Z",
          "signature": "bJb0wMQOEMD61mL/jaSz0s7rL1Cv5w2pp9tmnkc/Wi0EILrmdZlUAi6qhWVtMCbNzaRBYXpLgRbb2a8PdC6BDA=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "30806F8B712461E02DD89A574C40803F1B951A56",
          "timestamp": "2022-07-11T10:03:27.116865397Z",
          "signature": "fFaw94i3WgaqTnO/U2mZPYeH6lMRXcBwUKdx2UnOLuUtTtt9GkQf9fMLMNDqoAPIJk6kMo9nBJbOST6b62vtAQ=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "030EACE62A0FDC87356F9E2BE2C8EB2D8376F272",
          "timestamp": "2022-07-11T10:03:27.091041296Z",
          "signature": "UuYcTLPXQUlyvgBayHldaeHlsxgzLvQseM0Cdl2VLKcJTloW/Hce2DgyoPaBZ3kkz5VGncO5lemE7zkbA+l4Dg=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "1F2B40C34544868EA996FDD2BA13F1DCE3BF7A8D",
          "timestamp": "2022-07-11T10:03:27.13138453Z",
          "signature": "bt5ddtYgDU1xMoKyPu1MZ7P9fz71HeyTBj3YrKOABD7fAavru6ZYXyYG0/BIX3ruscs5qwTOwkKmBw4ZZQF4CA=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "3197C8328BCF200D00AC28909BEB99BAE57F7263",
          "timestamp": "2022-07-11T10:03:27.068818307Z",
          "signature": "0CQTOQMp7G2EPZ0Tdc6zdT+8qKe8ii9pG33cste1DebmUvlWG9cyW8x4VpWGNINdhx8p5py95FrUexKOLeY3Dg=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "40CACE4ECEBBCC24EB1192B93B2A912A0980FAE4",
          "timestamp": "2022-07-11T10:03:27.087926898Z",
          "signature": "ec7TYcEymQdSmb5Sc5KZS8hY5MoG4BvxZpO1c1ddQE3yG28oy0XKuvk6NsoadhLsZphdlD5T4hyABdBwfw4AAg=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "4338C4CDE85BFCF4F04E2ECBCBF7007DD93185FA",
          "timestamp": "2022-07-11T10:03:27.079306254Z",
          "signature": "jS7Ta3QMKkoVfOouXV1Phdu3hgtfDR4wenrE41ktKuBt2O8Td1lUqFWp6dz6/zyydjmBbtY0gN7K4ch+flTbDg=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "48181C41E43158F0ADE8011C86CF715BE87BD7F4",
          "timestamp": "2022-07-11T10:03:27.063093605Z",
          "signature": "TrevdTnBt6uUMo1aWZhgQxC+yyehZ6c6+9NSWTkJMK/afLXbXaC+fHHO7pJZNpLelOcQkdz7Awzfx61UkCbwDg=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "779E0D0690544828BAE8756036154E1C4659605A",
          "timestamp": "2022-07-11T10:03:27.105272926Z",
          "signature": "2RXRUwrarefkuJF9PNVhyTMZbuKUP+nzRbfuO9Oi+LTYXgju5iqRWM9IsgeheX2cpqnIdLZAFQi54zRhkTEDDQ=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "84ED9241C7520AE31F04F9759A2750118A97034C",
          "timestamp": "2022-07-11T10:03:27.074079962Z",
          "signature": "nTwXr6t5Ye7wx99e0JR4Yu3qc+EjnDhf9xMlVXCJUa7UpraZq33aCNeiPHs/jGTis+lGg8XLd01lpJG+k3v9CQ=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "85F3D82818E7BA6C639CB094664326F5001CF3FA",
          "timestamp": "2022-07-11T10:03:27.179045714Z",
          "signature": "XysWp0eUuTI/h+cljcuynBW+/G/eYI5fqyZhJp6gX27wPxs2QVB5Tr2iAj5s+1Ur1VICFDMKVml88QMlBZtICQ=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "8740C9E2428E2D8B5B2002552E0D2880EC6E1AB0",
          "timestamp": "2022-07-11T10:03:27.083894918Z",
          "signature": "FdJbstGkHDsn1xDcthPmwaHmd8TA2mRlmHNYr4fPsdfJeX+vZMupv1m7rPc/K3SCVFxoU2tx1AqN2/YnoiC5CQ=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "B286F6A0BD3CD35B1940860A4D912C32FC2D1863",
          "timestamp": "2022-07-11T10:03:27.082139818Z",
          "signature": "jTg7HJs5JX2h/BEWhgNJO4Gu+bRw8pQ1gNjmkP0Zu28IeEKb/dHdQEaLbtoPlzVHt4TozhUhCj269/aSoonODQ=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "EE8637A0EF75B3359F35B9AE75DCAB6349288503",
          "timestamp": "2022-07-11T10:03:27.085987268Z",
          "signature": "I56xPEoqA0SWkfh+EigrT7Yxh2q8ro70OqWkcTsFLEKA/CAnYxzriDikjQWcw6zmDScdjO9bZ489kKs7nhc+Ag=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "0B7EA0F411F506695D41F188343B3FB5F4CF789C",
          "timestamp": "2022-07-11T10:03:24.155935052Z",
          "signature": "y/+mtyA2kMzEnPSkgCrDzTYaBp1aiNTa8yXFRVv0/a36kC3K8schabqGLXK69bo7dS54Zk4aNEAcZf3O6Xk+Dg=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "20DA32578EC9F1BBDF8F0FF9A53543D74970EF93",
          "timestamp": "2022-07-11T10:03:27.125121865Z",
          "signature": "aTyQ8Saaus4qj3Da6wzofVd8ImkbTFm2gTGBeqfc22JlU2P6Ar1sr8hvLraUxvQIVmoxe5zxs4u+m5tSAaPSDA=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "C90202CD6B99F72E0534D770D9A31FE6883A1D38",
          "timestamp": "2022-07-11T10:03:27.071738044Z",
          "signature": "UmoxgVWGoFWjMe4VgK6Ehcjjl4b+eKZ+vEHdeHE6aDCTSveo4032B6av1bxc6LaGrwVUi4lis7wWBnVEFqfqBw=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "CA096A52D10DAAC7F5D295C7FF47EBD8DB4D43C9",
          "timestamp": "2022-07-11T10:03:27.241914187Z",
          "signature": "uqnpWY3IZOoV3OeRLpJFXuV6Kw2qnN9oOO9Z6iBMHGh3Yu8cocKSvKBAY99w2j4T637oo77zSRJStzgMRKj3AQ=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "CA1086B803C8AC4E754CCF1842B8EAA8ADC17292",
          "timestamp": "2022-07-11T10:03:27.079329336Z",
          "signature": "13L20BH1Sg8kgPcEG5r6sYRsAkztSf8ttWKLvO35EGWtu2mFrcJKGOy0yUjS09sU+XZ9bz6ZuOPxwq2xODM+DA=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "E4A24DB1D897A34DAF23CDF190B16934935E70CF",
          "timestamp": "2022-07-11T10:03:27.096181139Z",
          "signature": "zzTIuKGAloISItPsPepmHST9zOYRMn2eipms+Hy84SOgayh8Dn8CUCIe5jNLMl1OyzfEMcxM8w4DiOi6umt0AQ=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "6785F6FCD6C90B500964ABCE41FB7DF9B2DD4515",
          "timestamp": "2022-07-11T10:03:27.124875674Z",
          "signature": "IYRhltJVj4KxSGN/lzhs4W+5kyGFxXqLVGrDGYVCjiAkt7qzeCwNcppltxt6TbKQWEhQfOQTDMcbNc2CD9h9AA=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "81DA03EFE16079C6197C2949D3F82F835E19B90C",
          "timestamp": "2022-07-11T10:03:27.082143894Z",
          "signature": "lMgyqvqgtq3U5JPvtBHhr5CBxvwvfScjNpKlJ8QT9doZyIFGeomaRMBlb4+aVTwfhLtYhb2h9N4qDd1Yc/e8Bw=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "C6282A161258D8232DCE0E81A7D8F021E7A8BC26",
          "timestamp": "2022-07-11T10:03:27.096242054Z",
          "signature": "j2yrbjkuiX8MMHYrcX20Q3aE0Zkb6M123fMwo9U4JtrvMPrSkfirosaPaxvF9iDUTbCA88D3OxJ2M2dZR41eBg=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "6A6D5C2FA9CE7DE300D89C703132681D69155131",
          "timestamp": "2022-07-11T10:03:27.078956464Z",
          "signature": "aeLuhFTpPJ9YNKQeVNTmJbA92RxJfCBHNJ7dP6U6VBawlDbYORCX2VnvkZCvrL6w8wGfqvYDTSzlSfxnmTV7DQ=="
        }
      ]
    }
  }
}

```
