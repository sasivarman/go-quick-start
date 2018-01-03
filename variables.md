# Variables

Variables are statically typed, thus the _type_ must be explicitly provided or typed value must be assigned on declaration. Unassigned but typed variables are defaulted to _zero_ value of it's _type:_

```go
var a int     // = 0
var b int = 1
var c = 2     // int

var y = nil   // this is an error, as nil is untyped
var z         // this is an error, as type cannot be inferred
```

Multiple variables can be declared in a single `var` call:

```go
var d, e, f int               // = 0, 0, 0
var g, h, i int = 6, 7, 8
var j, k, l = 9, 10, "eleven" // = int, int, string
```

Variable declarations can be factored:

```go
var (
    a       int
    b       int = 1
    c           = 2
    d, e, f int
    g, h, i int = 6, 7, 8
    j, k, l     = 9, 10, "eleven"
)
```

The following single line factored declarations works but discouraged:

```go
var (a int; b int = 1; c = 2; d, e, f int; g, h, i int = 6, 7, 8; j, k, l = 9, 10, "eleven")
```

## Zero Value

Every type have a defined zero value:

```go
var a int    // = 0
var b string // = ""
var c bool   // = false
```

`nil` is the _zero value_ for _pointers_, _interfaces_, _maps_, _slices_, _channels_, and _function types_. When these declarations are unassigned, the `nil` value is assigned. Only the above mentioned types can be assigned to a `nil` value.

## Blank Identifier

`_` is an identifier that discards it's value safely:

```go
var _, needed int = 10, 20         // the first value is discarded
var _, second int = someFunction() // the first return from function is discarded
```

Used in functions that return multiple values to safely discard unused returns:

```go
var _, second int = someFunction() // the first return from function is discarded
```

As unused variables or imports raise compilation error in Go, blank identifiers can be used to safely silent them in development:

```go
package main

import (
    "fmt"
    "io"
)

var _ = fmt.Printf // safely silents unused imports for debugging; delete when done
var _ io.Reader    // silents via type declaration; delete when done

func main() {
    var a = 5
    _ = a // safely silents unused variables for debugging; delete when done
}
```

## Short Variable Declarations

A shorthand for variable declaration can be used in a _function_ only:

```go
func main() {
    a := 0
    b := "one"
    c, d := 2, "three"
    _, e := 4, 5       // first assignment is ignored
}
```

A variable can be redeclared with a short hand, only when redeclared together with a new non _blank_ variable in a multi variable declaration. The redeclaration has to obey the first declaration _type_.

```go
func ok() {
    a := 1
    a, b := 2, 3 // this is valid as b is a new variable   
}

func error() {
    a := 1
    a := 2           // this is an error because it is not multi variable declaration
    
    b := 3
    a, b := 4, 5     // this is an error because there is no new variable declared
    
    a, c := "six", 7 // this is an error before a is a int and cannot be assigned with string
    
    _, a := 8, 9     // this is an error because the other variable is blank
}
```



