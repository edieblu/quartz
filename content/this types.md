---
tags:
  - ✅
published: true
sr-due: 2025-08-13
sr-interval: 463
sr-ease: 250
---

⬅️ [[FEM TypeScript Fundamentals]]

## this types
```ts
function myClickHandler(
  this: HTMLButtonElement,
  event: Event
) {
  this.disabled = true
}
```