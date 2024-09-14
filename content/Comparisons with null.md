---
tags:
  - ✅
sr-due: 2027-07-31
sr-interval: 1085
sr-ease: 250
---

⬅️ [[Execute program MySQL]]
## Comparisons with null
- When we use single equal to compare anything with `NULL`, we get another `NULL`. That's even true when comparing `NULL` to itself.
- SQL also has `IS NULL` and `IS NOT NULL` comparisons that properly check for `NULL` values.
```sql
SELECT 5 IS NOT NULL AS result;
--Result:
[{result: 1}]
```
- Usually, you'll see `IS NULL` and `IS NOT NULL` as conditions in `WHERE` queries.
```sql
SELECT * FROM users WHERE email IS NOT NULL
```