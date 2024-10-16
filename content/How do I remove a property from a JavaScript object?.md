---
tags:
  - ✅
sr-due: 2024-11-02
sr-interval: 36
sr-ease: 276
---

⬅️ [[JavaScript]]
🔗  [Stack Overflow](https://stackoverflow.com/questions/208105/how-do-i-remove-a-property-from-a-javascript-object)

- use the `delete` keyword
```javascript
var obj = {
  myProperty: 1    
}
console.log(obj.hasOwnProperty('myProperty')) // true
delete obj.myProperty
console.log(obj.hasOwnProperty('myProperty')) // false
```

- or with destructuring
```javascript
const { a, ...rest } = { a: 1, b: 2, c: 3 };
```