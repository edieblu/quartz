---
tags:
  - ✅
published: true
sr-due: 2024-10-14
sr-interval: 41
sr-ease: 276
---

⬅️ [[JavaScript]]

🔗 [stack overflow](https://stackoverflow.com/questions/1335851/what-does-use-strict-do-in-javascript-and-what-is-the-reasoning-behind-it)

- Inside native ECMAScript modules (with import and export statements) and ES6 classes, strict mode is always enabled and cannot be disabled.

Strict mode helps out in a couple ways:

- It catches some common coding bloopers, throwing exceptions.
- it prevents, or throws errors, when relatively "unsafe" actions are taken (such as gaining access to the global object).
- it disables features that are confusing or poorly thought out.
- you can apply "strict mode" to the whole file... Or you can use it only for a specific function

## Resources
- https://johnresig.com/blog/ecmascript-5-strict-mode-json-and-more/