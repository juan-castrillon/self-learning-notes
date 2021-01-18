---
title: Data Types
parent: C
has_children: false
nav_order: 3
---

# Data Types

## Primary Data Types

In C, there are 5 primary data types:
- `int`
- `float`
- `double`
- `char`
- `void`: if a function is not returning anything, its return type should be void. Note that, you cannot create variables of void type.

Other types are derived from these ones (array,structure,etc.)

## Size and modifiers

- Bytes reserved in the memory can change according to the computer, but the `sizeof()` operator can be used to check
- Normally:
    - int : 4
    - char: 1
    - float: 4
    - double: 8
- `short` and `long` modifiers can be used before the type to limit (or expand the size) (Even `long long` is valid)
- `signed` and `unsigned` can be used to change the range. 

For example:
```c
#include<stdio.h>
int main(int argc, char const *argv[])
{
    printf("int:%d\n",sizeof(int));
    printf("short int:%d\n",sizeof(short));
    printf("long int:%d\n",sizeof(long));
    printf("char:%d\n",sizeof(char));
    printf("float:%d\n",sizeof(float));
    printf("double:%d\n",sizeof(double));
    return 0;
}
```
Outputs:
```
int:4
short int:2
long int:4
char:1
float:4
double:8
```

## Boolean Values

C has no boolean primitive types, however it uses the convention that `0` means “false” and any non-zero value means “true.” 
Boolean variables and functions that return Boolean values are traditionally declared `int`.
The `stdbool.h` library provides support for more explicit booleans in modern C compilers.
For example:

```c
#include <stdio.h>
#include <stdbool.h>

int main(void) {
    bool x = true;  /* equivalent to bool x = 1; */
    bool y = false; /* equivalent to bool y = 0; */
    if (x)  /* Functionally equivalent to if (x != 0) or if (x != false) */
    {
        puts("This will print!");
    }
    if (!y) /* Functionally equivalent to if (y == 0) or if (y == false) */
    {
        puts("This will also print!");
    }
}
```

------------------------------
## [Back to Index](../Aa_Index.md)