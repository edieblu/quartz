---
tags:
  - ✅
published: true
sr-due: 2027-02-09
sr-interval: 950
sr-ease: 250
---
⬅️ [[Execute program MySQL]]

## Start a new db
```sql
CREATE TABLE users (email TEXT, name TEXT);
INSERT INTO users (email, name) VALUES ('amir@example.com', 'Amir');
SELECT * FROM users;
```
- Executing a `SELECT` always returns an array of objects.
- For consistency, all SQL statements return arrays. Statements like `CREATE`, `INSERT` that don't retrieve data will return `[]`, an empty array of rows.

- 💡 A table can have as many columns as we like. (Within reason: SQLite allows [up to 2,000 columns](https://www.sqlite.org/limits.html) by default, but can be configured to allow as many as 32,767.)
- 💡 SQL keywords like `INSERT` and `SELECT` ignore case, so `INSERT` and `InSeRt` mean the same thing. Table and column names also ignore case, so `users` and `USErs` refer to the same table
- SQL does respect case within strings. `'a'` and `'A'` are different strings that are not equal.