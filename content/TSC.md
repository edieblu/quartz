---
published: true
tags:
  - ✅
sr-due: 2025-08-31
sr-interval: 478
sr-ease: 250
---
⬅️ [[FEM TypeScript Fundamentals]]

## TSC
Recommended setup (from execute program)

- `--strict` This enables all strict type checking options, including `--noImplicitAny` and several others.
- `--noImplicitReturns`. This reports an error when a function has a declared return type, but some code paths don't return a value. Without this option, your functions may return undefined values without you realizing it.
- `--noFallthroughCasesInSwitch`. With this option, the compiler will tell you when you accidentally write a case statement with no break or return.
- `--noUnusedLocals`. This options prevents unused local variables, which are usually a mistake.