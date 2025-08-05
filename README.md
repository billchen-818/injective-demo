# README

## Counter合约说明

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

## ExchangeDemo合约说明

### 部署

```sh
forge create --rpc-url https://k8s.testnet.json-rpc.injective.network --private-key ${PRIKEY} --broadcast src/ExchangeDemo.sol:ExchangeDemo
```

输出合约地址:0xf46D6803E479C90a927157f37711125059abc7Fb

### 验证合约

```sh
forge verify-contract --rpc-url https://k8s.testnet.json-rpc.injective.network --verifier blockscout --verifier-url 'https://testnet.blockscout-api.injective.network/api/' 0xf46D6803E479C90a927157f37711125059abc7Fb src/ExchangeDemo.sol:ExchangeDemo
```

### 充值点资金

```sh
injectived q exchange inj-address-from-eth-address 0xf46D6803E479C90a927157f37711125059abc7Fb
```

inj173kksqly08ys4yn32lehwygj2pv6h3lmkau8tv

可以直接在kelp钱包中转账到这个地址。

### 存一个ING

```sh
cast send --rpc-url https://k8s.testnet.json-rpc.injective.network --private-key ${PRIKEY} 0xf46D6803E479C90a927157f37711125059abc7Fb "deposit(string,string,uint256)" "0xf46D6803E479C90a927157f37711125059abc7Fb000000000000000000000001" "inj" 1000000000000000000
```

### 创建现货卖单

```sh
cast send --rpc-url https://k8s.testnet.json-rpc.injective.network --private-key ${PRIKEY} 0xf46D6803E479C90a927157f37711125059abc7Fb "createSpotLimitOrder((string,string,string,uint256,uint256,string,string,uint256))" '('0x0611780ba69656949525013d947713300f56c37b6175e02f26bffa495c3208fe','0xf46D6803E479C90a927157f37711125059abc7Fb000000000000000000000001','inj1zyg3zyg3zyg3zyg3zyg3zyg3zyg3zyg3t5qxqh',40, 1,"my-order-001","sell", 0)'
```

### 取消卖单

```sh
cast send --rpc-url https://k8s.testnet.json-rpc.injective.network --private-key ${PRIKEY} 0xf46D6803E479C90a927157f37711125059abc7Fb "cancelSpotOrder(string,string,string,string)" '0x0611780ba69656949525013d947713300f56c37b6175e02f26bffa495c3208fe' '0xf46D6803E479C90a927157f37711125059abc7Fb000000000000000000000001' '0xc499df8df064f66c2dea1d45da1606d5221c04aa67e6f4a342dc6926db1a97b6' "my-order-001"
```

这里的orderhash就是上一步的交易hash.