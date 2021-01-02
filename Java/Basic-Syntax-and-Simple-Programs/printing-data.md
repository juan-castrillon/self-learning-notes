# Printing data

## Displaying text using `println()` and `print()`

Standard output is a receiver to which a program can send information (text). It is supported by all common operating systems. Java provides a special object `System.out` to work with the standard output. We will often use it to print something.

The `println` method displays the passed string followed by a new line on the screen (print-line). As an example, the following code fragment prints four lines.

```java
System.out.println("I ");
System.out.println("know ");
System.out.println("Java ");
System.out.println("well.");
```

The output:

```
I
know
Java
well.
```

All strings were printed as is, without the double quotes.

The method allows you to print the empty line when no string is given:

```java
System.out.println("Java is a popular programming language.");
System.out.println(); // prints empty line
System.out.println("It is used all over the world!");
```
The output:

```
Java is a popular programming language.

It is used all over the world!
```
The print method displays the passed value and places the cursor (the position where we display a value) after it. As an example, the code below outputs all strings in a single line.

```java
System.out.print("I ");
System.out.print("know ");
System.out.print("Java ");
System.out.print("well.");
```
The output:

```
I know Java well.
```
Pay attention to the spaces between words. We pass them to methods for printing.

## Printing numbers and characters
Both methods `println` and `print` allow a program to print not only strings and characters, but also numbers.

Let's print two secret codes.

```java
System.out.print(108);   // printing a number
System.out.print('c');   // printing a character that represents a letter
System.out.print("Q");   // printing a string
System.out.println('3'); // printing a character that represents a digit

System.out.print(22);
System.out.print('E');
System.out.print(8);
System.out.println('1');
```
It outputs:

```
108cQ3
22E81
```

Like strings, none of the characters contain quotes.