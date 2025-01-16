1. 只能打开一个带有go.mod的文件夹

2. 执行这种类型的命令 /Users/yincong/go/pkg/mod/golang.org/toolchain@v0.0.1-go1.22.4.darwin-arm64/bin/go list -modfile=/Users/yincong/go/src/github.com/yincongcyincong/go-ethereum/go.mod -m -json -mod=mod all

3. 更新gomod的环境变量，并且不点gomod自动下载的选项。

   ### go开源
   1. 进入src目录有all.sh（执行编译和单测）和make.sh（执行编译），但是编译需要有./bin/go的二进制，执行完成之后才会在goland里面展示这个源的go版本
   2. 执行完成编译之后可以在idea里面选择自己编译的路径就能用自己新编译的go
   3. 提代码直接提github，会同步到gerrit
