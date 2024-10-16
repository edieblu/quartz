---
tags:
  - ✅
sr-due: 2024-11-07
sr-interval: 54
sr-ease: 296
---

⬅️ [[JavaScript]]
🔗 [Stack Overflow](https://stackoverflow.com/questions/20035101/why-does-my-javascript-code-receive-a-no-access-control-allow-origin-header-i)

The browser is blocking it as it usually allows a request in the same origin for security reasons. You need to do something different when you want to do a cross-domain request.

When you are using Postman they are not restricted by this policy. Quoted from _[Cross-Origin XMLHttpRequest](https://developer.chrome.com/docs/extensions/mv2/xhr/)_:

> Regular web pages can use the XMLHttpRequest object to send and receive data from remote servers, but they're limited by the same origin policy. Extensions aren't so limited. An extension can talk to remote servers outside of its origin, as long as it first requests cross-origin permissions.