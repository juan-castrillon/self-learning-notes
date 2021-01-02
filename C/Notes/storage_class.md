---
title: Scope
parent: Functions
grand_parent: C
nav_order: 1
---

# Variable storage class

Every variable in C programming has two properties: type and storage class.

Type refers to the data type of a variable. And, storage class determines the scope, visibility and lifetime of a variable.

There are 4 types of storage class:

- automatic (local)
- external (global)
- static
- register


## Local Variable

The variables declared inside a block are **automatic** or **local** variables. The local variables exist only inside the block in which it is declared. Is normally the case for variables inside functions


```c
#include <stdio.h>

int main(void) {
  
  for (int i = 0; i < 5; ++i) {
     printf("C programming");
  }
  
 // Error: i is not declared at this point
  printf("%d", i);  
  return 0;
}
```
Other example: 

```c
int main() {
    int n1; // n1 is a local variable to main()
}

void func() {
   int n2;  // n2 is a local variable to func()
}
```

This means you cannot access the n1 variable inside `func()` as it only exists inside `main()`. Similarly, you cannot access the n2 variable inside `main()` as it only exists inside `func()`.

## Global Variable

Variables that are declared outside of all functions are known as **external** or **global** variables. They are accessible from any function inside the program.

```c
#include <stdio.h>
void display();

int n = 5;  // global variable

int main()
{
    ++n;     
    display(); //Outputs n = 7
    return 0;
}

void display()
{
    ++n;   
    printf("n = %d", n);
}
```

> If a global variable is declared in `file1`, to use it in another file `file2`, the keyword `extern` is used in `file2` to indicate that the external variable is declared in another file. 
> On file1:
>```c
>int number = 10;
>int main(int argc, char *argv[]) 
>{
>    return 1;
>}
>```
> On file2:
>```c
>extern int number;
>int function() 
>{
>    number++;
>    return number;
>}
>```

## Register Variable

The `register` keyword is used to declare register variables. Register variables were supposed to be faster than local variables.

However, modern compilers are very good at code optimization, and there is a rare chance that using register variables will make your program faster.

## Static Variable

A static variable is declared by using the `static` keyword.

- They cannot be accessed from any other file. Thus, prefixes `extern` and `static` cannot be used in the same declaration.
- They maintain their value throughout the execution of the program independently of the scope in which they are defined.

As a consequence of these two properties, the following two cases are derived:

- If a `static` variable is defined outside of the functions it will be accessible only by the code that follows in the file it is declared.
- If the `static` variable is declared in a function, it will only be accessible from the function, and it will keep its value between function executions.


```c
#include <stdio.h>
void display();

int main()
{
    display(); //6
    display(); //11
}
void display()
{
    static int c = 1;
    c += 5;
    printf("%d  ",c);
}
```
------------------------------
## [Back to Index](../Aa_Index.md)