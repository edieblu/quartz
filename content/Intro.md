---
tags:
  - ✅
sr-due: 2027-07-15
sr-interval: 1073
sr-ease: 250
---

⬅️ [[FEM TypeScript Fundamentals]]
## Intro

**What is typescript?**
- TypeScript is an open source (maintained by MS), typed syntactic superset of JavaScript (i.e. it has all of JavaScript's syntax, plus some new syntax as well.)
- Compiles to readable JS
- Three parts: Language, Language Server (what powers autocompletes inside VSCode) and Compiler
- Kind of like a fancy linter

**Why types?**
- It allows you, as a code author, to leave more of your intent “on the page”
- It has the potential to move some kinds of errors from runtime (where they would affect users) to compile time

💡 When the compiler accepts a program's types, we say that that program type checks.
💡 The compiler forces us to use types correctly. If we use them incorrectly, it's a type error and the program won't compile.
💡 Every variable has a type. Every value we assign must match the variable's type.

Each TypeScript program is a valid JavaScript program, but with extra annotations: the types. After checking types, the TypeScript compiler generates JavaScript by removing all TypeScript-specific syntax from a program. Then, the result is run as JavaScript.

This means that there's no way to inspect types at runtime. Types are only used during type checking, then they're thrown away (aka type erasure).

In JavaScript, any code with valid syntax will run. In TypeScript, code must have valid syntax and must type check. Only then will it run.

JavaScript: syntax check -> execution.
TypeScript: syntax check -> type check -> execution.


Examples:
	- Values that are potentially absent (null or undefined)
	- Incomplete refactoring
	- Breakage around internal code contracts (e.g., an argument becomes required)

- It serves as the foundation for a great code authoring experience (i.e. in-editor autocomplete)