---
tags:
  - ✅
published: true
sr-due: 2027-06-11
sr-interval: 1134
sr-ease: 250
---
⬅️ [[Code Complete]]

## Structures
- structure refers to data that's built up from other types (aka `struct`)
- structures bundle groups of related items together
- use structures to simplify parameter lists e.g. `routine(name, age, gender)` vs `routine(employee)`
- use structures to reduce maintenance

**🤔 What is the difference between a class and a structure?**
(in C++) A Structure is not secure and cannot hide its implementation details from the end-user while a class is secure and can hide its programming and designing details.
 - use struct for plain-old-data structures without any class-like features;
 - use class when you make use of features such as private or protected members, non-default constructors and operators, etc.

C has structs, it has no concept of encapsulation, so everything is public.

## Pointers
- every pointer consists of two parts: a location in memory and a knowledge of how to interpret the contents of that location

### Location in memory
- an address often expressed in hexadecimal notation
- the pointer only contains this address

### Interpreting the contents
- if a pointer points to an integer, the compiler interprets the memory location given by the pointer as an integer
- memory doesn't have any inherent interpretation associated with it
- a pointer error is usually the result of a pointer pointing somewhere it shouldn't (memory corruption)

## Global data
- global variables are accessible anywhere in the program
- used for preserving global values
- make variables local and global only if you need them
- you should have naming conventions to differentiate among local, class and global data
- anything you can do with global data, you can do better with access routines