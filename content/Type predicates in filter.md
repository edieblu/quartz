---
tags:
  - ✅
sr-due: 2027-04-25
sr-interval: 988
sr-ease: 290
---

⬅️ [[Execute Program Advanced TypeScript]]
## Type predicates in filter
- if we `filter` an `Array<string | number>` and just want to get the numbers out, the return type will still be `(string | number)[]`
- you can fix this with a type predicate e.g. `isNumber` 
```ts
function isNumber(maybeNumber: number | string): maybeNumber is number {
  return typeof maybeNumber === 'number';
}

const numbersAndStrings: (number | string)[] = [1, 'a', 2, 'b'];
/* This assignment works because `filter` respects our `isNumber` type
 * predicate. This `filter` call narrows the array from (number |
 * string)[] to just number[]. */
const numbers: number[] = numbersAndStrings.filter(isNumber);
numbers;
```
- it does that by using generic constraints and function overloads
```ts
// ts filter definition
interface Array<T> {
  filter<S extends T>(
	// used when given a type predicate function as the callback
    predicate: (value: T) => value is S
  ): Array<S>
  filter(
    predicate: (value: T) => unknown
  ): Array<T>
}
```