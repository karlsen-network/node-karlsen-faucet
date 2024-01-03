# Karlsen Faucet

Miniature Karlsen faucet website based on [Karlsen Wallet](https://github.com/karlsen-network/node-karlsen-wallet)
framework. The faucet can be run on single or multiple networks.
In case you run it on multiple networks it will use the same
seed phrase for all together.

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

## Configuration

You need to have a hCaptcha subscription. You can create a free one
at: https://www.hcaptcha.com/

Once you have created it copy the `sitekey` and `secret` into
`config/karlsen-faucet.conf` file.

Lastly you need to create a file `.seeds` with the 12-word seed
phrase of a wallet to disable address derivation. This is optional
but recommended if you run the faucet on a secure and privately
owned system.

It is highly recommended to run the faucet behind a reverse proxy
like NGINX and add the following header into your proxy
configuration:

```
proxy_set_header X-Real-IP $remote_addr;
```

It will ensure that single IP addresses cannot empty the faucet and
limit their amount in the 24 hour timeframe.

## Running

```
git clone https://github.com/karlsen-network/node-karlsen-faucet
cd node-karlsen-faucet
npm install
node karlsen-faucet.js --testnet --host 0.0.0.0 --limit 100 --rpc 127.0.0.1:42210
```
