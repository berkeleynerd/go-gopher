# Gopher protocol library for Golang

[![Build Status](https://cloud.drone.io/api/badges/prologic/go-gopher/status.svg)](https://cloud.drone.io/prologic/go-gopher)
[![CodeCov](https://codecov.io/gh/prologic/go-gopher/branch/master/graph/badge.svg)](https://codecov.io/gh/prologic/go-gopher)
[![Go Report Card](https://goreportcard.com/badge/prologic/go-gopher)](https://goreportcard.com/report/prologic/go-gopher)
[![GoDoc](https://godoc.org/git.mills.io/prologic/go-gopher?status.svg)](https://godoc.org/git.mills.io/prologic/go-gopher) 
[![Sourcegraph](https://sourcegraph.com/git.mills.io/prologic/go-gopher/-/badge.svg)](https://sourcegraph.com/git.mills.io/prologic/go-gopher?badge)

This is a standards compliant Gopher library for the Go programming language
implementing the RFC 1436 specification. The library includes both client and
server handling and examples of each.

## Installation

```#!bash
$ go get git.mills.io/prologic/go-gopher
```

## Usage

```#!go
import "git.mills.io/prologic/go-gopher"
```

## Example

### Client

```#!go
package main

import (
	"fmt"

	"git.mills.io/prologic/go-gopher"
)

func main() {
	res, _ := gopher.Get("gopher://gopher.floodgap.com/")
	bytes, _ := res.Dir.ToText()
	fmt.Println(string(bytes))
}
```

### Server

```#!go
package main

import (
	"log"

	"git.mills.io/prologic/go-gopher"
)

func hello(w gopher.ResponseWriter, r *gopher.Request) {
	w.WriteInfo("Hello World!")
}

func main() {
	gopher.HandleFunc("/hello", hello)
	log.Fatal(gopher.ListenAndServe("localhost:70", nil))
}
```

## Related

Related projects:

- [gopherproxy](https://git.mills.io/prologic/gopherproxy)
  gopherproxy is Gopher to HTTP proxy that uses go-gopher
  for all of its core functionality.

- [gopherclient](https://git.mills.io/prologic/gopherclient)
  gopherclient is a cross-platform QT/QML GUI Gopher Client
  using the gopherproxy library as its backend.

## License

MIT
