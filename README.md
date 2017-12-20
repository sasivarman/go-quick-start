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

* **`GOPATH`** environment variable specifies the workspace path
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

The encouraged path convention in Go is to mimic source repository URL:

```bash
# Package from github.com/username/hello
$GOPATH/src/
    github.com/             # source repository hostname
        username/           # nested in directories as per repository path
            hello/          # last directory name is the package name
                world.go
```

It is encouraged to follow source repository based convention for Go packages even if the package is not version controlled.

There are 2 types of Go package:

1. **Library** - Go library that can be imported in to program or another library
2. **Program** - Go program that can be executed

## Library

A library is a package that cannot be executed, but can be included in to another program or library.

```go
package world

var Message string = "Hello World!"
```

This package provides a string property called `Message`.

