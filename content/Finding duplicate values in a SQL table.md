---
tags:
  - ✅
sr-due: 2024-10-02
sr-interval: 32
sr-ease: 270
---

⬅️ [[SQL]]
🔗 [Stack Overflow](https://stackoverflow.com/questions/2594829/finding-duplicate-values-in-a-sql-table)

It's easy to find duplicates with one field:

```sql
SELECT email, COUNT(email) 
FROM users
GROUP BY email
HAVING COUNT(email) > 1
```

How do you get duplicates with the same `email` **and** `name`?
```sql
SELECT
    name, email, COUNT(*)
FROM
    users
GROUP BY
    name, email
HAVING 
    COUNT(*) > 1
```