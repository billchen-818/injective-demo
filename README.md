# README

## 说明

### 部署

```sh
forge create --rpc-url https://k8s.testnet.json-rpc.injective.network --private-key ${PRIKEY} --broadcast src/Counter.sol:Counter
```

部署时输出的合约地址：0x47acCeD93cB1cafa4F43Fa0A8152977435AD8C41

### 验证

```sh
forge verify-contract --rpc-url https://k8s.testnet.json-rpc.injective.network --verifier blockscout --verifier-url 'https://testnet.blockscout-api.injective.network/api/' 0x47acCeD93cB1cafa4F43Fa0A8152977435AD8C41 src/Counter.sol:Counter
```

### 查询

```sh
cast call --rpc-url https://k8s.testnet.json-rpc.injective.network 0x47acCeD93cB1cafa4F43Fa0A8152977435AD8C41 "value()" 
```

### 调用

```sh
cast send --rpc-url https://k8s.testnet.json-rpc.injective.network --private-key ${PRIKEY} 0x47acCeD93cB1cafa4F43Fa0A8152977435AD8C41 "increment(uint256)" 4
```

### 查询

```sh
cast call --rpc-url https://k8s.testnet.json-rpc.injective.network 0x47acCeD93cB1cafa4F43Fa0A8152977435AD8C41 "value()" 
```