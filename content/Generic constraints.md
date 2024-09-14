---
tags:
  - ✅
sr-due: 2027-03-31
sr-interval: 973
sr-ease: 290
---


⬅️ [[Execute Program Advanced TypeScript]]
## Generic constraints
- Constraints let us say "this can be any type... as long as it's compatible with this other type".
- They are a way to voluntarily constrain ourselves, so that we can only see a small piece of a type inside of the function.
- We do this by adding the generic constraint `<T extends {age: number}>`. In TypeScript, we can always add `extends ...` to a generic type parameter. Anywhere we can write `<T>`, we can also write `<T extends ...>`.
```ts
function filterBelowAge<T extends {age: number}>(
  things: Array<T>,
  limit: number
): Array<T> {
  return things.filter(thing => thing.age < limit);
}
```
- Inside the function, `T` always has the property `age: number`. That forces us to write the function in a way that works for any object with an age. Using the type in any other way is a type error.
- Generic constraints are a critical feature of TypeScript, but they show up primarily in library or framework code