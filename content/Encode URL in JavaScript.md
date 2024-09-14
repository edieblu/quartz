---
tags:
  - ✅
sr-due: 2024-10-12
sr-interval: 46
sr-ease: 296
---

⬅️ [[JavaScript]]
🔗 [Stack  Overflow](https://stackoverflow.com/questions/332872/encode-url-in-javascript)

Three options:
- `escape()` will not encode: `@*/+`
- `encodeURI()` will not encode: `~!@#$&*()=:/,;?+'`
- `encodeURIComponent()` will not encode: `~!*()'`

`escape` is implemented differently in different browsers?

## Modern

There's also [URLSearchParams](https://developer.mozilla.org/en-US/docs/Web/API/URLSearchParams/URLSearchParams) and [`URL()` interface](https://developer.mozilla.org/en-US/docs/Web/API/URL)