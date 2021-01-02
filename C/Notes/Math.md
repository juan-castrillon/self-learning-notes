---
title: Math
parent: C
has_children: false
nav_order: 5
---

# Math in C

## Operators
- `+`: Addition
- `-`: Subtraction
- `*`: Multiplication
- `/`: Division (Between `int` values, rounds down)
- `++`: Increment
- `--`: Decrement
- `%`: Mod
- **NO POWER OPERATOR**

## `math.h`

The `math.h` header file, includes functions to perform operations not possible with the built in operators

It uses `double` or `float` values.

Some notable are:
- `sqrt(float)`: Get the square root of a value
- `pow(base,exponent)`: Get base to the power of exponent

For a list [see here](http://www.cplusplus.com/reference/cmath/)

## Example

```c
#include<stdio.h>
#include<math.h>

int main(int argc, char const *argv[])
{
    float a;
    float b;
    printf("Input two numbers: ");
    scanf("%f",&a);
    scanf("%f",&b);
    printf("a+b = %.2f\n",a + b); //Limits to two numbers after the dot
    printf("a-b = %.2f\n",a - b);
    printf("a*b = %.2f\n",a * b);
    printf("a/b = %.2f\n",a / b);
    printf("a^b = %.2f\n",pow(a,b));
    printf("sqrt(a) = %.2f\n",sqrt(a)); 
    printf("sqrt(b) = %.2f\n",sqrt(b));   
    return 0;
}
```

------------------------------
## [Back to Index](../Aa_Index.md)
