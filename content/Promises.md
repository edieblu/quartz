---
tags:
  - ✅
sr-due: 2027-06-04
sr-interval: 1028
sr-ease: 250
---

⬅️ [[FEM TypeScript Fundamentals]]
## Promises
- TypeScript needs to statically type promises, just like it does for other code.
- All promises have the type `Promise<T>`, where `T` is the type of the value inside the promise
-  It's easy to forget to give functions a `Promise` return type.

```ts
//👎
const promise: number = Promise.resolve(100);
promise;

//Async Result:

type error: Type 'Promise<number>' is not assignable to type 'number'.
```