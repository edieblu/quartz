---
tags:
  - ✅
published: true
sr-due: 2026-02-12
sr-interval: 592
sr-ease: 250
---
⬅️ [[FEM TypeScript Fundamentals]]
## Readonly value vs property
```ts

// can't replace it, but can mutate it
type User = {
  name: string
  readonly catNames: string[]
};

// can't mutate the array, but can replace it
type User = {
  name: string
  catNames: ReadonlyArray<string>
};

// safest
type User = {
  name: string
  readonly catNames: ReadonlyArray<string>
};

```