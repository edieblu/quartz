---
tags:
  - ✅
sr-due: 2024-10-17
sr-interval: 34
sr-ease: 272
---

⬅️ [[Web Development]]
🔗 [Stack Overflow](https://stackoverflow.com/questions/105034/how-do-i-create-a-guid-uuid)

- UUIDs (Universally Unique IDentifier), also known as GUIDs (Globally Unique IDentifier), according to [RFC 4122](https://www.ietf.org/rfc/rfc4122.txt), are identifiers designed to provide certain uniqueness guarantees.

- UUIDS, are **128 bit numbers**, composed of 16 octets and represented as 32 base-16 characters, that can be used to identify information across a computer system

- It's a **36-character** alphanumeric string that can be used to identify information

- [`crypto.randomUUID()`](https://developer.mozilla.org/en-US/docs/Web/API/Crypto/randomUUID) is now standard on all modern browsers and JS runtimes. However, because [new browser APIs are restricted to secure contexts](https://blog.mozilla.org/security/2018/01/15/secure-contexts-everywhere/), this method is only available to pages served locally (`localhost` or `127.0.0.1`) or over HTTPS.
- for generating UUIDs on legacy platforms or in non-secure contexts, there is [the `uuid` module](https://www.npmjs.com/package/uuid). It is well-tested and supported.

If everything else fails, then use this one
```js
function uuidv4() {
  return "10000000-1000-4000-8000-100000000000".replace(/[018]/g, c =>
    (+c ^ crypto.getRandomValues(new Uint8Array(1))[0] & 15 >> +c / 4).toString(16)
  );
}

console.log(uuidv4());
```
Note: solutions based on `Math.random()` do not provide good uniqueness guarantees.

## Uuid Format
- UUIDs must be of the form "`xxxxxxxx-xxxx-Mxxx-Nxxx-xxxxxxxxxxxx`", where x is one of [0-9, a-f] _M_ is one of [1-5], and _N_ is [8, 9, a, or b]