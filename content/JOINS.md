---
tags:
  - ✅
published: true
sr-due: 2025-09-25
sr-interval: 490
sr-ease: 250
---
⬅️ [[Execute program MySQL]]
## JOINS
- aka `INNER JOIN`
- `ON` is like `WHERE`, but it applies specifically to joins
```sql
SELECT * FROM people JOIN cats ON people.id = cats.owner_id

SELECT name AS cat, first_name AS person FROM people JOIN cats ON people.id = cats.owner_id
```

It's always correct to think about basic `JOIN`s as two nested loops with a filter, like this:
- For each person in the people table:
	-   For each cat in the cats table:
    	-   If the `ON` condition is true for this person and this cat:
        	-   Return a row with the columns from this person and this cat.

- It's common for tables to have the same column names, especially for `id` columns. This can get very confusing, so it's best to use `AS` to explicitly alias every joined column, rather than blindly selecting `*`. That will make your SQL code more clear to other programmers.
```sql
 SELECT
    cats.id AS cat_id,
    people.id AS person_id
  FROM people JOIN cats ON people.id = cats.owner_id
  
  
  SELECT people.first_name AS person, cats.name AS cat
  FROM people
  JOIN cats
    ON people.id = cats.owner_id
  WHERE people.first_name = 'Amir'
 ```
 
 ### Performance
 - Nested loops are a perfect mental model for how `JOIN` works, but they're only a mental model. In reality, the database will optimize the query, rebuilding it to be more efficient while still giving the same results.