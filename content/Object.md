---
published: true
tags:
  - ✅
sr-due: 2026-02-14
sr-interval: 609
sr-ease: 274
---

⬅️ [[Execute Program Modern JavaScript]]

## Object
- **getters**
```js
let userName = 'Amir';
const user = {
  get userName() { return userName}
}

// with destructuring
const user = {get name() { return 'Be' + 'tty'; }};
const {name} = user;
name;

// Result:
'Betty'

```

**setters**:
```js
const user = {
  realName: 'Amir',
  set userName(newName) { this.realName = newName; }
};

// another example
class User {
  constructor(name) {
    this.names = [name]
  }
   set name(newName) {
    this.names.push(newName);
  }
}
```

together:
```js
const user = {
  realName: 'Amir',
  get userName() { return this.realName; },
  set userName(newName) { this.realName = newName; },
};

user.userName = 'Betty';
[user.realName, user.userName];

// Result:
['Betty', 'Betty']
```

Don't forget the `get` or `set` keyword:
```js
const user = {
  userName: function () { return 'Amir'; }
};
typeof user.userName;

// Result:
'function'
```

### Computed properties
```ts
const users = [
  {name: 'Amir', loginCount: 5},
  {name: 'Betty', loginCount: 16},
];

function loginCount(user) {
    return {[user.name]: user.loginCount}
}
```