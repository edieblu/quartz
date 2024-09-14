---
published: true
tags:
  - ✅
sr-due: 2028-05-10
sr-interval: 1390
sr-ease: 270
---

⬅️ [[Execute Program Advanced TypeScript]]
## Validating data manually
- 💡`typeof null === 'object'` in both JavaScript and TypeScript.

```ts
type Comment = {
  message: string
};

function hasMessageProperty(obj: {}): obj is {message: unknown} {
  return 'message' in obj;
}

function parseCommentJson(json: string): Comment | undefined {
  const parsed: unknown = JSON.parse(json);
  if (typeof parsed === 'object') {
    if (parsed !== null) {
      if (hasMessageProperty(parsed)) {
        if (typeof parsed.message === 'string') {
          return {message: parsed.message};
        }
      }
    }
  }
  return undefined;
}
```
Remember: 
-   The JSON value might not be an object at all.
-   It might be `null`, which is an object in JavaScript but not the kind of object we expect.
-   It might not have the `message` property that we expect.
-   It might have a `message`, but with an unexpected type.

- 💡 We can implement checks with a third-party data validation library like [io-ts](https://github.com/gcanti/io-ts) or [runtypes](https://github.com/pelotom/runtypes).
- 💡 When using `JSON.parse`, it's best to explicitly specify the `unknown` type, like `const parsed: unknown = JSON.parse(json)`.