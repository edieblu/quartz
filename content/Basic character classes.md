---
tags:
  - ✅
published: true
sr-due: 2027-12-03
sr-interval: 1280
sr-ease: 270
---

⬅️ [[Execute Program RegEx]]

## Basic character classes
- `\d` for digits
- `\s` for whitespace (spaces, newlines, tabs, etc.)
- Making these character classes upper-case negates them. For example, `\d` is all digits. But `\D` is any character that isn't a digit.
```js
/^\d*$/.test('3000')
var re = /^\d\d\d-\d\d\d\d$/;
```