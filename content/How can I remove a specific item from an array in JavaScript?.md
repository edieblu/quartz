---
tags:
  - ✅
sr-due: 2024-11-16
sr-interval: 36
sr-ease: 276
---

⬅️ [[JavaScript]]
- [Stack Overflow](https://stackoverflow.com/questions/5767325/how-can-i-remove-a-specific-item-from-an-array-in-javascript)
Find the `index` of the array element you want to remove using [`indexOf`](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array/indexOf), and then remove that index with [`splice`](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array/splice).

```javascript
const array = [2, 5, 9];

console.log(array);

const index = array.indexOf(5);
if (index > -1) { // only splice array when item is found
  array.splice(index, 1); // 2nd parameter means remove one item only
}

// array = [2, 9]
console.log(array); 
```