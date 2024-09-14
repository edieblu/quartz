---
tags:
  - ✅
sr-due: 2027-10-19
sr-interval: 1150
sr-ease: 250
---

⬅️ [[FEM TypeScript Fundamentals]]
## Nullish coalescing ??
- `null` means there's a value, and the value is nothing
- `undefined` means the value isn't available (yet)
- similar to the JavaScript logical OR operator, `||`. But unlike `||`, it doesn't treat `0` and `''` as falsey.
- aka "returning the first value that isn't `null` or `undefined`"

```ts
1 ?? 'default' === 1
0 ?? 'default' === 0
'a' ?? 'default' === 'a'
'' ?? 'default' === ''
null ?? 'default' === 'default'
undefined ?? 'default' === 'default'
```

```ts
function numberOrOne(n: number | undefined): number {
  return n ?? 1;
}
[numberOrOne(3), numberOrOne(undefined), numberOrOne(0)];

// Result:
[3, 1, 0]
```