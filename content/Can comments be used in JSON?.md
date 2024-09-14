---
published: true
tags:
  - ✅
sr-due: 2024-09-28
sr-interval: 28
sr-ease: 270
---

⬅️ [[JSON]]
🔗 [Stack Overflow](https://stackoverflow.com/questions/244777/can-comments-be-used-in-json)

No. JSON is data-only. If you include a comment, then it must be data too.

A hack!

```json
{
  "api_host" : "The hostname of your API server. You may also specify the port.",
  "api_host" : "hodorhodor.com",

  "retry_interval" : "The interval in seconds between retrying failed API calls",
  "retry_interval" : 10,

  "auth_token" : "The authentication token. It is available in your developer dashboard under 'Settings'",
  "auth_token" : "5ad0eb93697215bc0d48a7b69aa6fb8b",

  "favorite_numbers": "An array containing my all-time favorite numbers",
  "favorite_numbers": [19, 13, 53]
}
```

The above code is [valid JSON](http://jsonlint.com/). If you parse it, you'll get an object like this:

```json
{
    "api_host": "hodorhodor.com",
    "retry_interval": 10,
    "auth_token": "5ad0eb93697215bc0d48a7b69aa6fb8b",
    "favorite_numbers": [19,13,53]
}
```