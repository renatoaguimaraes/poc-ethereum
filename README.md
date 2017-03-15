# poc-ethereum
Ethereum configuration to work in private network.

Install geth, see https://github.com/ethereum/go-ethereum/wiki/Building-Ethereum.

Initialize node.
```shell
geth --datadir "/path/ethereum/data"
```

Stop node.
```shell
ctrl+c
```

Create new account.
```shell
geth --datadir "/path/ethereum/data" account new
```

Create CustomGenesis.json
```json
{
    "nonce": "0x0000000000000042",     "timestamp": "0x0",
    "parentHash": "0x0000000000000000000000000000000000000000000000000000000000000000",
    "extraData": "0x0",     
    "gasLimit": "0x8000000",     
    "difficulty": "0x400",
    "mixhash": "0x0000000000000000000000000000000000000000000000000000000000000000",
    "coinbase": "0x3333333333333333333333333333333333333333",     
    "alloc": {
            "0xbed632ceb41f15983cca84f67203696b6ab499ab": {
           	    "balance": "10015200000000000000000"
            }
    }
}
```

Configure custom node.
```json
geth --datadir "/path/ethereum/data" init CustomGenesis.json
```

Initialize node on miner mode.
```shell
geth --fast --cache=2048 --jitvm --rpc  --datadir "/path/ethereum/data" --mine
```
