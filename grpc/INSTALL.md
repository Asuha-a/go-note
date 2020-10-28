# INSTALL.md

## protocol buffer compilerをインストールする

gRPCを使うのにprotocol bufferは必須では無いがデファクトスタンダードになっている。  
ここではversion3のproto3を使用する。  
proto3: protocol buffer language  
protoc: protocol buffer compiler  
protocは.protoファイルをコンパイルするために使う。  

Linux

```terminal
PROTOC_ZIP=protoc-3.7.1-linux-x86_64.zip
curl -OL https://github.com/protocolbuffers/protobuf/releases/download/v3.7.1/$PROTOC_ZIP
sudo unzip -o $PROTOC_ZIP -d /usr/local bin/protoc
sudo unzip -o $PROTOC_ZIP -d /usr/local 'include/*'
rm -f $PROTOC_ZIP
```

```terminal
libprotoc 3.0.0
```

などと表示される。  

## 必要なライブラリをインストールする

プロジェクトを初期化しgo.modを作る。

```terminal
go mod init
```

```terminal
go get google.golang.org/protobuf/cmd/protoc-gen-go \
         google.golang.org/grpc/cmd/protoc-gen-go-grpc
```

上でprotoc-gen-go-grpcがインストールできなかったら下記を実行

```terminal
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
[Cannot go-get protoc-gen-go-grpc with a specific version](https://github.com/grpc/grpc-go/issues/3727)
[Installing protoc](http://google.github.io/proto-lens/installing-protoc.html)