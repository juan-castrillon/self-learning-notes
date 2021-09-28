---
title:  Language Basics
parent: Go
nav_order: 1
---

# Syntax

- Go programs don't use semicolons to end statements. Instead the compiler detects new lines.
- Case sensitive (Capital first letter means a field/method is exported or `public`)

## `builtin` Package

- Is included by default
- Among others has:
  - `panic()`: To display and error and exit the program
  - `len()`: To determine length of things (arrays, strings, maps, etc)

- It also includes the basic types
- More info in [the docs](https://pkg.go.dev/builtin)

## Types

Basic types include:
```go
bool
string
uint, uint8, uint16, uint32, uint64 //Unsigned integer
int, int8, int16, int32, int64 // Integer, int can vary on the machine architecture (32 or 64 bits)
byte //Alias for int8
rune //Alias for int32, represents an unicode code point
float32, float64
complex64, complex128 //Complex numbers (0 + 2i)
```

More complex types include:
- Arrays
- Slices (Similar to `List` in Java, variable size array)
- Maps
- Struct
- Function (Go allows for functional programming)
- Interface
- Channel
- Pointer (Similar to C, a reference to memory)
- Custom Types

## Declarations

Variables can be declared in different ways:
```go
var x int //Initializes the variable in the zero value
var x int = 2 // Explicit declaration and assignment
var x = 2 //Type is inferred 
x := 2 //Shorthand for type inference - ONLY USABLE INSIDE FUNCTIONS SCOPE
```

At the same time constants, can be used (outside functions)
```go
const Pi = 3.14
const (
    Pi = 3.14
    Wa = 3.68
    We = "AEIOU"
)
```