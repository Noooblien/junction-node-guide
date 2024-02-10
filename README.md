# Installation Guide

## Go Installation

First, download and install Go programming language:
```bash
sudo apt install build-essential
```

```bash
wget https://dl.google.com/go/go1.20.6.linux-amd64.tar.gz
sudo tar -C /usr/local -xzf go1.20.6.linux-amd64.tar.gz
export PATH=$PATH:/usr/local/go/bin
source ~/.profile
go version
```

## Ignite Installation

Next, download and install Ignite:
```bash
wget https://github.com/ignite/cli/releases/download/v0.27.1/ignite_0.27.1_linux_amd64.tar.gz

chmod +x ignite_0.27.1_linux_amd64.tar.gz

tar -xvf ignite_0.27.1_linux_amd64.tar.gz

sudo mv ignite /usr/local/bin

ignite version
```

## Junction Node Installation
TO Start a Junction Node, you need to install the Junction Node software. You can install the software by running the following commands:

```bash
git clone https://github.com/airchains-network/junction.git
cd junction

git checkout v0.0.2-beta

ignite chain build

rm -rf ~/.junction

$HOME/go/bin/junctiond init <moniker>

cp resources/genesis/genesis.json ~/.junction/config/genesis.json

$HOME/go/bin/junctiond start --api.enable   --api.address "tcp://0.0.0.0:1317" --rpc.laddr "tcp://0.0.0.0:26657" --p2p.laddr "tcp://0.0.0.0:26656"  --p2p.persistent_peers="009075e1d1b0989ab2d0563c9e7454eb6c320772@35.200.232.241:26656" --minimum-gas-prices ="0.0001dair"
```

## Status Check
To check the status of the node, run the following command:
```bash
$HOME/go/bin/junctiond status
```

## Junction Validator Node
After the Catching is False, you can create a validator node.

```bash
$HOME/go/bin/junctiond keys add <key-name>

$HOME/go/bin/junctiond tx staking create-validator \
--amount=58stake \
--pubkey=$($HOME/go/bin/junctiond tendermint show-validator) \
--moniker=<moniker> \
--chain-id=junction \
--commission-rate="0.05" \
--commission-max-rate="0.10" \
--commission-max-change-rate="0.01" \
--min-self-delegation="1" \
--gas="200000" \
--fees="2stake" \
--from=<key-name> -y

$HOME/go/bin/junctiond query tendermint-validator-set
```

