# INSTALL.md
## protocol buffer compilerをインストールする
gRPCを使うのにprotocol bufferは必須では無いがデファクトスタンダードになっている。  
ここではversion3のproto3を使用する。  
proto3: protocol buffer language  
protoc: protocol buffer compiler  
protocは.protoファイルをコンパイルするために使う。  

Linux

```
sudo apt install -y protobuf-compiler
protoc --version
```

```
libprotoc 3.0.0
```
などと表示される。  

## 必要なライブラリをインストールする。

プロジェクトを初期化しgo.modを作る。

```
go mod init
```

```
go get google.golang.org/protobuf/cmd/protoc-gen-go \
         google.golang.org/grpc/cmd/protoc-gen-go-grpc
```

上でprotoc-gen-go-grpcがインストールできなかったら下記を実行
```
go get -u -v google.golang.org/grpc/cmd/protoc-gen-go-grpc@master
```

go.modに各ライブラリが追加されている。  

```go.mod
module github.com/Asuha-a/grpc-go-test

go 1.15

require (
	google.golang.org/grpc/cmd/protoc-gen-go-grpc v1.0.0 // indirect
	google.golang.org/protobuf v1.25.0 // indirect
)
```

## References
[Protocol Buffer Compiler Installation](https://grpc.io/docs/protoc-installation/)
[Quick start-gRPC](https://grpc.io/docs/languages/go/quickstart/)