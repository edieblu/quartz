---
tags:
  - ✅
published: true
sr-due: 2030-12-17
sr-interval: 2402
sr-ease: 310
---
⬅️ [[CS50]]

- 🔗 [Course Website](https://cs50.harvard.edu/x/2021/weeks/3/)

## Big O notation (*O*)

- for describing the running time of algorithms (how many steps max will it take)
- `O(n)` - on the order of n

**🤔 And what's in the opposite end of Big O?**

- `Ω` Greek Omega letter used to describe the best-case scenario (Ω of ...)
- They are both approximations

## Linear search
- Iterate across the array from left to right, trying to find the target element.

```c
for i from 0 to n-1
  If i-th  element is "value you are looking for"
    return true
return false
```

## Binary search

- Given a sorted array, divide and conquer by systematically eliminating half of the remaining elements (phone book) in the search for the target element.

```c
if no items
  return false
if middle item is "value you are looking for"
  return true
else if "value you are looking for" < middle item
  search left half
else if "value you are looking for" > middle item
  search right half
```

### Sorting

- In C you can't use double equal to compare two strings (yes for `int` and yes for `char`)
- instead you have to use a function like `strcmp()` found in `<string.h>` file


**🤔 What's a hertz?**

- something that is done once per second
- if your computer's CPU is 1 gigahertz, that means that it can do 1 billion things at a time

## Custom types

**🤔 What is a struct?**
It's a container inside which you can put multiple other data types.

```c

// define the struct
typedef struct
{
  string name;
  string number;
}
person;

// initialize the array people with length of two
// using the person struct
person people[2]

// assign value
people[0].name = "Eva";
people[0].number = "123-456-789";
```

## Selection sort

- Find the smallest unsorted element in an array and swap it with the first unsorted element of that array.
- The amount of work will decrease with each iteration.
- However, you can't short circuit and quit the work even if all the elements are already swapped

```c
for i from 0 to n-1
  find smallest item between i'th item and last item
  swap the smallest item with the i'th item
```

## Bubble sort

- Swap the adjacent pairs of elements if they are out of order, effectively **bubbling larger elements** to the right and smaller ones to the left.

```c
Repeat n-1 times
  for i from 0 to n-2
    if i'th and i+1'th elements out of order
      swap them
  if no swaps
      Quit
```

## Merge sort

- Split the full array into subarrays, then merge those subarrays back together in the correct order.
- Meaning that in an array of size 8, you'll start with 8 lists of size 1
- You'll need some temporary arrays to help you with sorting, meaning you'll be needing at least twice as much space

```c
if only one item
  return
else
  sort left half of items
  sort right half of items
  merge sorted halves
```
 ![[Pasted image 20211208141424.png]]

## Insertion sort

- Proceed once through the array from left to right, shifting elements as necessary to insert each element into its correct place.

🤔 **How do the algorithms compare In terms of running time (slowest -> fastest)?**

In terms of Big O:

- `O(n2)` bubble sort, selection sort, insertion sort
- `O(n log n)` merge sort
- `O(n)` linear search
- `O(log n)` binary search
- `O(1)`

In terms of Ω:

- `Ω(n2)` selection sort
- `Ω(n log n)` merge sort
- `Ω(n)` bubble sort, insertion sort
- `Ω(log n)`
- `Ω(1)` linear search, binary search

## θ Theta

for describing algorithms where `O` and`Ω` values are the same

- `θ(n2)` selection sort
- `θ(n log n)` merge sort
- `θ(n)`
- `θ(log n)`
- `θ(1)`

## Recursion

- A function calling itself.

- Classic example is the factorial:
  `fact(n) = n * fact(n-1)`

Every factorial has two cases:

- base case: when triggered, will terminate the recursive process
- recursive case: which is where recursion actually occurs

```c
int fact(int n)
{
  if (n == 1)
    return 1;
  else
    // With single line returns, you can take the curly braces away.
    return n * fact(n-1)'
}
```
