---
tags:
  - ✅
published: true
sr-due: 2024-09-17
sr-interval: 88
sr-ease: 270
---
⬅️ [[JavaScript]]
⬅️ [[Pointer]]

from: https://www.pointer.io/tags/javascript

## JavaScript Bloat in 2024
🔗 [here](https://tonsky.me/blog/js-bloat/)
tldr: 10MB  of JavaScript is not a lot? 🤷‍♂️

## Writing Javascript without a build system
🔗 [here](https://jvns.ca/blog/2023/02/16/writing-javascript-without-a-build-system/)

Build systems can do lots of useful things, like:
- combining 100s of JS files into one big bundle (for efficiency reasons)
- translating Typescript into Javascript
- typechecking Typescript
- minification
- adding polyfills to support older browsers
- compiling JSX
- treeshaking (remove unused JS code to reduce file sizes)
- building CSS (like [tailwind](https://tailwindcss.com/) does)
- and probably lots of other important things

Examples of build systems:
- webpack, rollup, esbuild, parcel, or vite

[A virtual DOM in 200 lines of JavaScript](https://lazamar.github.io/virtual-dom/)
- The goal of a virtual DOM: It’s not about performance. A Virtual DOM is an abstraction to simplify the act of modifying a UI.

1. _Create_ a virtual representation of the DOM
2. _Diff_ virtual DOM nodes
3. _Apply_ a virtual DOM diff to an HTML element