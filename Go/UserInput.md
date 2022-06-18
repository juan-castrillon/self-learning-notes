---
title:  User Input
parent: Go
nav_order: 2
---

# Reading from STDIN

The `fmt` package offers methods to scan input from the terminal line: 

```go
fmt.Printf("Please give me your name: ")
var name string
fmt.Scanln(&name)
fmt.Println("Your name is", name)
```

# Command Line Arguments

## `os.Args`

By default, go allows to read arguments passed to the binary, in the form of the `os.Args` string slice

![1](../img/osargs.png)

