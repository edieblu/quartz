---
tags:
  - ✅
sr-due: 2027-05-27
sr-interval: 1024
sr-ease: 250
---

⬅️ [[FEM TypeScript Fundamentals]]
#✅ 

## Nullish values

### null
- `null` means: there is a value, and that value is nothing. 

### undefined
- `undefined` means the value isn’t available (yet?)

```ts
let notDefined: undefined = null;
notDefined;

// Result:

type error: Type 'null' is not assignable to type 'undefined'.
```

### void
- `void` should exclusively be used to describe that a function’s return value should be ignored

### Non-null assertion operator
- aka optional chaining, the non-null assertion operator (`!`) is used to cast away the possibility that a value might be `null` or `undefined`.

```ts
type GroceryCart = {
  fruits?: { name: string; qty: number }[]
  vegetables?: { name: string; qty: number }[]
}

const cart: GroceryCart = {}

cart.fruits.push({ name: "kumkuat", qty: 1 })
cart.fruits!.push({ name: "kumkuat", qty: 1 })
```

### Definite assignment operator
- `!:`, same as above but used on class fields instead