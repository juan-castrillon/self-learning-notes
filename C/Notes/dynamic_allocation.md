---
title: Dynamic Memory Allocation
parent: C
has_children: false
nav_order: 8
---
# Dynamic Memory Allocation

When a C program runs, the OS assigns a certain amount of memory for the program. This memory, is used when declaring variables or buffers. In order to dynamically ask for memory (when for example buffer sizes are unknown), the `<stdlib.h>` header file provides functions for dynamic memory allocation.

## `malloc`

The function ``malloc`` is used to initialize pointers with memory from free store (a section of memory available to all programs).

The argument to `malloc` is the amount of memory requested (in bytes), and `malloc` gets a block of memory of that size and then returns a pointer to the block of memory allocated (or `NULL` if the memory could not be assigned).

The amount of bytes to ask for normally depends on the type of the data to be stored, so the `sizeof` operator is commonly used:

```c
int *p;
p = malloc(10 * sizeof(int)); //This asks for space for 10 integer numbers
```

The pointer (after being checked for `NULL`) can then be used to store and retrieve values. For example, the code belows, allows to allocate dynamically for user input and then store the values:
```c
#include <stdlib.h>
#include <stdio.h>

int main(int argc, char const *argv[])
{
    int size, *p;
    printf("Number of elements: ");
    scanf("%d", &size);
    p = malloc(size * sizeof(int));
    if (p == NULL) return -1;
    printf("Start entering\n");
    for (int i = 0; i < size; i++)
    {
        scanf("%d", (p + i));
    }
    printf("All numbers read\n");
    for (int i = 0; i < size; i++)
    {
        printf("%d ", *(p + i));
    }
    return 0;
}
```

> Contrary to just declaring an array based on the read size, using malloc, the values have "allocated" duration. That means the lifetime lasts until the values are freed by a call to `free()`. An array would create values with automatic storage duration. This means that the array's lifetime lasts until its identifier goes out of scope.

## `free()`

The free function returns memory to the operating system. Because memory allocated using `malloc` doesn't get freed on their own, one must explicitly use `free()` to release the space.

```c
int *p;
p = malloc(10 * sizeof(int));
//...some code
free(p);
```

## `calloc()`
The name "calloc" stands for contiguous allocation.

The `malloc()` function allocates memory and leaves the memory uninitialized. Whereas, the `calloc()` function allocates memory and initializes all bits to zero.

It uses as parameters, the number of elements and the size of one element:
```c
float *ptr = calloc(25, sizeof(float)); //Space for 25 float elements.
```

## `realloc()`
If the dynamically allocated memory is insufficient or more than required, you can change the size of previously allocated memory using the `realloc()` function.

Its syntax is the following:
```c
ptr = realloc(ptr, x);
```
Here, `ptr` is reallocated with a new size `x`.

For example:
```c
#include <stdio.h>
#include <stdlib.h>

int main () {
   char *str;

   /* Initial memory allocation */
   str = (char *) malloc(15);
   strcpy(str, "tutorialspoint");
   printf("String = %s,  Address = %u\n", str, str);

   /* Reallocating memory */
   str = (char *) realloc(str, 25);
   strcat(str, ".com");
   printf("String = %s,  Address = %u\n", str, str);

   free(str);
   
   return(0);
}
```