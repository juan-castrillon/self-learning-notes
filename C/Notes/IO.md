# Output

In `<stdio.h>` there are several functions to print strings or characters to the STDOUT of the system

To see all the functions see [here](https://en.cppreference.com/w/c/io)

> In strings, escape characters can be used to print certain characters:
    - \n -> New Line
    - \t -> Tab
    - \' -> Single quote
    - \" -> Double quote
    - \\ -> Backlash 

## `puts`

Prints a string into the STDOUT and **adds a \n character**

```c
puts("Hello");
```

## `printf`

- More powerful than `puts`. Allows to print a formatted string (optional)
- Apart from the escape sequences, it also uses placeholders to format the string

```c
printf("Hello"); // No formatting (but no \n at the end)
```

### Placeholders

They are replaced in the strings with the parameters passed

Placeholder | Type
--- | ---
`%d` `%i` | Decimal Based Integer
`%s` | String
`%c` | Character
`%f` | Floating point value
`%e` | Scientific notation (with "e")
`%g` | Shorter between `%f` and `%e`

Width and precision can also be modified with numbers and "." among other things.

```c
#include <stdio.h>
// Testing placeholders
int main(int argc, char const *argv[])
{
    int a = 2;
    float b = 3.85447995945454565; //large float
    printf("Printing integer %d, %i\n",a,a); //Printing integer 2, 2
    printf("Now printing a %s", "string\n"); //Now printing a string
    printf("Characters like %c as well\n", 'w'); //Characters like w as well
    printf("Whole float: %f, shortening %.2f, with width %5.2f\n",b,b,b); // Whole float: 3.854480, shortening 3.85, with width  3.85
    printf("Now scientific %e and the one that works both ways %.3g" ,b,b); //Here %.3g prints 3.85, with 2-> 3.9
    return 0;
}
```

[For more information](https://www.tutorialspoint.com/c_standard_library/c_function_printf.htm)

## `putchar(int character)`

- Method for outputting characters
- Works with `int` values for the characters (Unicode)
- **Stream Oriented** : Like `getchar()` is a buffered method, and only executes when the buffer is flushed or full

```c
#include<stdio.h>
int main(int argc, char const *argv[])
{
    printf("Enter a character: ");
    int c = getchar();
    printf("Entered: ");
    putchar(c); //At the end flushes, and executes
    return 0;
}
```

# Input

## `getchar()`

- Reads a character from standard input
- Returns an `int` value for the character (Unicode)
- **Stream Oriented**

## `scanf()`

- Uses placeholders (Like `printf`) to read values into declared variables
- Is used like `scanf("format",&variable)` using a pointer to the variable (address of operator)
- Not recommended for strings
- Stops reading in the first whitespace character

```c
#include<stdio.h>
int main(int argc, char const *argv[])
{
    int a;
    float b;
    printf("Integer: ");
    scanf("%d",&a);
    printf("Decimal: ");
    scanf("%f",&b);
    printf("Entered int %d and float %.2f",a,b); //Can cut the float
    return 0;
}
```

## `fgets()`

- Method normally used to read from streams (files for example)
- `stdin` is considered a stream in C, so is used to read strings
- Receives an input buffer, the max amount of bytes to read into the buffer and the stream

```c
#include<stdio.h>
int main(int argc, char const *argv[])
{
    char string[64]; //Size for 63 char
    puts("Enter a string: ");
    fgets(string,64,stdin);
    printf("You entered %s",string);
    return 0;
}


```

------------------------------
## [Back to Index](../Aa_Index.md)