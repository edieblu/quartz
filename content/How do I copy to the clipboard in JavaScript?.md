---
tags:
  - ✅
sr-due: 2024-11-19
sr-interval: 44
sr-ease: 296
---

⬅️ [[JavaScript]]
- 🔗 [Stack Overflow](https://stackoverflow.com/questions/400212/how-do-i-copy-to-the-clipboard-in-javascript)

 [Async Clipboard API](https://www.w3.org/TR/clipboard-apis/#async-clipboard-api) `[navigator.clipboard.writeText]`
- Text can be copied to the clipboard directly from a variable.
- Only supported on pages served over HTTPS.
- In Chrome 66 pages inactive tabs can write to the clipboard without a permissions prompt.

```javascript
var text = "Example text to appear on clipboard";
navigator.clipboard.writeText(text).then(function() {
  console.log('Async: Copying to clipboard was successful!');
}, function(err) {
  console.error('Async: Could not copy text: ', err);
});
```