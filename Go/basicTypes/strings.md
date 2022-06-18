---
title: String and Related
parent: Basic Types
grand_parent: Go
---

# Strings

- Collection of bytes (or `rune`)
- Out-of-the-box support for Unicode strings (Where multiple bytes are required to store on character -> `rune` is a `int32` value that represents one unicode code point)

- Strings can be thought of of both bytes and runes: 

```go
a := "Hello 榇"
for i := 0; i < len(a); i++ {
    fmt.Printf("Character %v, Type: %T\n", a[i], a[i])
}
```

Will print 

```
Character 72, Type: uint8
Character 101, Type: uint8
Character 108, Type: uint8
Character 108, Type: uint8
Character 111, Type: uint8
Character 32, Type: uint8
Character 230, Type: uint8
Character 166, Type: uint8
Character 135, Type: uint8
```

An each `a[i]` is treated as a `byte`. In the same way, 

```go
a := "Hello 榇"
for _, c := range a {
    fmt.Printf("Character %v, Type: %T\n", c, c)
}
```

will print

```
Character 72, Type: int32
Character 101, Type: int32
Character 108, Type: int32
Character 108, Type: int32
Character 111, Type: int32
Character 32, Type: int32
Character 27015, Type: int32
```

where every charaacter is a `rune`

## Conversion

The `strconv` package includes many functions to convert strings to other data types, and in reverse, other types to string.

To convert an integer for example, special attention must be given to the method: 
```go
n := 100
input := strconv.Itoa(n) //Will be 100
input = strconv.FormatInt(int64(n), 10) //will be 100
input = string(n) // will be "d"
```

## Processing

Packages like `unicode` and `strings` help with string processing. In particular, `strings` has some useful methods as:
- `EqualFold` to compare irrelevant of case
- `HasPrefix`, `HasSuffix`
- `Fields` to split into a slice based on whitespace
- `Split` to split into a slice based on a separator string
- `SplitAfter` to split into a slice based on a separator string, keeping it
- `Trim` to apply a `TrimFunc` fo the string