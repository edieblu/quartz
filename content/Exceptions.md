---
tags:
  - ✅
published: true
sr-due: 2025-08-30
sr-interval: 483
sr-ease: 250
---
⬅️ [[FEM TypeScript Fundamentals]]

## Exceptions
- We can never say `catch (e: Error)`, we can only `catch (e: any)` or `catch (e: unknown)`.
- catch the error as `catch (e: unknown)`, then using `e instanceof OurErrorClass` as a type guard.
```ts
let error: Error;

try {
  throw new Error('something broke');
} catch (e: unknown) {
  /* We can only catch exceptions as `unknown` or `any`. We use `unknown`
   * because it's safer, but then we have to narrow the type with a
   * conditional. */
  if (e instanceof Error) {
    error = e;
  } else {
    throw new Error("We can't handle that type of exception!");
  }
}
error.message;

// Result:
'something broke'
```