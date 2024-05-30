---
published: true
tags:
  - ✅
sr-due: 2025-09-22
sr-interval: 489
sr-ease: 250
---
⬅️ [[Execute Program Modern JavaScript]]

## Destructuring
- sparse array destructuring
```ts
const letters = ['a', 'b', 'c', 'd'];
const [a, , c] = letters;
[a, c];

// Result:
['a', 'c']
```

- undefined when no indexes
```js
const letters = ['a', 'b', 'c'];
const [a, b, c, d] = letters;
[c, d];

// Result:
['c', undefined]
```

- collecting the rest (Rest element must be last element)
```js
const letters = ['a', 'b', 'c'];
const [a, ...others] = letters;
others;

// Result:
['b', 'c']
```

- object destructuring
```ts
const key = 'name';
const {[key]: value} = {name: 'Amir'};
value;
// Result:
'Amir'
```

- in function definitions
```ts
function getFirstArrayElement([first]) {
  return first;
}
getFirstArrayElement(['cat', 'dog', 'horse']);

// Result:

'cat'
```

- in `for-of` loops
```ts
const users = [{name: 'Amir'}, {name: 'Betty'}];
const names = [];
for (const {name} of users) {
  names.push(name);
}
```

- nested destructuring
```ts
//arays

const dataPoints = [
  [10, 20],
  [30, 40]
];

const [, [, y2]] = dataPoints
//Result 
40

const user = {
  name: 'Amir',
  address: {
    city: 'Paris',
  },
};
const {address, address: {city}} = user;
[city, address];

//Result

```