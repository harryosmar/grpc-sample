## setup

https://grpc.io/docs/languages/go/quickstart/

### 1. GO PATH

Make sure gopath has been setup and added to path

```
export PATH="$PATH:$(go env GOPATH)/bin"
```


### 2. Protocol Compiler/protoc/ProtoBuf

https://github.com/protocolbuffers/protobuf/releases
https://grpc.io/docs/protoc-installation/

```
	curl -OL https://github.com/protocolbuffers/protobuf/releases/download/v3.17.3/protoc-3.17.3-osx-x86_64.zip \
	&& unzip -o protoc-3.17.3-osx-x86_64.zip -d /usr/local bin/protoc \
	&& unzip -o protoc-3.17.3-osx-x86_64.zip -d /usr/local 'include/*' \
	&& rm -f protoc-3.17.3-osx-x86_64.zip
```

### 3. Protobuf/protoc Runtime/Compiler for go

> Protobuf support go programming language https://github.com/protocolbuffers/protobuf-go in package google.golang.org/protobuf

ProtoBuf/protoc compiler plugins for code generator

> Protocol buffer compiler requires a plugin to generate code
 
https://grpc.io/docs/languages/go/quickstart/

```
# The protocol buffer compiler requires a plugin to generate Go code
go get google.golang.org/protobuf/cmd/protoc-gen-go@v1.27

# The protocol buffer compiler requires a plugin to generate grpc Go code
go get google.golang.org/grpc/cmd/protoc-gen-go-grpc@v1.1
```


## Example

```
cd helloword

# after changes in helloworld.proto
protoc --go_out=. --go_opt=paths=source_relative \
    --go-grpc_out=. --go-grpc_opt=paths=source_relative \
    helloworld/helloworld.proto


go run greeter_server/main.go

go run greeter_client/main.go
```