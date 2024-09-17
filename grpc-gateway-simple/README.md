# Create Simple gRPC-Gateway in Go
* https://tuts.heomi.net/create-simple-grpc-gateway-in-go/

# Overview

The gRPC-Gateway is a plugin of the Google protocol buffers compiler [protoc](https://github.com/protocolbuffers/protobuf). It reads protobuf service definitions and generates a reverse-proxy server which translates a RESTful HTTP API into gRPC.

# Prerequisites

* [golang](https://go.dev/doc/install) (1.18+)

We are using goenv to manage the go version
```bash
$ goenv versions
  system
  1.17.13
  1.18.10
  1.18.3
  1.19.13
  1.20.14
  1.21.11
* 1.22.4 (set by /home/tvt/.goenv/version)
```

* Install the [protocol buffer compiler](https://grpc.io/docs/protoc-installation/) [protoc]:

On Linux
```bash
$ apt install -y protobuf-compiler
$ protoc --version  # Ensure compiler version is 3+

libprotoc 3.12.4
```

On MacOS
```bash
$ brew install protobuf
$ protoc --version  # Ensure compiler version is 3+
```

* Install gRPC `protoc` tools for generating Go

```bash
$ go install google.golang.org/protobuf/cmd/protoc-gen-go@latest
$ go install google.golang.org/grpc/cmd/protoc-gen-go-grpc@latest
$ go install github.com/grpc-ecosystem/grpc-gateway/v2/protoc-gen-grpc-gateway@latest
```

Need to ensure update your PATH so that the protoc compiler can find the plugins
```bash
export GOPATH=$HOME/go
export PATH=$PATH:$GOPATH/bin
```

You can check the version
```bash
$ protoc-gen-go --version
protoc-gen-go v1.34.2
$ protoc-gen-go-grpc --version
protoc-gen-go-grpc 1.5.1
$ protoc-gen-grpc-gateway --version
Version v2.22.0, commit unknown, built at unknown
```

# Project Struture

Create the project folder
```bash
$ mkdir grpc-gateway
$ cd grpc-gateway
```

Create the go.mod file
```bash
$ go mod init github.com/favtuts/grpc-gateway
```

# Create the main.go

The `main.go` file is to  create the gateway entry point. For this, run the commands below.
```bash
$ mkdir cmd
$ touch cmd/main.go
```

Place the hello world code 
```go
package main

import "fmt"

func main() {
	fmt.Println("Hello gRPC-Gateway demostration")
}
```

Run the code:
```bash
$ go run cmd/main.go

Hello gRPC-Gateway demostration
```