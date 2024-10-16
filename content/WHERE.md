---
tags:
  - ✅
sr-due: 2028-04-16
sr-interval: 1289
sr-ease: 250
---

⬅️ [[Execute program MySQL]]

## WHERE
```sql
SELECT * FROM users WHERE name = 'Amir';
SELECT email FROM users WHERE name = 'Amir';
```
- Note that the standard equality operator in SQL is \=
- Most SQL databases support not-equal comparisons with the familiar `!=` operator. Sometimes you'll also see the `<>` operator, as in `a <> b`, which means the same thing.
- `AND` and `OR`
- `length`
```sql
SELECT name FROM users WHERE length(name) > 4
```
- Different database systems provide different functions. SQLite only provides a few functions, but PostgreSQL [provides hundreds](https://www.postgresql.org/docs/12/functions.html). We can also define our own functions, then use them in queries.