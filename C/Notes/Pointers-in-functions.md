---
title: Pointers in Functions
parent: Pointers
grand_parent: C
has_children: false
nav_order: 2
---
# Pointers in functions

Pointers can be used as arguments or as return values of functions.

## As arguments

When passing pointers as arguments, the memory address is passed, this allows to escape the scope of the function to modify variables (because the value stored in the memory address is modified). For example, this program:
```c
#include <stdio.h>

void modify(int i);

int main(int argc, char const *argv[])
{
    int a = 30;
    printf("Before %d\n", a);
    modify(a);
    printf("After %d", a);
    return 0;
}

void modify(int i)
{
    i = i + 20;
}
```
will print 
```
Before 30
After 30
```
By passing a pointer as argument instead:
```c
#include <stdio.h>

void modifyWithRef(int *pointer);

int main(int argc, char const *argv[])
{
    int a = 30;
    printf("Before %d\n", a);
    modifyWithRef(&a);
    printf("After %d", a);
    return 0;
}

void modifyWithRef(int *pointer)
{
    *pointer += 20;
}
```
The result is:
```
Before 30
After 50
```

> This can also be used to pass strings as arguments in functions. In this case, the construction
> ```c
> while( *pointer )
> ```
> Is useful for going through the whole string, is equivalent to `while(*pointer != '\0')`

## As return values

When a function returns a pointer, is returning a memory address. This is useful when returning for example a pointer passed as an argument
```c
char *longer(char *string1, char *string2)
{
    if (strlen(string1) > strlen(string2)) return string1;
    else return string2;
}
```
However, when dealing with arrays or returning new values, the scope of the function has to be taken into account. The memory address can be returned but when exiting the function, the value that was inside is deleted. To avoid that, the keyword `static` is used, which makes the array persistent in memory between function calls. See [here](storage_class.md).