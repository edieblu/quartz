---
tags:
  - ✅
sr-due: 2024-10-09
sr-interval: 31
sr-ease: 276
---

⬅️ [[JavaScript]]
- 🔗 [Stack Overflow](https://stackoverflow.com/questions/122102/what-is-the-most-efficient-way-to-deep-clone-an-object-in-javascript)

- `structuredClone(value)`
- The returned value is a [deep copy](https://developer.mozilla.org/en-US/docs/Glossary/Deep_copy) of the original `value`.
- Since March 2022, this feature works across the latest devices and browser versions. This feature might not work in older devices or browsers.

```js
const mushrooms1 = {
  amanita: ["muscaria", "virosa"],
};

const mushrooms2 = structuredClone(mushrooms1);

mushrooms2.amanita.push("pantherina");
mushrooms1.amanita.pop();

console.log(mushrooms2.amanita); // ["muscaria", "virosa", "pantherina"]
console.log(mushrooms1.amanita); // ["muscaria"]

```