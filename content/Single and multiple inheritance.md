---
tags:
  - ✅
sr-due: 2025-11-25
sr-interval: 528
sr-ease: 250
---

⬅️ [[FEM TypeScript Fundamentals]]
## Single and multiple inheritance
- In JavaScript and TypeScript, classes can only extend one other class. This is called "single inheritance", in contrast to the "multiple inheritance" allowed by some other languages.
- Implementing two incompatible interfaces doesn't give us a `never` type. Instead, it causes an error directly in the class definition.
```ts
interface NameMustBeString {
  name: string
}

interface NameMustBeNumber {
  name: number
}

class User implements NameMustBeString, NameMustBeNumber {
  name: string;
  
  constructor(name: string) {
    this.name = name;
  }
}

const amir = new User('Amir');
amir.name;

//Result:
type error: Property 'name' in type 'User' is not assignable to the same property in base type 'NameMustBeNumber'.
  Type 'string' is not assignable to type 'number'.
```