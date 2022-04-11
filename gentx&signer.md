# Sistem Gereksinimleri
- 4 GB RAM, x64 2.0 GHz 2v CPU
- 512 GB SSD

# Güncellemeler
``` 
apt update
sudo apt-get install git curl build-essential make jq -y
```

# Go Yüklemek
```
curl https://dl.google.com/go/go1.17.6.linux-amd64.tar.gz | sudo tar -C/usr/local -zxvf -
```
```
cat <<'EOF' >>$HOME/.profile
export GOROOT=/usr/local/go
export GOPATH=$HOME/go
export GO111MODULE=on
export PATH=$PATH:/usr/local/go/bin:$HOME/go/bin
EOF
```
```
source $HOME/.profile
go version
```

# Genxt
```
git clone https://github.com/archway-network/archway
cd archway
git checkout main
make install
```
archwayd version
 "0.0.5"

```
HOMEDIR=/root/.archway
archwayd config chain-id torii-1 --home $HOMEDIR
archwayd config node https://rpc.torii-1.archway.tech:443 --home $HOMEDIR
archwayd init <Your-Moniker> --chain-id torii-1 --home $HOMEDIR
wget https://raw.githubusercontent.com/archway-network/testnets/main/torii-1/penultimate_genesis.json
cp penultimate_genesis.json $HOMEDIR/config/genesis.json
archwayd keys add <key-name> --home $HOMEDIR
archwayd add-genesis-account $(archwayd keys show <key-name> -a --home $HOMEDIR)  1001000utorii --home $HOMEDIR

archwayd gentx my-key 1000000utorii \
  --commission-rate 0.1 \
  --commission-max-rate 0.1 \
  --commission-max-change-rate 0.1 \
  --pubkey $(archwayd tendermint show-validator --home $HOMEDIR) \
  --chain-id torii-1
  ```

Github PR: https://github.com/archway-network/testnets/tree/main/torii-1/gentx
Signer: https://github.com/archway-network/testnet-signer 
