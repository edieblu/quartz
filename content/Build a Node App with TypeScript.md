---
tags:
  - ✅
sr-due: 2024-10-24
sr-interval: 47
sr-ease: 290
---

⬅️ [[TypeScript]]

🔗 https://www.totaltypescript.com/typescript-and-node

we will need a few things:

- A `dev` script to run our code locally and check for TypeScript errors.
- A `build` script to bundle our code for production and check for TypeScript errors.
- A `start` script to run our bundled code in production.

1. `npm init -y`
2. add `"type": "module"` to the `package.json` file. (This tells Node.js to use ES Modules instead of CommonJS modules.)
```json
{
  // ...other properties
  "type": "module"
  // ...other properties
}
```
3.  install `pnpm` and add dependencies
```bash
pnpm add -D typescript @types/node
```
4. add `tsconfig.json` (explanation [here](https://www.totaltypescript.com/tsconfig-cheat-sheet))
```json
{
  "compilerOptions": {
    /* Base Options: */
    "esModuleInterop": true,
    "skipLibCheck": true,
    "target": "es2022",
    "allowJs": true,
    "resolveJsonModule": true,
    "moduleDetection": "force",
    "isolatedModules": true,
    /* Strictness */
    "strict": true,
    "noUncheckedIndexedAccess": true,
    /* If transpiling with TypeScript: */
    "moduleResolution": "NodeNext",
    "module": "NodeNext",
    "outDir": "dist",
    "sourceMap": true,
    /* If your code doesn't run in the DOM: */
    "lib": ["es2022"]
  }
}
```

5. add `.gitignore`
```
node_modules
dist
```

6. create `src/index.ts`
7. `build` script
```json
{
  // ...other properties
  "scripts": {
    "build": "tsc" // turns ts code into JavaScript using `tsc`, and also checks for any errors.
  }
  // ...other properties
}
```
8. `start` script
```json
{
  // ...other properties
  "scripts": {
    "start": "node dist/index.js"
  }
  // ...other properties
}
```
Running `pnpm build && pnpm start` will build our code and then run it.

9. `dev` script
- `tsc --watch` to bundle our TypeScript code and check for errors.
- `node --watch` to re-run our application when it changes.
```json
{
  // ...other properties
  "scripts": {
    "dev:tsc": "tsc --watch --preserveWatchOutput" // The `--preserveWatchOutput` flag tells TypeScript not to clear the console output when it re-runs.
  }
  // ...other properties
}
```

```json
{
  // ...other properties
  "scripts": {
    "dev:node": "node --enable-source-maps --watch dist/index.js"
  }
  // ...other properties
}
```

`--enable-source-maps` means that error stack traces will point to your TypeScript files instead of your JavaScript files. This is possible because of the `"sourceMap": true` in our `tsconfig.json`.

```json
{
  // ...other properties
  "scripts": {
    "dev": "pnpm run \"/dev:/\""
  }
  // ...other properties
}
```

This script runs all the scripts that start with `dev:` in parallel.

[Example on GitHub](https://github.com/mattpocock/typescript-node)