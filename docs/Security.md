# Security implification for Cosmos Node

## Network

A Cosmos Network uses the following ports:

- `26656/tcp` - a p2p port to communicate between nodes.
- `26657/tcp` - a Tendermint RPC port. Should be disabled for incoming requests from the public Internet.
- `26658/tcp` - a ABCI port. Should be disabled for incoming requests from the public Internet.
- `26660/tcp` - a Tendermint Prometheus metrics
- `9090/tcp` - a Cosmos SDK gRPC API port
- `1317/tcp` - a Cosmos SDK HTTP REST port 
- `6060/tcp` - a pprof debugger port

Depending on your Node's role allowed ports set may vary. 

Best practises suggest to always limit ports to only local usage. Use a proxy server (e.g. nginx) installed on the node to provide external access. The proxy server may apply additional security level both for HTTP REST and gRPC calls (TLS, rate-limiting, whitelisting and e.g.)


Credits:
- https://docs.cosmos.network/v0.47
- https://forum.cosmos.network/t/what-ports-does-gaiad-use/444
- https://medium.com/@kidinamoto/tech-choices-for-cosmos-validators-27c7242061ea
- https://medium.com/forbole/a-step-by-step-guide-to-join-cosmos-hub-testnet-e591a3d2cb41

## Hardening

- Configure remote access (basically SSH)
  - No root access (or with private keys only)
  - No password login
  - No port forwardning


## Integrity checks

An integrity software (AIDE in linux) can lockdown the system configuration and warn you in case of unauthorized changes.

You should track down the following files (beside the default recommended rules):

- `${GAIA_HOME}/config/config.toml` - configuration for daemon `gaiad`.
- `${GAIA_HOME}/config/client.toml` - configuration for CLI part `gaiad`.
- `${GAIA_HOME}/config/node_key.json` - node key.
- `${GAIA_HOME}/config/priv_validator_key.json` - validator key.