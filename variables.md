# Variables

Variables are statically typed, thus the _type_ must be explicitly provided or a non _nil_ value must be assigned on declaration. Unassigned but typed variables are defaulted to _zero_ value of it's _type:_

```go
var a int     // = 0
var b int = 1
var c = 2     // int

var z = nil     // this is an error, as nil is untyped
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



