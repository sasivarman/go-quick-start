# Constants

Constants are statically typed and must be assigned with a constant value or expression_:_

```go
const a int = 1
const b = 2     // int
const c = 3.0   // float

const x int     // this is an error, as value is not assigned
const y = nil   // this is an error, as nil is untyped
const z         // this is an error, as type cannot be inferred
```

Multiple constant can be declared in a single `const` call:

```go
const g, h, i int = 6, 7.0, 8
const j, k, l = 9, 10.0, "eleven" // = int, float, string
```



