---
published: true
tags:
  - ✅
sr-due: 2025-09-06
sr-interval: 487
sr-ease: 250
---

⬅️ [[Code Complete]]
🤔 Testing is the most popular quality-improvement quality

## Type of testing
- black-box testing: in which the tester cannot see the inner workings of the item being tested
- white-box testing: in which the tester is aware of the inner workings

🤔 Developers should spend 8%-25% of the total project time doing tests
- test for every design requirement
- TDD has many benefits
- since exhaustive testing is impossible, the are of testing is that of picking the test cases most likely to find errors

Structured basis testing (minimum number o cases to test the path of your program)
- start with 1, the add 1 for each `if`, `while`, `repeat`, `for`, `&&`, `||`
- add 1 for each case in a case statement

- Data flow testing is based on the idea that data usage is at least as error-prone as control flow
- Data can be defined, used or killed

## Error guessing (testing for common-sense errors)
- test for off-by-one errors (and other boundary analysis)
- bad data: too little, too much, wrong kind or size, uninitialized 
- test minimum normal config (saving an empty doc) and max normal config
- test if compatible with old data

## Where are most errors found?
- most errors tend to be concentrated in a few highly defective routines
- 80% of the errors are found in 20% of a project's classes or routines
- maintenance activities should be focused on identifying, redesigning, and rewriting from the ground up those routines that have been identified as error-prone

## Types of errors:
- most common sources of errors were thin application-domain knowledge, fluctuating and conflicting requirements and communication and coordination breakdown
- typos are a super common
- so is the misunderstanding of the design

## How many errors should you expect to find?
- industry average experience is about 1-25 errors per 1000 lines of code for delivered software
- it is cheaper to build high-quality software than it is to build and fix low-quality software

Test cases are often as likely or more likely to contain errors than the code being tested

## Testing tools
- scaffolding: mock/stub object, stub routines, using dummy files
- random data generators
- coverage monitors
- logger
- debugger

## How to improve testing?
- plan to test from the beginning
- retest (regression testing): testing that the software hasn't taken a step backward
- automated testing
- keep test record data to determine whether your project is getting sicker or healthier