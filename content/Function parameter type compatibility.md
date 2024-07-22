---
aliases:
  - contravariance
tags:
  - ✅
published: true
sr-due: 2027-03-20
sr-interval: 972
sr-ease: 250
---

⬅️ [[Execute Program Advanced TypeScript]]
## Function parameter type compatibility
- in typescript narrower types are assignable to wider types
- BUT! Functions that take narrower types are not assignable to functions that take wider types.
```ts
function takesLiteralString(s: 'lastLoginDate'): string {
  return s;
}

type TakesString = (s: string) => string;

const testFunction: TakesString = takesLiteralString;
testFunction('lastLoginDate'); //Typescript Error
```
- For regular, non-function types, we can always assign narrower types to wider types. We can assign the literal type `'lastLoginDate'` to a `string` variable because the former has a narrower type.
- For function parameters, the same rule applies, but in reverse (we can assign functions that take wider parameters to function types that take narrower parameters.)
- It's fine to pass a `'lastLoginDate'` to a function that expects a `string`. It's also fine to pass a `[number, number]` to a function that expects an `Array<number>`.
- The technical term for what we've seen here is "contravariance". In most strict static languages, function types are "contravariant on the parameter types". That means "for function parameters, the normal rule about assigning narrower types to wider types is reversed".