# poc-ethereum - test networks
Ethereum configuration to work in private network.

Install geth, see https://github.com/ethereum/go-ethereum/wiki/Building-Ethereum.

### Configuration

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

Initialize node.
```shell
geth --fast --cache=2048 --jitvm --rpc  --datadir "/path/ethereum/data"
```

### Console

Attach console via ipc file.
```shell
geth attach /path/ethereum/data/geth.ipc
```
Set default account.
```javascript
web3.eth.defaultAccount = '0xbed632ceb41f15983cca84f67203696b6ab499ab'
```
Set ether database.
```javascript
miner.setEtherbase(personal.listAccounts[0])
```
Get balance account.
```javascript
web3.fromWei(web3.eth.getBalance(web3.eth.accounts[0]), "ether")
```
Set extra data
```javascript
miner.setExtra("renato.guimaraes")
```
Hash time estimate
```javascript
etm = eth.getBlock("latest").difficulty / eth.hashrate
Math.floor(etm / 3600.) + "h " + Math.floor((etm % 3600)/60) + "m " +  Math.floor(etm % 60) + "s"
```
Start mining with thread numbers.
```javascript
miner.star(4)
```
Stop mining.
```javascript
miner.stop()
```
