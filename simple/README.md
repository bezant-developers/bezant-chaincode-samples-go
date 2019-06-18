# `Go Chaincode` simple code
This tutorial will explain how to write `Hyperledger Fabric` chain code based on `Go`


# `Chaincode` development example
Writing your own chain code requires an understanding of the `Fabric` platform, `Go`. An application is a basic example chain code that creates assets (key-value pairs) on a ledger.

``Put``
```bash
docker exec cli peer chaincode invoke -o orderer.example.com:7050 -C bezant-channel -n simple-go --peerAddresses peer0.bezant.example.com:7051 -c '{"Args":["put", "a", "10"]}'
```

``Get``
```bash
docker exec cli peer chaincode query -C bezant-channel -n simple-go --peerAddresses peer0.bezant.example.com:7051 -c '{"Args":["get", "a"]}'
```

``PutByWalletAddress``
```bash
docker exec cli peer chaincode invoke -o orderer.example.com:7050 -C bezant-channel -n simple-go --peerAddresses peer0.bezant.example.com:7051 -c '{"Args":["putByWalletAddress", "10"]}'
```

``Instantiate``
```bash
docker exec cli peer chaincode install -n simple-go -v 1.0 -p simple-go
docker exec cli2 peer chaincode install -n simple-go -v 1.0 -p simple-go                                                                                            
docker exec cli peer chaincode instantiate -o orderer.example.com:7050 -C bezant-channel -n simple-go -v 1.0 -c '{"Args":["init"]}'               
```

``Upgrade``
```bash
docker exec cli peer chaincode install -n simple-go -v 1.1 -p simple-go
docker exec cli2 peer chaincode install -n simple-go -v 1.1 -p simple-go                                                                                            
docker exec cli peer chaincode upgrade -o orderer.example.com:7050 -C bezant-channel -n simple-go -v 1.1 -c '{"Args":["init"]}'               
```