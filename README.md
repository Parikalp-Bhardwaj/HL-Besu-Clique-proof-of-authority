# HL-Besu-Clique-proof-of-authority

In Clique networks, approved accounts, known as signers, validate transactions and blocks. Signers take turns to create the next block.


We are creating a Private blockchain with 4 nodes In this 4 nodes one will be bootnode and others will be validators.

# Get the address for Node-1

In Clique networks, you must include the address of at least one initial signer in the genesis file. For this Clique network, we’ll use `Node-1` as the initial signer. This requires obtaining the address for Node-1

To get the address for Node-1, in the Node-1 directory,

```
docker-compose ./generate-key/docker-compose.yaml up -d
```

Now you will get `data` folder inside `./generate-key/data`. Copy the `data` folder and past to `./Node-1/data/`

# Create the genesis file

The genesis file defines the genesis block of the blockchain (that is, the start of the blockchain). The Clique genesis file includes the address of `Node-1` as the initial signer in the extraData field.

Copy the `./Node-1/node1Address` excluding the 0x prefix.



Now inside the `./Node-1/cliqueGenesis.json` In extraData, replace <Node 1 Address> with the address for `Node-1/data/node1Address`, excluding the 0x prefix.

## Before
```
{
  ...
"extraData": "0x0000000000000000000000000000000000000000000000000000000000000000<Node 1 Address>0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000",
  ...
}
```

## After
```
{
...
"extraData":"0x0000000000000000000000000000000000000000000000000000000000000000b9b81ee349c3807e46bc71aa2632203c5b4620340000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000",
  ...
}
```

Same thing we will do with `./Node-2/cliqueGenesis.json`,`./Node-3/cliqueGenesis.json`, `./Node-4/cliqueGenesis.json`

`./Node-2/cliqueGenesis.json` In extraData, replace <Node 1 Address> with the address for `Node-1/data/node1Address`, excluding the 0x prefix.

`./Node-3/cliqueGenesis.json` In extraData, replace <Node 1 Address> with the address for `Node-1/data/node1Address`, excluding the 0x prefix.

`./Node-4/cliqueGenesis.json` In extraData, replace `<Node 1 Address>` with the address for `Node-1/data/node1Address`, excluding the 0x prefix.


# Start the first node as the bootnode

 ```
 docker-compose -f ./Node-1/docker-compose.yaml up -d
 ```
 
 When the node starts, the `enode URL` displays. Copy the enode URL to specify Node-1 as the bootnode in the following steps.
 
 ![App Screenshot](https://besu.hyperledger.org/en/stable/assets/images/EnodeStartup.png)
 
 You will get the encode url copy encode url and past `./Node-2/config.toml` 
 `
 bootnodes=["enode://d2316b2386f364c960f443e4c415f829cd6f8e3aa889eb81ee9f8f9c50fffbf16dee0ffb822904054a72b8477aa1083e3112b5d5ae95907eefb834f417f23262@127.0.0.1:30303"]
 `
 
 Same thing we will do with `./Node-2/config.toml`,`./Node-3/config.toml`, `./Node-4/config.toml`

Now let's run four nodes 

```
docker-compose -f docker-compose.yaml up -d
```
 


