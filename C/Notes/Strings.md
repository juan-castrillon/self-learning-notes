---
title: Strings
parent: C
has_children: false
nav_order: 4
---

# Strings

- Strings are not a type in C, instead are represented by a `char[]`
- The final character is always the null character `'\0'`. This has to be accounted for in the size
- Use double quotes `"` (instead of single like `char`)

As with any array, the size can be left empty if assigned immediately: 
```c
char buffer[] = "something";
```
Or it need to be declared:
```c
char buffer[15]; //Here it has space for 14 characters (+ null)
//do something
```

------------------------------
## [Back to Index](../Aa_Index.md)