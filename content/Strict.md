---
tags:
  - ✅
sr-due: 2027-03-15
sr-interval: 919
sr-ease: 252
---

⬅️ [[FEM TypeScript Fundamentals]]
## Strict
- `noImplicitAny`: forces us to provide explicit types for every function parameter
- `strictNullChecks`: TypeScript doesn't allow us to assign `null` or `undefined` to variables unless their types include `null` or `undefined`
- `strictPropertyInitialization`
- `strictFunctionTypes`

- Strict mode is disabled by default, always set: 
```ts
{"compilerOptions": {"strict": true}}
```