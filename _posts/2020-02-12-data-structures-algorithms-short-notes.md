---
layout:     post
title:      Data Structures and Algorithms - Quick Review
date:       2020-02-12
summary:    Short notes about basic data structures and algorithms.
categories: Data-Science, Computer-Science, Programming
---

## Measuring algorithm performance

| Notation  | Example   |
|---|---|
| O(1) | looking up element in array  |
| O(log(n))  | Finding element in sorted array using binary search  |
|  O(n) | Searching unsorted array for a specific value   |
| O(n log(n)) | Complex softing algorithms like Merge-Sort and Heap-Sort  |
| O(n^2)  |  Simle sorting algorithms like Bubble-Sort & Insertion-Sort |


## Data Structures

### Arrays
- Collection of elements identified by a index or key.
- Stored contiguously in memory. Allows random access. 
- Usually (in most languages/implementations) zero indexed and cannot grow in size.
- If the implementation allows growing or shrinking the array, adding or deleting items in beginning or middle requires moving elements to new memory locations. Addring or deleting to end is O(1).

| Task  | Time Complexity  |
|---|---|
| Calculating item index  | O(1)  |
| Inserting or deleting in beginning  | O(n)  |
| Inserting or deleting in middle | O(n) |
| Inserting or deleting in end | O(1) |

### Linked List
- Collection of elements called nodes. 
- Not stored contiguously in memory.
- Nodes contain (data, pointer_next). pointer_next has points to location of next node. Doubly linked list has pointer_prev that points to previous node.
- Suitable for collections of items of different types that grows or shinks.
- Items can be added or removed easily. Memory does not need reorganization.

For a singly linked list:
| Task  | Time Complexity  |
|---|---|
| Finding a specific item   | O(n)  |
| Inserting or deleting to Head  | O(1)  |
| Inserting or deleting in middle | O(n) |
| Inserting or deleting in end | O(n) |


### Stacks (LIFO)
- Stack of elements that supports push and pop.
- LIFO: last in first out.
- Push and Pop:  O(1)

Applications:
- Expression processing / syntax parsing. 
- Backtracking: browser back stack.
- Function call stacks - keep track of which functions called what routines etc. 

### Queues (FIFO)
- Queue of elements that support add and remove.
- FIFO:  First in first out.
- Add and remove O(1)

Applications:
- Order processing
- Message queues (Ordering is not lost) 

### Hast Tables (Dictionaries)
- Associative arrays: elements stored in a (key, value) pair.
- Hash Fucntion + tie braking --> Allows assigining a unique key to unique location in memory (hence allowing access to the specific value stored there).
- Uniquely map a key to a specific value.
- Allow quick lookup, particluarly for large collections  -  O(1)
- Items not ordered in memory. 
- Finding keys close to other keys would require sorting.

## Recursion
- A function that calls itself.
- Simplifies the algorithm and code for certain iterative tasks by allowing you to reuse the functionality you have already written.
- Requires a breaking condition. 
- Uses the function call stack.

Applications: 
- Looking for a specific file in a nested directory structures. 

## Sorting 

### Bubble Sort
The highest items bubble up ot top

[a,b,c,d,e,f]
- Go from left to right
    1 Compare 2 elements (a, b)
    2 Swap if a > b (for ascending order)
    3 Move ahead one element and repeat steps (1,2) until end of array. 
    4 Start from left to right and repeat steps (1,2,3) until largest element has ended up to the right. 

Time complexity: Nested for loop: O(n^2)

### Merge Sort
- Divide and conquer approach that uses recursion.
- Good on large arrays.
- Compromizes on space complexity in the merging part.
 
Time complexity: O(n log(n))

#### Algorithm:

Recursively:
- Divide array in half until size of array = 1.
- Merge each element with next to form sorted array.

i.e. 
- Dividing array of size n by half to get single elements requires log(n) time for a array of size n. (log is base 2)
- Merging a sorted array of size n/2 with with another requires n comparisons. 

Recurrence relation:
T(n) = 2^i * T(n / 2^i) + i*n

When you reach single element T(1) = 1. T(1) happens when n / 2^i = 1 or i = log(n).
Simplifying the recurrence relation by using i = log(n) gives: 
T(n) =  n + nlog(n)

Hence, considering the dominant term for large n the time complexity is O(nlog(n)).


Check out
https://www.youtube.com/watch?v=g1AwUYauqgg


### Quick Sort










<!-- Links List Example

#### INSIDE BODY #####

## IMAGE
![Spark Components][spark_components]

## PAGE LINK
For more info on other components [look here][mapr_spark_article]

#### LINK FOOTER #####
[spark_components]: /notes/images/spark-components.png "Spark Componenets Image Link"
[mapr_spark_article]: https://mapr.com/ebooks/spark/03-apache-spark-architecture-overview.html
-->