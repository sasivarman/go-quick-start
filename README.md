# Go Quick Start

A quick start guide for Go programming language aimed at experienced programmers:

* Concise explanations
* More executable code snippets
* Complete language features coverage 
* As vanilla as possible

## Requirements

1. [Go Installation](https://golang.org/doc/install)
2. [Source Code Editor or IDE](https://golang.org/doc/editors.html)

## Workspace

Go requires all Go files to be stored under a single directory called **workspace**.

* `GOPATH` environment variable specifies the workspace path
* `$ go env GOPATH` outputs the active workspace path
* [Workspace path can be changed](https://golang.org/wiki/SettingGOPATH); thus its possible to switch workspaces but highly discourage
* Workspace path must not be the same as Go installation

The workspace directory consists of the 3 sub directories:

1. `src/` contains all source codes organized in to **packages**
2. `pkg/` stores all importable libraries upon package installation
3. `bin/` stores all executable binaries upon package installation

## Package

Go modularizes application in to packages which are just directories with `.go` files:

```bash
# Package hello
$GOPATH/src/                # all source belong in workspace src directory
    hello/                  # package hello
        world.go            # at least one .go source file
```

The encouraged path convention in Go is to mimic source repository URL even if source is not version controlled:

```bash
# Package from github.com/username/hello
$GOPATH/src/
    github.com/             # source repository hostname
        username/           # nested in directories as per repository path
            hello/          # last directory name is the package name
                world.go
```

Nested directories are considered separate packages:

```bash
$GOPATH/src/github.com/username/
    hello/                        # package hello -> github.com/username/hello
        world.go
        moon.go
        hi/                       # package hi -> github.com/username/hello/hi
            hey.go
```

There are 2 types of Go package:

1. **Library** - Go library that can be imported in to program or another library
2. **Program** - Go program that can be executed

## Library

A Go library is a package that cannot be executed, but can be included in to another program or library.

```go
// $GOPATH/src/github.com/username/hello/world.go

package hello

var message string = "Hello World!"

// public scoped variables or functions names must start with uppercase
func GetMessage() string {
    return message
}
```

This `hello` package provides a function called `GetMessage()`.

* It is encouraged that the `package` name is in lowecase alpha numeric only with no symbols
* It is encouraged to name the`package` the same as the last directory name of the package path

A package can be split in to multiple `.go` files, but they all must remain in the same directory and must use the same `package` name. During compilation, all the package's `.go` files will be build as one.

## Program

A Go program can be executed. Both programs and libraries can import other libraries:

```go
// $GOPATH/src/github.com/username/say/something.go

package main

import (
    "fmt"                       // standard library can be imported without a path
    "github.com/username/hello" // custom library must be imported relative to GOPATH
    "../hello/hi"               // relative path works but discouraged
    mathematics "math"          // import can have alias name
    _ "net/http/pprof"          // alias to blank identifier - imported but unused
)

func main() {
    fmt.Println(hello.GetMessage())
    fmt.Println(hi.GetMessage())
    fmt.Println(mathematics.PI)
}
```

* `package` name of a program must be `main`
* Function `main()` must be the entry point of a program

The following `import` statement works but discouraged

```go
// multiple import statements
import "fmt"
import mathematics "math"

// single line factored import
import ("github.com/username/hello"; hey "../hello/hi")
```

## Build Tools

[`go` command line tool](https://golang.org/cmd/go/) is for managing Go source code:

```
$ go [command] [arguments]
```

The following are the commonly used commands:

* `go build [files]`

  * compiles the specified `.go` files \(multiple files possible\)
  * when no files are specified, compiles `.go` files in the current directory
  * outputs a executable binary in the current directory when a program \(package `main`\) is build successfully
  * outputs nothing if a library is build successfully
  * outputs error if build fails

* `go run [files]`

  * run `build` as above and runs resulting executable binary
  * only works on a program \(package `main`\)

* `go install [files]`

  * run `build` as above and copies the resulting executable binary to workspace
  * library objects are copied to `$GOPATH/pkg/`
  * program \(package `main`\) executable are copied to `$GOPATH/bin/`
  * if `$GOPATH/bin/` is added to system `PATH`, the installed executable can be run from any directory

Variables

Constant

Types

Scope

Pointers

Interfaces

Structs

Functions

Methods

