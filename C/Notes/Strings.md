---
title: Strings
parent: Data Types
grand_parent: C
has_children: false
nav_order: 1
---

# Strings

- Strings are not a type in C, instead are represented by a `char[]`
- The final character is always the null character `'\0'`. This has to be accounted for in the size
- Use double quotes `"` (instead of single like `char`)


## Declaration

As with any array, the size can be left empty if assigned immediately: 
```c
char buffer[] = "something";
```
Or it need to be declared:
```c
char buffer[15]; //Here it has space for 14 characters (+ null)
//do something
```

Also valid is to use [pointers]() in the following way:

```c
char * name = "John Smith";
```

This method creates a string which we can only use for reading. 

## Manipulating Strings

Using the `string.h` library, many manipulation functions can be used. The complete list of methods is [here](https://fresh2refresh.com/c-programming/c-function/string-h-library-functions/) and the most important are:
- `strlen(s)`: Display the number of characters in a string (Not including the null character at the end!)
- `strcpy(buffer,s)`: Copies one string into a buffer (another)
- `strcat(buffer,s)`: Appends a string to a buffer (Has to have enough space)
- `strtok(s,del)` and `strtok_r(s,del,*s)`: Separates the string into tokens by the characters in the delimiter. [How to use](https://www.geeksforgeeks.org/strtok-strtok_r-functions-c-examples/)
- `char *strchr(const char *str, int c)` searches for the first occurrence of the character `c` in the string and returns a pointer to it

> To concatenate strings in C, the `+` operator **does not** work. The process is:
>   1. Create a new buffer string with enough size for both strings
>   2. Copy the first string into the buffer
>   3. Append the second string
>   ``` c
> #include <stdio.h>
>#include <string.h>
>
>int main(int argc, char const *argv[])
>{
>    char name[64];
>    char lastName[64];
>    puts("Enter the name: ");
>    fgets(name,64,stdin);
>    puts("Last Name: ");
>    fgets(lastName,64,stdin);
>    
>    char buffer[128];
>    strcpy(buffer,name);
>    strcat(buffer,lastName);
>
>    printf("Your name is: %s", buffer);
>
>    return 0;
>}
>```