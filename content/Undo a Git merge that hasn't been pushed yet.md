---
tags:
  - ✅
sr-due: 2024-11-11
sr-interval: 31
sr-ease: 270
---

⬅️ [[Git]]
- [Stack Overflow](https://stackoverflow.com/questions/2389361/undo-a-git-merge-that-hasnt-been-pushed-yet)

- With `git reflog` check which commit is one prior the merge

Then you can reset it using:

```bash
git reset --hard commit_sha
```

Be aware that any modified and uncommitted/unstashed files will be reset to their unmodified state