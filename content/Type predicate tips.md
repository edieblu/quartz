---
tags:
  - ✅
published: true
sr-due: 2029-01-27
sr-interval: 1569
sr-ease: 267
---

⬅️ [[Execute Program Advanced TypeScript]]
## Type predicate tips
Keep these two points in mind to prevent bugs when using type predicates:  
-   1.  TypeScript trusts us to implement type predicates correctly. Test your predicate functions well to make sure that they do what you think they do.
    2.  Type predicates can take unions as their arguments, or they can take `unknown`. In most cases, `unknown` is the safest and most flexible option.

## Indexing types with union types
- If `User` is `{name: string, age: number}`, then `User['name' | 'age']` is `string | number`.
```ts
type User = {
  name: string
  age: number
};

type NameOrAge = User['name' | 'age'];

const user = {
  name: 'Amir',
  age: 36,
};

type NameOrAge = (typeof user)['name' | 'age'];

const nameOrAge: NameOrAge = 'Betty';
nameOrAge;
```

Distributive property:
```ts
type User = {name: string, age: number};
type PropertyTypes1 = User['name' | 'age'];
type PropertyTypes2 = User['name'] | User['age'];
```