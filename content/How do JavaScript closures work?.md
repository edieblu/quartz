---
tags:
  - ✅
sr-due: 2024-09-22
sr-interval: 10
sr-ease: 276
---

⬅️ [[JavaScript]]
🔗 [StackOverflow](https://stackoverflow.com/questions/111102/how-do-javascript-closures-work)

A closure is a pairing of:

1. A function and
2. A reference to that function's outer scope (lexical environment)

A lexical environment is part of every execution context (stack frame) and is a map between identifiers (i.e. local variable names) and values.

Every function in JavaScript maintains a reference to its outer lexical environment. This reference is used to configure the execution context created when a function is invoked. This reference enables code inside the function to "see" variables declared outside the function, regardless of when and where the function is called.

If a function was called by a function, which in turn was called by another function, then a chain of references to outer lexical environments is created. This chain is called the scope chain.

In the following code, `inner` forms a closure with the lexical environment of the execution context created when `foo` is invoked, _closing over_ variable `secret`:

```javascript
function foo() {
  const secret = Math.trunc(Math.random() * 100)
  return function inner() {
    console.log(`The secret number is ${secret}.`)
  }
}
const f = foo() // `secret` is not directly accessible from outside `foo`
f() // The only way to retrieve `secret` is to invoke `f`
```

If JavaScript did not have closures, then more states would have to be passed between functions _explicitly_, making parameter lists longer and code noisier.

Returning a `function` from inside another function is the classic example of closure, because the state inside the outer function is implicitly available to the returned inner function, even after the outer function has completed execution.

A closure is created when a function is declared; this closure is used to configure the execution context when the function is invoked.