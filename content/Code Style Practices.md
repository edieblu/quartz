---
tags:
  - ✅
published: true
sr-due: 2024-12-20
sr-interval: 186
sr-ease: 260
---

⬅️ [[NodeJS Best Practice]]
🔗 [GH](https://github.com/goldbergyoni/nodebestpractices?tab=readme-ov-file#3-code-patterns-and-style-practices)

- Use ESLint 
	- use **`eslint-config-prettier`** for eslint/prettier config
- Use Node.js eslint extension plugins
- Name your functions
- Naming conventions: Use **_lowerCamelCase_** when naming constants, variables and functions, **_UpperCamelCase_** (capital first letter as well) when naming classes and **_UPPER_SNAKE_CASE_** when naming global or static variables
-  Prefer const over let. Ditch the var
- Require modules at the beginning of each file, before and outside of any functions.
- Avoid effects outside of functions: Avoid putting code with effects like network or DB calls outside of functions