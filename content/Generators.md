---
tags:
  - ✅
published: true
sr-due: 2026-11-24
sr-interval: 890
sr-ease: 270
---
⬅️ [[Execute Program Modern JavaScript]]
## Generators
```ts
// The * in function* marks our function as a generator.
function* numbers() {
  // Each yield in the generator provides one value to the loop.
  yield 1;
  yield 2;
  yield 3;
}

// generators are iterable
const results = [];
for (const n of numbers()) {
  results.push(n);
}
results;

//Result:
[1, 2, 3]

// converted to an array
function* letters() {
  yield 'a';
  yield 'b';
}
Array.from(letters());

Result:

['a', 'b']

// another example
function* numbers() {
  let x = 1;
  yield x;
  x += 1;
  yield x;
}
Array.from(numbers());

// Result:
[1, 2]

// and another one
function* numbersBelow(maximum) {
  for (let i=0; i<maximum; i++) {
    yield i;
  }
}
Array.from(numbersBelow(3));

Result:

[0, 1, 2]

```
- `yield` is like `return` but we can do it multiple times