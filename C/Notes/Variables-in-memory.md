---
title: Variables in memory
parent: Data Types
grand_parent: C
has_children: false
nav_order: 4
---

# Variables in memory

A variable of any type, can be seen as a data container. Being so, it occupies a certain space in the memory

## Sizeof

Using the `sizeof()` operator, allows to know how much bytes the variable occupies. This, although standard in many computers for the primitive types, **should not be assumed**.

For example
```c
#include<stdio.h>
int main(int argc, char const *argv[])
{
    int a;
    printf("int:%lu\n",sizeof(a));
}
```
Outputs:
```
int:4
```

## Address operator

To know the memory address where the variable is store, the address operator `&` is used

For example
```c
int a;
float b;
char c;

printf("a is located at %p\n",&a);
printf("b is located at %p\n",&b);
printf("c is located at %p.",&c);
```

prints
```
a is located at 000000000061FE1C
b is located at 000000000061FE18
c is located at 000000000061FE17.
```