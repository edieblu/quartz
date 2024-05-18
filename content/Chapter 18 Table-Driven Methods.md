---
published: true
tags:
  - ✅
sr-interval: 498
sr-due: 2024-05-13
sr-ease: 270
sr-due: 2038-04-01
sr-interval: 5071
sr-ease: 290
---

⬅️ [[Code Complete]]

- a table driven method is a scheme that allows you to look up information in a table rather than using (complicated) logic statements

### Direct Access Table
- allows you to access the table element you are interested in directly
![[Pasted image 20211115144219.png]]

### Indexed Access
- when you use indexes, you use the primary data to look up a key in an index table and then use the value from the index table to lookup the main data you're interested in
- and so rather than being accessed directly, an indexed access table is accessed via an intermediate index

Advantages: 
- A lot less space to create an index array with a lot of wasted space
- Cheaper to manipulate entries in an index than entries in a main table
- Maintainability by putting index-access code in its own routine
![[Pasted image 20211115144234.png]]

### Stair-step access
- entries are valid for ranges of data rather than for distinct data points

Advantages:
- It works well with irregular data
- Flexible, modifiable
![[Pasted image 20211115144321.png]]