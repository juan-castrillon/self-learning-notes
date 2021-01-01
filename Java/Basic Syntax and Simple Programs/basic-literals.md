# Basic Literals

## Literals
Regardless of its complexity, a program always performs operations on numbers, strings, and other values. These values are called literals. There are many different sorts of literals in Java, but in this topic we will focus only on a few of them: the ones that surround us all the time in everyday life.

Let's consider integer numbers, strings, and characters in the format in which they are written in Java.

## Integer numbers
These numbers are used to count things in the real world. Also, we will often use them in Java.

Here are several examples of valid integer number literals separated by commas: `0, 1, 2, 10, 11, 100`.

If an integer value contains a lot of digits, we can add underscores to divide the digit into blocks for increased readability: `1_000_000`. It's more readable than the same value written as `1000000`.

## Characters

A single character can represent a digit, a letter or another symbol. To write a character we use single quotes as follows: `'A', 'B', 'C', 'x', 'y', 'z', '0', '1', '2', '9'`. Character literals can represent symbols of an alphabet, digits from `'0'` to `'9'`, whitespaces (`' '`), or other characters or symbols (`'$'`).

Do not confuse characters that represent numbers (e.g. `'9'`), with numbers themselves (e.g. `9`).

A character can't include two and more digits or letters because it represents only a single symbol. The following two examples are incorrect: 'abc', '543'. These literals contain too many characters.

## Strings
A string is a sequence of any individual characters. Strings represent text information such as a text of advertising, an address of a web page or a login on a site.

To write a string we use double quotes instead of single ones. Here are some valid examples: "text", `"I want to know Java"`, `"123456"`, `"e-mail@gmail.com"`. A string consisting of a single character like `"A"` is also a valid string, but do not confuse it with the `'A'` character.

As you can see, strings can include letters, digits, whitespaces, and other characters.
