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

