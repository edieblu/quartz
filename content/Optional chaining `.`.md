---
tags:
  - ✅
sr-due: 2028-02-08
sr-interval: 1221
sr-ease: 250
---

⬅️ [[FEM TypeScript Fundamentals]]
## Optional chaining `?.`
- if `someObject?` then `.property`
- `someObject?.property` means: `(someObject === null || someObject === undefined) ? undefined : someObject.property`
```ts
type Comment = {text: string};
function getComment(): Comment | undefined {
  return undefined;
}
getComment()?.text;

// another example
users.map(user => user?.address?.postalCode);
```