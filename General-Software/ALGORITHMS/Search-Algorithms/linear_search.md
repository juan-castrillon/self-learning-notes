---
title: Linear Search
parent: Search Algorithms
grand_parent: Algorithms
nav_order: 1
---

# The linear search algorithm

Linear search (or sequential search) is a simple algorithm for searching an element with a specific value in the array. The algorithm checks each array element until it finds the target value or reaches the array end.

In the worst case, it performs exactly $n$ comparisons where $n$ is the length of the input array. The time complexity is $O(n)$.

## Example
Suppose, we have an array of $6$ elements:

![img](../../Java/img/linear1.PNG)

Our goal is to find the index of an element with the value $20$. We will start from the first element with index $0$ and compare each array element with the target value until we find the target value.

![img2](../../Java/img/linear2.PNG)

As you may see, the linear search is a simple algorithm with an important advantage: it can search in unsorted arrays.

## Possible modifications

Possible modifications of the linear search algorithm are:

- check whether the array contains an element, return `true` or `false`;
- search for the first or the last occurrence of an element in the array;
- count all occurrences of an element in the array;
- search for all occurrences of an element in the array;
- search for an element in the subarray of the array with the given indices.
- 
Also, the linear search algorithm can be used as a subroutine in more complex algorithms. For example, to count all occurrences of all array elements in another array.

If we know that our array is sorted (e.g. in ascending order), we could modify the linear search algorithm. If the next checked element is greater than the target value, it means we will not find the value in the rest of the array, and the algorithm should stop.


[Here](https://www.cs.usfca.edu/~galles/visualization/Search.html) is a visualization of the algorithm. To see it, enter the target value and select Linear Search at the top of the page.