---
title: Data Types
parent: C
has_children: true
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

In the case of integers, the `stdint.h` header file defines types and constant to work with precisely specifed types (Like `uint64_t` which represents an unsigned integer which is always 64 bits). More information [here](https://pubs.opengroup.org/onlinepubs/009696799/basedefs/stdint.h.html).

## Constants

### Constant Data type

-Declared just like a normal variable, using the keyword `const`
- Value has to be assigned when created
- Has limited scope (to where is defined)

```c
int main()
{
    const int x = 5;
    //Scope valid in the main method
}
```

### Constant Expression

- Creates constants in the preprocessor (directive)
- Using the directive `#define` followed by an immediate value to assign
- Name in ALL CAPS
- No semicolon
- Scope throughout the whole file when defined

```c
#define ROWS 20
#define COLUMNS 60
#define GRID ROWS*COLUMNS //Scope in whole file

int main() {
    //something
}
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