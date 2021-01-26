---
title: Structures
parent: Data Types
grand_parent: C
has_children: false
nav_order: 3
---

# The `struct` type

Can be seen as a combination of other data types (including other `struct`)

Is similar to classes in OOP languages

## Initializing and accessing.

```c
int main(int argc, char const *argv[])
{
    struct example {
        int number;
        char name[32];
    };

    struct example example1;
    strcpy(example1.name,"Juan Pablo");
    example1.number = 7;

    struct example example2 = {
        8,
        "Pablo Juan"
    };

    printf("%s, number: %d\n", example1.name, example1.number);
    printf("%s, number: %d", example2.name, example2.number);
   
    return 0;
}

```

The code above prints
```
Juan Pablo, number: 7
Pablo Juan, number: 8
```
And shows both ways of initializing a `struct`

> Note that in C, the `=` operator doesn't assign value to strings, and `strcpy` should be used.

## In Functions

You can also return structures from functions by defining their return type as a structure type. For instance:

```c
struct example function();
```
