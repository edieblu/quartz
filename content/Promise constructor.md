---
tags:
  - ✅
sr-due: 2026-03-31
sr-interval: 592
sr-ease: 250
---

⬅️ [[Execute Program JavaScript Concurrency]]


```js
new Promise(resolve => resolve(5));

// Async Result:
{fulfilled: 5}

new Promise((resolve, reject) => reject(new Error('it failed')));

// Async Result:
{rejected: 'Error: it failed'}
```

- One important thing to keep in mind: the `resolve` function that we get from the constructor is separate from the `Promise.resolve` method. And the `reject` function here is separate from the `Promise.reject` method.