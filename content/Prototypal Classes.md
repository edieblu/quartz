---
tags:
  - ✅
sr-due: 2026-07-16
sr-interval: 721
sr-ease: 270
---

⬅️ [[YDKJS Chapter 5]]
## Prototypal Classes

A prototypal class with `Object.create(..)`

```js
var Classroom = {
    welcome() {
        console.log("Welcome, students!");
    }
};

var mathClass = Object.create(Classroom);

mathClass.welcome();
// Welcome, students!
```

- All functions by default reference an empty object at a property named `prototype`.
- This is not the function's prototype (where the function is prototype linked to), but rather the prototype object to link to when other objects are created by calling the function with `new`.

- So you could do this instead:

```js
function Classroom() {
    // ..
}

Classroom.prototype.welcome = function hello() {
    console.log("Welcome, students!");
};

var mathClass = new Classroom();

mathClass.welcome();
// Welcome, students!
```

- The "prototypal class" pattern is now strongly discouraged, in favor of using **ES6's class mechanism**:

```js
class Classroom {
    constructor() {
        // ..
    }

    welcome() {
        console.log("Welcome, students!");
    }
}

var mathClass = new Classroom();

mathClass.welcome();
// Welcome, students!
```

- Under the covers, the same prototype linkage is wired up, but this class syntax fits the class-oriented design pattern much more cleanly than "prototypal classes".