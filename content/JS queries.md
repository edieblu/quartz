---
tags:
  - ✅
published: true
sr-due: 2024-11-19
sr-interval: 545
sr-ease: 250
---
⬅️ [[Execute program MySQL]]

## JS queries
```js
const users = exec(`SELECT name FROM users WHERE id = ?`, [1]);
const amir = users[0];
amir.name;

function findUser(id) {
  return exec(`SELECT * FROM users WHERE id = ?`, [id]);
}

function findUser(id) {
  const queryResult = exec(`SELECT id, name FROM users WHERE id = ?`, [id])
  if (!queryResult.length) return null
  return queryResult[0]
}
```
- If we have two `?` parameters in our query, we have to provide two values to fill those parameters.
- With `SELECT ... ?`, [1, 2]), the `1` and `2` are called "bind parameters". The query contains some holes marked with `?`, and the parameters get bound to those holes.
- We can reference a specific bind parameter `?1`, `?2` (parameter numbers start at 1, so `?1` refers to the bind parameter at index 0)
```sql
SELECT name FROM cats WHERE name = ?1 AND owner_name = ?1`, ['Wilford']
```
- (The syntax for these parameters varies by database. For example, PostgreSQL's bind parameters are referenced with `$1`, `$2`, etc.)