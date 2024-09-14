---
tags:
  - ✅
sr-due: 2026-09-09
sr-interval: 743
sr-ease: 270
---

⬅️ [[Execute Program JavaScript Concurrency]]
## Using Resolve later
- We can store the `resolve` function in a variable. This allows us to "capture" the `resolve` function, then use it outside of the `new Promise` constructor.
```js
let savedResolve;

const promise = new Promise(resolve => { savedResolve = resolve; });

/* The `savedResolve` variable now contains the function that we got from the
 * `new Promise` constructor. Calling it will fulfill the promise, even
 * though it now looks like "savedResolve" and "promise" are unrelated. */
savedResolve(3);
promise;
// Async Result:
{fulfilled: 3}

```

- The net effect of this is: we can split promises into two pieces. We might pass the `resolve` function to one part of the system, then pass the promise itself to a totally different part. When the "reading" side tries to look inside the promise with a `then`, it will have to wait until the "writing" side has called `resolve`.

```js
let savedResolve;
const promise = new Promise(resolve => { savedResolve = resolve; })
  .then(n => n * 2);
setTimeout(() => savedResolve(3), 1000);
promise;

// Async Result:
{fulfilled: 6}
```
- we can only resolve the promise once