---
tags:
  - ✅
sr-due: 2024-11-01
sr-interval: 40
sr-ease: 276
---

⬅️ [[JavaScript]]
🔗 [Stack Overflow](https://stackoverflow.com/questions/7486085/copy-array-by-value)


```js
let oldArray = [1, 2, 3, 4, 5];

let newArray = oldArray.slice();

console.log({newArray});
```

For references, strings and numbers (and not the actual object), **`slice()` copies object references into the new array.** Both the original and new array refer to the same object. If a referenced object changes, the changes are visible to both the new and original arrays.

Primitives such as strings and numbers are immutable, so changes to the string or number are impossible.

Elements can be: literal values, literal structures, or prototypes.

```javascript
// Literal values (type1)
const booleanLiteral = true;
const numberLiteral = 1;
const stringLiteral = 'true';

// Literal structures (type2)
const arrayLiteral = [];
const objectLiteral = {};

// Prototypes (type3)
const booleanPrototype = new Bool(true);
const numberPrototype = new Number(1);
const stringPrototype = new String('true');
const arrayPrototype = new Array();
const objectPrototype = new Object(); // or `new function () {}
```

From these elements we can create three types of arrays.

```javascript
// 1) Array of literal-values (boolean, number, string) 
const type1 = [ true, 1, "true" ];

// 2) Array of literal-structures (array, object)
const type2 = [ [], {} ];

// 3) Array of prototype-objects (function)
const type3 = [ function () {}, function () {} ];
```

Because `arr1` is an array of literal values (boolean, number, or string), you can use any deep copy technique discussed above, where `slice()` and spread `...` have the highest performance.