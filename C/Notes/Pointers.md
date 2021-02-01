---
title: Pointers
parent: C
has_children: false
nav_order: 7
---

# Pointers

A pointer is a variable that holds a memory location (an address)

## Declaration

As any variable, pointers also can be of any data type. The `*` operator is used before the name to indicate a pointer
```c
int variable;
int *pointer_variable;
```
Also as any variable, **it must be initialized before using it**. This is done assigning the address of another variable
```c
int variable = 5;
int *pointer_variable = &variable;
```

## Dual Nature

A pointer can represent two things according to how it is used:
1. If used **without** the `*`, it represents a memory location, an address
2. If used **with** the `*`, it represents the value at its location

```c
int a = 4;
    int *pointer;

    pointer = &a;

    printf("At address %p there is a value of %d", pointer, *pointer);
    // Prints At address 000000000061FE14 there is a value of 4
```