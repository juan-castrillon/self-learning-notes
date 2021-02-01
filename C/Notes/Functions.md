---
title: Functions
parent: C
has_children: true
nav_order: 6
---

# Functions

A function is a block of code that performs a specific task. 

In C There are two types:

- Standard library functions
- User-defined functions

## Standard Library Functions

These come included with libraries and have functions available to use given that the `#include` preprocessor directive is used to use the header file (`.h`).

The main example is the `<stdio.h>` library that includes all methods to interact with I/O like `printf` or `getchar`. In order to use it:

```c
#include <stdio.h>

int main()
{
    //something
}
```

Many other standard libraries exist, for example

Header File | Functionality
---|---
`<assert.h>`  |  Program assertion functions
`<ctype.h>`	|  Character type functions
`<locale.h>`	|  Localization functions
`<math.h>`	|  Mathematics functions
`<setjmp.h>`	|  Jump functions
`<signal.h>`	|  Signal handling functions
`<stdarg.h>`	|  Variable arguments handling functions
`<stdio.h>`	|  Standard Input/Output functions
`<stdlib.h>`	|  Standard Utility functions
`<string.h>`	|  String handling functions
`<time.h>`	|  Date time functions


## User defined functions

> In C, arguments are copied by value to functions, which means that we cannot change the arguments to affect their value outside of the function. To do that, we must use pointers

In order to define a function, two things are necessary: 

1.** Valid declaration**: A function can return only one parameter, and it should specify its type, and its arguments
```c
void function1(void)
{
    //something
}

void function2()//Empty parenthesis mean void arguments
{
    //something
}

int function3(int a, char b) //With type and arguments
{
    //something
}
```

2. The function must be  be **introduced to the compiler**: This is done in two ways. First it can be prototyped before using it and then declared (this is normally what header files are for):

```c
void function(void);

int main()
{
    function();
    return 0;
}

void function(void)
{
    //something
}
```

This is not required if the declaration appears before is used e.g before the main.

```c
void function(void)
{
    //something
}

int main()
{
    function();
    return 0;
}
```

### Static functions

By default, functions are global in C. If we declare a function with `static`, the scope of that function is reduced to the file containing it.

The syntax looks like this:

```c
static void fun(void) {
   printf("I am a static function.");
}
```





