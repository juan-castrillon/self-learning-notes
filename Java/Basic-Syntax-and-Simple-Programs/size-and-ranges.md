---
title: Size and Ranges
parent: Basic Syntax and Simple Programs
grand_parent: Java
nav_order: 6
---

# Size and ranges

In this lesson, we will discuss the classification and properties of primitive types provided by Java. Maybe you already know a few of them. The basic types can be separated into several groups according to meaning. Types from the same group can be operated in the same way, but have different sizes and, as consequence, represent different ranges of values.

You do not need to know all this information by heart, because it is easy to find it in the documentation or simply Google it. But a common understanding of these concepts is important in job interviews and practice.

## Numbers
Java provides several types for integers and fractional numbers. These types are often used in arithmetic expressions.

**Integer numbers** (0, 1, 2, ...) are represented by the following four types: `long`,`int`,`short`,`byte`(from the largest to the smallest). These types have different sizes and may represent different ranges of values. The range of an integer type is calculated as  $−2^{n−1}$ to $2^{n−1}−1$, where `n` is the number of bits. The range includes `0`, which is the reason for subtracting 1 from the upper bound.

- `byte`: size 8 bits (1 byte), range from -128 to 127
- `short`: size 16 bits (2 bytes), range from -32768 to 32767
- `int`: size 32 bits (4 bytes), range from $−(2^{31})$ to $(2^{31})−1$
- `long`: size 64 bits (8 bytes), range from $−(2^{63})$ to $(2^{63})−1$

The sizes of types are always the same. They do not depend on the operating system or hardware and cannot be changed.

The most commonly used integer types are `int` and `long`. Try to use `int` if it is enough for your purposes. Otherwise, use `long`.

```java
int one = 1;
long million = 1_000_000L;
```

**Floating-point** types represent numbers with fractional parts. Java has two such types: `double` (64 bits) and `float` (32 bits). These types can store only a limited number of significant decimal digits (~6-7 for `float` and ~14-16 for `double`). Usually, you will use the `double` type in practice.

```java
double pi = 3.1415;
float e = 2.71828f;
```

Note, that when we declare and initialize a `float` variable, we should mark the assigned value with the special letter `f`. It is often a good practice to mark a long value with `L` as well. We will learn more about numeric literals later.

## Characters

Java has a type named `char` to represent letters (uppercase and lowercase), digits, and other symbols. Each character is just a single letter enclosed in single quotes. This type has the same size as the `short` type (2 bytes = 16 bits).

```java
char lowerCaseLetter = 'a';
char upperCaseLetter = 'Q';
char dollar = '$';
```
Characters represent symbols from many alphabets including hieroglyphs, as well as some special symbols which will be studied in the following lessons.

## Booleans
Java provides a type called `boolean`, which can store only two values: `true` and `false`. It represents only one bit of information, but its size is not precisely defined.

```java
boolean enabled = true;
boolean bugFound = false;
```

We will often use this type in conditionals and as a result of comparing two numbers.

As a recap, we note that the types used most often are `int`, `long`, `boolean`, `char`, and `double`. Also, remember that `long` is the widest integer type. Knowledge of sizes and ranges of data types may help you with interviews.