### geth 启动
dev启动： ./geth --dev --http --http.api eth,web3,net --http.corsdomain "https://remix.ethereum.org"     
--keystore /Users/yincong/Library/Ethereum/keystore --password  /Users/yincong/go/src/github.com/yincongcyincong/go-ethereum/build/bin/passwd1.txt    

正常启动：./geth --syncmode snap --gcmode archive    

light已经不可用    

### geth交互    
geth attach <datadir>/geth.ipc socket文件在日志里面查找    

### wallet创建
clef init --configdir /home/user/go-ethereum/clefdata     
clef newaccount --keystore sepolia-data/keystore    
记住密码，/Users/yincong/go/src/github.com/yincongcyincong/go-ethereum/build/bin/passwd1.txt 里面写明文密码

使用https://docs.web3js.org/web3_playground/    可以拿到private key
```
web3.eth.accounts.decrypt('{"address":"e413eeff4636947bc4f6c9a09222b57e861aaf07","crypto":{"cipher":"aes-128-ctr","ciphertext":"c07773716bc28907cf6fbead3dfecabfbc1fb948b414898aaa722fcfa6affb31","cipherparams":{"iv":"d6f14d40c3213580cf6a62931c2cfbf6"},"kdf":"scrypt","kdfparams":{"dklen":32,"n":262144,"p":1,"r":8,"salt":"7978963ce27b2cd17f10c1f4b47b288fd6d0a239ee94b02c411aafb1c1c5e74c"},"mac":"cc3de7a04763f7c3755cf5ded68ed14a0c8b67220b0f56a5c9562a823e6287a4"},"id":"d86a88b3-e2ae-45bb-92d4-0d8116e11679","version":3}', '123')
```
