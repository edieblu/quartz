---
tags:
  - ✅
sr-due: 2027-09-07
sr-interval: 1226
sr-ease: 270
---

⬅️ [[Execute program MySQL]]

## Defaults

```sql
  CREATE TABLE users (
    name TEXT,
    login_count INTEGER NOT NULL DEFAULT 0
  );
```
- the type (`INTEGER`) in this case always has to come after the column name. The rest of the properties can be ordered freely