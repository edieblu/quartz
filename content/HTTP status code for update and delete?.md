---
tags:
  - ✅
sr-due: 2024-11-04
sr-interval: 37
sr-ease: 272
---

⬅️ [[Web Development]]
🔗 [Stack Overflow](https://stackoverflow.com/questions/2342579/http-status-code-for-update-and-delete)

For a **PUT** request: **HTTP 200**, **HTTP 204** should imply "resource updated successfully". **HTTP 201** if the **PUT** request created a new resource.

For a **DELETE** request: **HTTP 200** or **HTTP 204** should imply "resource deleted successfully".

**HTTP 202** can also be returned by either operation and would imply that the instruction was accepted by the server, but not fully applied yet. It's possible that the operation fails later, so the client shouldn't fully assume that it was success.

A client that receives a status code it doesn't recognize, but it's starting with 2 should treat it as a 200 OK.