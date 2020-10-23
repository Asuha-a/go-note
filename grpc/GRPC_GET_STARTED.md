# GRPC_GET_STARTED.md
## Hello World
恒例Hello World
リポジトリをクローン

```
git clone git@github.com:grpc/grpc-go.git
```
helloworldディレクトリにすでにプロジェクトを作ってくれている

```
cd grpc-go/examples/helloworld
```

サーバを起動

```
go run greeter_server/main.go
```

すると次のようなログが出て動かなくなる。

```
go: downloading google.golang.org/genproto v0.0.0-20200806141610-86f49bd18e98
go: downloading golang.org/x/net v0.0.0-20200707034311-ab3426394381
go: downloading golang.org/x/sys v0.0.0-20200803210538-64077c9b5642
go: downloading golang.org/x/text v0.3.3
```
処理が遅いわけではなく誰かがアクセスしてくるのを待っているだけなので**新しいターミナルで**クライアントを実行する。

```
go run greeter_client/main.go
```

するとサーバはログを出力し、

```
2020/10/23 16:51:06 Received: world
```

クライアントはサーバから帰ってきたレスポンスを出力する。

```
2020/10/23 16:51:06 Greeting: Hello world
```
これでgRPCを使った通信に成功しました。  

## References
[Quick start-gRPC](https://grpc.io/docs/languages/go/quickstart/)