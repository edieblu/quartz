---
tags:
  - ✅
published: true
sr-due: 2028-08-22
sr-interval: 1492
sr-ease: 270
---

⬅️ [[CS50 Week 05 - Data Structures]]

```c
// an empty linked list
node *list = NULL
  
// We use sizeof(node) to get the right amount of memory to 
// allocate, and malloc returns a pointer that we save as n
node *n = malloc(sizeof(node))
	
// We want to make sure malloc succeeded in getting memory for us
if (n != NULL)
{
	
// This is equivalent to (*n).number, where we first go to the 
// node pointed to by n, and then set the number property. 
// In C, we can also use this arrow notation
    n->number = 1;
	
// Then we need to make sure the pointer to the next node in our // list isn't a garbage value, but the new node won't point to 
// anything (for now)
    n->next = NULL;
}
```

But steps involved are:

- dynamically allocate spare memory for a new node
- check to make sure we didn't run out of memory
- initialize the node's val field
- initialize the node's next field
- return a pointer to the newly created node

❗Always insert to the beginning of the list - you already have the pointer to the list's `HEAD`

One of the trickiest things with linked lists is figuring out the order of doing this - you certainly don't want to end up with an orphaned list! When inserting items, always make sure to point to the next item (i.e., previous head) first, before changing the `HEAD` of the list.

🤔 Every time you allocate memory with malloc, you need to check whether that value != NULL before doing stuff to it. Every time you stuff with pointers, you need to check for `NULL` as well.

**Tradeoff**: we need to allocate twice as much memory for each element in order to spend less time adding values. We can't use binary search.

**Summary**
- insertion is easy (O(1))
- deletion is easy
- lookup is bad (O(n))
- relatively difficult to sort
- relatively small-size (not as small as arrays)