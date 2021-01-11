---
title: Stream Filtering
parent: Functional Programming
grand_parent: Java
nav_order: 8
---

# Stream Filtering 

Filtering is an important operation that allows to obtain only those elements of the collection that meet a specified condition. 


## The filter method
To filter elements, streams provide the `filter` method. It returns a new stream consisting only of those elements that match the given predicate.

As an example, here is a list of prime numbers (a prime number is a whole number greater than 1 whose only factors are 1 and itself):

```java
List<Integer> primeNumbers = Arrays.asList(2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31);
```

We'd like to create a new list consisting of prime numbers that belong to the range from 11 to 23 (inclusively).

```java
List<Integer> filteredPrimeNumbers = primeNumbers.stream() // create a stream from the list
        .filter(n -> n >= 11 && n <= 23) // filter elements
        .collect(Collectors.toList());   // collect elements in a new list
```

So, the `filteredPrimeNumbers` list is:

```
[11, 13, 17, 19, 23]
```

Since the `filter` method takes a predicate, it is possible to instantiate an object directly and pass it to the method.

```java
Predicate<Integer> between11and23 = n -> n >= 11 && n <= 23; // instantiate the predicate

List<Integer> filteredPrimeNumbers = primeNumbers.stream() // create a stream from the list
        .filter(between11and23)        // pass the predicate to the filter method
        .collect(Collectors.toList()); // collect elements in a new list
```

Of course, the result is the same as before.

## Using multiple filters
Sometimes, two or more filters are used together. For example:

- to separate a complex logic from a single filter;
- to filter the stream, then process it by other methods and then filter again.


Let's consider an example. Given a list of programming languages with empty strings.

```java
List<String> programmingLanguages = Arrays.asList("Java", "", "scala", "Kotlin", "", "clojure");
```

We'd like to count how many programming languages start with an upper letter ignoring all the empty strings.

```java
long count = programmingLanguages.stream()
        .filter(lang -> lang.length() > 0) // consider only non-empty strings
        .filter(lang -> Character.isUpperCase(lang.charAt(0)))
        .count(); // count suitable languages
```
The count is `2` (`"Java"`, `"Kotlin"`).

These two filter operations can be replaced with a single operation that takes a complex predicate:

```java
filter(lang -> lang.length() > 0 && Character.isUpperCase(lang.charAt(0)))
```
