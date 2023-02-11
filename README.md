# HL-Besu-Clique-proof-of-authority

In Clique networks, approved accounts, known as signers, validate transactions and blocks. Signers take turns to create the next block.


We are creating a Private blockchain with 4 nodes In this 4 nodes one will be bootnode and others will be validators.

# Get the address for Node-1

In Clique networks, you must include the address of at least one initial signer in the genesis file. For this Clique network, we’ll use `Node-1` as the initial signer. This requires obtaining the address for Node-1

To get the address for Node-1, in the Node-1 directory,

```
docker-compose ./generate-key/docker-compose.yaml up -d
```
