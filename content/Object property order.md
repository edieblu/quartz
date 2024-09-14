---
tags:
  - ✅
sr-due: 2026-03-30
sr-interval: 594
sr-ease: 250
---

⬅️ [[Execute Program Modern JavaScript]]

- always ordered the same way they were inserted (even with stringify and parse)
- except! when an object has number keys, (1) they always come first in the key list, (2) they're always sorted numerically, and (3) they're always converted into strings (1 becomes '1')
```js
Object.keys({b: 'b', 1: 'one', a: 'a'});

// Result:

['1', 'b', 'a']
```