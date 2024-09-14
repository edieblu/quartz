---
tags:
  - ✅
sr-due: 2027-12-14
sr-interval: 1216
sr-ease: 250
---

⬅️ [[Execute Program RegEx]]
## Maybe
- The `?` operator matches a character zero or one times, but not more than one.
```js
/^a?$/.test('a'); // true
/^a?$/.test(''); // true
/^a?$/.test('b'); // false
```
- The `?` operator affects whatever is immediately before it. For example, in `ab?`, the `?` operators only affects "b", not "a". We say that it _binds tightly_.

```js
/^ab?$/.test('a'); // true

/^(555-)?555-5555$/.test('555-555-5555'); // true
/^(555-)?555-5555$/.test('555-5555'); // true
```