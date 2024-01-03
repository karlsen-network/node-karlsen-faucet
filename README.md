# Karlsen Faucet

Miniature Karlsen faucet website based on [Karlsen Wallet](https://github.com/karlsen-network/node-karlsen-wallet)
framework.

## Setup Karlsend

```
git clone https://github.com/karlsen-network/karlsend
cd karlsend
go build
cd cmd/karlsenminer
go build
```

## Run Karlsend Testnet

Terminal 1:

```
cd karlsend
karlsend --utxoindex --testnet
```

Terminal 2:

```
cd karlsend/cmd/karlsenminer
karlsenminer --miningaddr=karlsentest:qpuyhaxz2chn3lsvf8g7q5uvaezpp5m7pyny4k8tyq --mine-when-not-synced --testnet
```

## Running

```
git clone https://github.com/karlsen-network/node-karlsen-faucet
cd node-karlsen-faucet
npm install
node karlsen-faucet
```

## Development Environment

To setup development environment for debugging `karlsen-wallet` and
`karlsencore-lib` modules:

### Setup TypeScript

```
npm install -g typescript
tsc -v
```

`tsc` should yield 4.0.5 or higher.

### Clone and setup repositories

git clone https://github.com/karlsen-network/node-karlsen-faucet
git clone https://github.com/karlsen-network/node-karlsen-wallet
git clone https://github.com/karlsen-network/node-karlsen-core-lib
cd node-karlsen-core-lib
npm link
cd ..
cd node-karlsen-wallet
npm link
npm link karlsen-core-lib
cd ..
cd node-karlsen-faucet
npm install
npm link karlsen-wallet
cd ..

Terminal 1:

```
cd node-karlsen-wallet
tsc --watch
```

Terminal 2:

```
cd node-karlsen-faucet
node karlsen-faucet
```

`node karlsen-faucet` will attempt to bind to all available networks.
You can use `--devnet` and `--testnet` flags to have it bind to a
single network.
