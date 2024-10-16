---
tags:
  - ✅
sr-due: 2024-10-28
sr-interval: 12
sr-ease: 278
---

⬅️ [[NodeJS]]
[🔗 Stack Overflow](https://stackoverflow.com/questions/18875674/whats-the-difference-between-dependencies-devdependencies-and-peerdependencie)

- [`dependencies`](https://github.com/npm/npm/blob/2e3776bf5676bc24fec6239a3420f377fe98acde/doc/files/package.json.md#dependencies) are installed on both:
    - `npm install` from a directory that contains `package.json`
    - `npm install $package` on any other directory
- [`devDependencies`](https://github.com/npm/npm/blob/2e3776bf5676bc24fec6239a3420f377fe98acde/doc/files/package.json.md#devdependencies) are:
    - also installed on `npm install` on a directory that contains `package.json`, unless you pass the `--production` flag, or if the `NODE_ENV=production` environment variable is set
    - not installed on `npm install "$package"` on any other directory, unless you give it the `--dev` option.
    - are not installed transitively.
- [`peerDependencies`](https://github.com/npm/npm/blob/2e3776bf5676bc24fec6239a3420f377fe98acde/doc/files/package.json.md#peerdependencies):
    - before 3.0: are always installed if missing, and raise an error if multiple incompatible versions of the dependency would be used by different dependencies.
    - [expected to start on 3.0](http://blog.npmjs.org/post/110924823920/npm-weekly-5) (untested): give a warning if missing on `npm install`, and you have to solve the dependency yourself manually. When running, if the dependency is missing, you get an error (mentioned by [@nextgentech](https://stackoverflow.com/users/1997767/nextgentech)) This explains it nicely: [https://flaviocopes.com/npm-peer-dependencies/](https://flaviocopes.com/npm-peer-dependencies/)
    - [in version 7](https://github.blog/2021-02-02-npm-7-is-now-generally-available/) peerDependencies are automatically installed unless an upstream dependency conflict is present that cannot be automatically resolved
- Transitivity:
    - `dependencies` are installed transitively: if A requires B, and B requires C, then C gets installed, otherwise, B could not work, and neither would A.
    - `devDependencies` is not installed transitively. E.g. we don't need to test B to test A, so B's testing dependencies can be left out.