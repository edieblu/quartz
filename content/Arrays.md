---
published: true
tags:
  - ✅
sr-due: 2027-05-30
sr-interval: 1046
sr-ease: 250
---

⬅️ [[CS50 Week 05 - Data Structures]]
## Arrays
- Arrays are contiguous blocks of memory
- Arrays aren't easily resizable

🤔 Garbage values aren't bad - you just don't know what they are.

**Summary**
- insertion is bad 
	- in the case when the array is not big enough (O(n))
	- if the array is big enough and we have the index Omega of 1
- deletion is bad
- lookup is great (random access constant time)
- relatively easy to sort
- relatively small size-wise
- stuck with a fixed size, no flexibility