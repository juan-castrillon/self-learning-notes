---
title: Pointer Arithmetic
parent: Pointers
grand_parent: C
has_children: false
nav_order: 1
---
# Pointer Arithmetic

A pointer, as discussed before, is a reference to a memory address. This can be exploited to perform arithmetic operations with them, to access values

## Accessing arrays

Arrays are in reality similar to pointers. Although they are not the same:Array variables are a reference to the memory position of the first element of the array in the memory, while pointers are variables that hold a value (that is a memory address). [More info](https://www.programiz.com/c-programming/c-pointers-arrays)

This similarity translates into pointer arithmetic and array indexing being equivalent:
```c
int array[] = {1, 2, 3, 4, 5};
int *pointer;

pointer = array; //Because array is already a memory reference
for (int i = 0; i < 5; i++)
{
    printf("Element %d is %d\n", i, *(pointer + i));
}
```
prints
```
Element 0 is 1
Element 1 is 2
Element 2 is 3
Element 3 is 4
Element 4 is 5
```
As well as modifying the for loop like:
```c
for (int i = 0; i < 5; i++)
{
    printf("Element %d is %d\n", i, *pointer);
    pointer++;
}
```

> Note that an array of pointers, is also possible
> ```c
> char *a[3] = {"One", "Two", "Three"};
> ```