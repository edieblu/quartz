---
tags:
  - ✅
published: true
sr-due: 2027-07-04
sr-interval: 1100
sr-ease: 250
---

⬅️ [[Execute Program Advanced TypeScript]]
## Conditional types
- with the ternary operator
```ts
type WrapStringInArray<T> = T extends string ? Array<string> : T;
const s: WrapStringInArray<string> = ['hello'];
```

- with mapped types
```ts
type WrapStringsInArrays<T> = {
  [K in keyof T]: T[K] extends string ? Array<string> : T[K]
};

type User = {
  name: string
  email: string
  age: number
};

const amir: WrapStringsInArrays<User> = {
  name: ['Amir'],
  email: ['amir@example.com'],
  age: 36,
};
amir.name;

// another example, replacing nums with null
type ReplaceNumberPropertiesWithNull<T> = {
   [K in keyof T]: T[K] extends number ? null : T[K]
};
```
- 💡 Regular application code rarely needs conditional types.
- However, conditional and mapped types are critical in code that needs to be highly generic, like library and framework code.