# Flow Control

## IF Statements
If statements are similar to other languages:
```c
if (condition)
{
    //do something
}
else if
{
    //another option
}
else 
{
    //else
}
```
However, in C if inside any condition there is just one line of code, the `{ }` are optional
```c
if (condition)
    //do something
else
    //else
```

### Logical Operators and Comparison
- `==` : used for equality check.
- `!=` : not equal
- `>`
- `<`
- `>=`
- `<=`
- `&&` AND
- `||` OR

## Switch Case Statement

C also allows the use of switch case statements:

```c
switch(variable)
{
    case value1:
        //do something
        break;
    case value2:
        //do something
        break;
    default:
        //do something
}
```

It important to know that:
- The expression to switch on should be of `int` type (`int`, `char`,`enum`, etc.)
- The values in the cases have to be constant
- Switch case in C falls through, so using breaks is necessary but similar cases can also be stacked

## While Loop
Similar to other languages, just accepts a condition
```c
int x = -10;
while(x <= 10)
{
    printf("%d\n",x);
    x += 2;
}
```
> `while(1)` is for an infinite loop

## Do While Loop
Similar to the while loop but executes first and then checks the condition. So always executes at least once
```c
char letter = 'A';
do
{
    printf("%c\n",letter);
    letter++;
}
while(letter != 'Z');
```

## For loop
Similar to other languages, includes:
- Initialization
- Looping Condition
- Accumulation

```c
for(int i = 1; i <= 20; i++)
{
    printf("%d\n",i);   
}
```

## Break and Continue

The `break` statement ends the loop immediately when it is encountered. Its syntax is:

```c
break;
```

The `continue` statement skips the current iteration of the loop and continues with the next iteration. Its syntax is:

```c
continue;
```

## C `goto` Statement

The `goto` statement allows us to transfer control of the program to the specified label.

Syntax of `goto` Statement:

```c
goto label;
... .. ...
... .. ...
label: 
statement;
```

The label is an identifier. When the `goto` statement is encountered, the control of the program jumps to `label:` and starts executing the code.


Example: 

// Program to calculate the sum and average of positive numbers
// If the user enters a negative number, the sum and average are displayed.

```c
#include <stdio.h>

int main() {

   const int maxInput = 100;
   int i;
   double number, average, sum = 0.0;

   for (i = 1; i <= maxInput; ++i) {
      printf("%d. Enter a number: ", i);
      scanf("%lf", &number);
      
      // go to jump if the user enters a negative number
      if (number < 0.0) {
         goto jump;
      }
      sum += number;
   }

jump:
   average = sum / (i - 1);
   printf("Sum = %.2f\n", sum);
   printf("Average = %.2f", average);

   return 0;
}
```

Output: 

```
1. Enter a number: 3
2. Enter a number: 4.3
3. Enter a number: 9.3
4. Enter a number: -2.9
Sum = 16.60
Average = 5.53
```


Important is that: 
- The use of `goto` statement may lead to code that is buggy and hard to follow.
- Also, the `goto` statement allows you to do bad stuff such as jump out of the scope.
- That being said, `goto` can be useful sometimes. For example: to break from nested loops.
- `goto` is rarely useful and you can create any C program without using `goto` altogether.

------------------------------
## [Back to Index](../Aa_Index.md)