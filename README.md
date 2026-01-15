# json5 by golang

[![Go Reference](https://pkg.go.dev/badge/github.com/928799934/json5-go.svg)](https://pkg.go.dev/github.com/928799934/json5-go)
[![GitHub tag (latest SemVer pre-release)](https://img.shields.io/github/v/tag/928799934/json5-go?include_prereleases&label=release-tag)](https://github.com/928799934/json5-go/releases)
[![Go Report Card](https://goreportcard.com/badge/github.com/928799934/json5-go)](https://goreportcard.com/report/github.com/928799934/json5-go)
[![Open Source Helpers](https://www.codetriage.com/928799934/json5-go/badges/users.svg)](https://www.codetriage.com/928799934/json5-go)
[![License](https://img.shields.io/badge/license-BSD-blue.svg)](https://github.com/928799934/json5-go/blob/master/LICENSE.md)

[![Build Status](https://travis-ci.org/928799934/json5-go.svg?branch=master)](https://travis-ci.org/928799934/json5-go)

The code is heavily modified from https://travis-ci.org/yosuke-furukawa/json5.

[JSON5](https://github.com/aseemk/json5) is Yet another JSON.
---

# go get
```
$ go get github.com/928799934/json5-go
```

# example

```go
package main

import (
	"encoding/json"
	"fmt"
	"github.com/928799934/json5-go"
	"os"
)

func main() {
	var data interface{}
	dec := json5.NewDecoder(os.Stdin)
	err := dec.Decode(&data)
	if err != nil {
		fmt.Println(err)
	}
	b, err := json.MarshalIndent(data, "", "    ")
	if err != nil {
		fmt.Println(err)
	}
	fmt.Println(string(b))
}
```

```js
// This is json5 demo
// json5 can write comment in your json
{
  key : "Key does not need double quote",
  // json specific
  "of" : "course we can use json as json5",
  trailing : "trailing comma is ok",
}
```

```
$ json5 -c example.json5
# output
#{
#    "key": "Key does not need double quote",
#    "of": "course we can use json as json5",
#    "trailing": "trailing comma is ok"
#}
```
