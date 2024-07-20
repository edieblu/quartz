---
sr-due: 2028-08-21
sr-interval: 1500
sr-ease: 270
published: true
tags:
  - ✅
---

⬅️ [[Execute Program JavaScript Concurrency]]
## Promise constructor is synchronous
- When we do `new Promise(...)` and pass a callback to the constructor, that cb is ran immediately (even if you wrapped with a `setTimeout`)
```js
const array = [];
array.push('before');

new Promise(resolve => {
  array.push('constructed');
});

array.push('after');
array;

// Result:
['before', 'constructed', 'after']
```
- but `then` always works async	
- 💡  Constructor callbacks always run immediately and synchronously, while `then` callbacks are scheduled to run asynchronously.