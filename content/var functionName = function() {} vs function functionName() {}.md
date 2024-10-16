---
tags:
  - ✅
sr-due: 2024-11-22
sr-interval: 66
sr-ease: 296
---

⬅️ [[JavaScript]]
🔗 [StackOverflow](https://stackoverflow.com/questions/336859/var-functionname-function-vs-function-functionname)

The difference is that `functionOne` is a **function expression** and so only defined when that line is reached, whereas `functionTwo` is a **function declaration** and is defined as soon as its surrounding function or script is executed (due to [hoisting](http://adripofjavascript.com/blog/drips/variable-and-function-hoisting.html)).

Expression
```javascript
// TypeError: functionOne is not a function
functionOne();

var functionOne = function() {
  console.log("Hello!");
};
```


Declaration
```javascript
// Outputs: "Hello!"
functionTwo();

function functionTwo() {
  console.log("Hello!");
}
```

### Aliasing Functions
Functions can be aliased by assigning one function to multiple variables (e.g., `var xyz = abc`). This makes `xyz` and `abc` references to the same function object.

### Naming Functions
A function's `name` attribute depends on how it's defined. Named functions like `function abc(){}` have their name property set automatically, while anonymous functions assigned to variables have an empty name (e.g., `var abc = function(){}`).