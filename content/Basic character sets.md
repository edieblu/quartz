---
tags:
  - ✅
sr-due: 2026-05-12
sr-interval: 622
sr-ease: 250
---

⬅️ [[Execute Program RegEx]]
## Basic character sets
```js
[aou] // same as
(a|o|u)
```

- That was shorter, but still wordy. We can specify an entire range of characters by using `-`.
```js
/[a-z]/.test('g');
```

- Character sets can be _negated_ to mean "everything not in the set". (`^`)
- Normally it means "beginning of line". But inside `[]`, it means "negate the character set".
```js
/[^a]/.test('a'); // false

/[^ab]/.test('a'); // any char that isn't a or b

/[^a-z]/.test('h'); // false
```

- Character sets match exactly one character in the string (use `*` pr `+` for more)