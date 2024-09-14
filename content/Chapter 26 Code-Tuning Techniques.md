---
tags:
  - ✅
sr-due: 2028-04-15
sr-interval: 1323
sr-ease: 250
---

⬅️ [[Code Complete]]
- refactorings are changes that improve a program's internal structure while code tuning changes degrade the internal structure in exchange for gains in performance
- if the changes didn't degrade the internal structure, we wouldn't consider them optimizations; we would use them by default and consider them to be standard coding practice
- computers have become so powerful that for many common kinds of programs, the level of performance optimization explained here is irrelevant (embedded systems, real-time systems etc might still benefit)
- always insist on measurable improvement
- results will vary widely with different languages, compilers and environments

### Logic
- use short-circuit evaluation
- perform selective looping and exit the loop as soon as a condition is met
- order tests by frequency (normal case)
- compare performance of similar logic structures (`if`/ `else` vs `case`)
- use lazy evaluation (only do the work if needed)

### Loops
- switching: making a decision inside a loop every time it's executed. Use unswitching instead (make the decision outside the loop)
- jamming (or fusion): combining two loops that operate on the same set of elements
- loop unrolling: handling two or more cases in each pass (instead of one) - be vary of off-by-one errors!
- minimize the work done inside loops
- sentinel values 🤷‍♀️ (used with linear searches)
- putting the busiest loop on the inside
- strength reduction: replace an expensive operation (multiplication) with a cheaper one (addition)

### Data transformations
- use integers instead of floating points
- use the fewest array dimensions possible
- minimize array references
- use supplementary indexes (index for length)
- use caching: saving a few values in such a way that you can retrieve the most commonly used values more easily than the less commonly used values

### Expressions
- use algebraic identities; `not a and not b` better: `not (a or b)`
- strength reduction: addition > multiplication, multiplication > exponentiation, integers > floating-point numbers, single precision numbers > double precision numbers
- initialize as `const` instead of computing
- use the correct type of constant (to avoid type conversion)
- precompute results
- eliminate common subexpressions

### Routines
- rewrite routines inline