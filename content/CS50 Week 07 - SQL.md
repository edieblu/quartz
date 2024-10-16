---
tags:
  - ✅
sr-due: 2028-08-04
sr-interval: 1446
sr-ease: 250
---

⬅️ [[CS50]]
⬅️ [[SQL]]

- 🔗 [Course Website](https://cs50.harvard.edu/x/2021/weeks/7/)

## CSV
- a `.csv` is a flat-file database
- the data for each column is separated by commas, and each row is on a new line, saved simply as a file
- very portable; good for sorting; bad for searching
- if you use `with open` for opening files in `python`, it will handle the eventual closing of the file as well. So essentially, the file will remain open while you are indented inside the `with` block.
- the `DictReader` presumes that the first row is going to be column headings (if your file doesn't have headers, you'll have to manually configure `DictReader`)

**🤔 What does to canonicalize mean?**
- to canonicalize means to format your data in some standard way

```python
# how to print only unique values
import csv

# a colection of unique values
titles = set()

with open("Favorite TV Shows - Form Responses 1.csv", "r") as file:
    reader = csv.DictReader(file)

    for row in reader:
		# the dict reader is aware of the column names
		# trim and uppercase the entries
        titles.add(row["title"].strip().upper())

# let's sort as well
for title in sorted(titles):
    print(title)

```

This is how you'd define a dictionary:
```python
titles = dict()
#or
titles = {}

	# dict vote counter
    for row in reader:
        title = row["title"].strip().upper()
        if title not in titles:
            titles[title] = 0
        titles[title] += 1
```

And this is how you'd sort by dict value (not key):
```python
def f(title):
    return titles[title]

# 🤯 you can pass in functions to sorted
for title in sorted(titles, key=f, reverse=True):
	
# for short (anonymous) functions, you can write them inline like this:
# lambda arguments: return value
for title in sorted(titles, key=lambda title: titles[title], reverse=True):

```

## Relational database
-  programs that store data, ultimately in files, but with additional data structures that allow us to search and store data more efficiently.
- SQLite is a lightweight version of it (very much used on mobile apps)
- instead of `.csv`, the data is now stored in a binary file
- inside the file live the tables (aka sheets inside a spreadsheet)
- `sqlite3` command-line tool for interacting with the db
- you can import a `.csv` file into `sqilite3`
![[Pasted image 20211216111749.png]]

## SQL
When working with data, you generally deal with these four actions:
- `CREATE` and `INSERT`
- `SELECT` (aka `READ` in the `CRUD` world)
- `UPDATE`
- `DELETE`

For example:
- `SELECT title FROM shows;`
- `SELECT * FROM shows;` (selects all columns)

SQL supports many functions that we can use to count and summarize data:
-   `AVG`
-   `COUNT`
-   `DISTINCT`, for getting distinct values without duplicates
-   `LOWER`
-   `MAX`
-   `MIN`
-   `UPPER`
-   …

You can also add  **clauses**, or phrases that modify the query:
-   `WHERE`, matching results on a strict condition
-   `LIKE`, matching results on a less strict condition
-   `ORDER BY`, ordering results in some way
-   `LIMIT`, limiting the number of results
-   `GROUP BY`, grouping results in some way
-    …

Example queries:
- `sqlite> SELECT title FROM shows WHERE title LIKE "%Office%";` (`%` is a wildcard)
- `sqlite> SELECT DISTINCT(UPPER(title)) FROM shows ORDER BY UPPER(title);`
- `SELECT UPPER(title), COUNT(title) FROM shows GROUP BY UPPER(title) ORDER BY COUNT(title);`

🤔 What does it mean to normalize data?
- To reduce redundancy and ensure a single source of truth.

### Data Types
-   `BLOB`, for “binary large object”, raw binary data that might represent files
-   `INTEGER`
-   `NUMERIC`, number-like but not quite a number, like a date or time
-   `REAL`, for floating-point values
-   `TEXT`, like strings

### Attributes
-   `NOT NULL`, there must be some value
-   `UNIQUE`, means that the value for that column must be unique for every row in the table
-   `PRIMARY KEY`, like the `id` column above that will be used to uniquely identify each row
-   `FOREIGN KEY`, like the `show_id` column above that refers to a column in some other table

Back in our Python file, this is how you can create a squlite db programmatically:

```python
from cs50 import SQL

open("shows.db", "w").close()
db = SQL("sqlite:///shows.db")

db.execute("CREATE TABLE shows (id INTEGER, title TEXT, PRIMARY KEY(id))")
db.execute("CREATE TABLE genres (show_id INTEGER, genre TEXT, FOREIGN KEY(show_id) REFERENCES shows(id))")


with open("Favorite TV Shows - Form Responses 1.csv", "r") as file:
    reader = csv.DictReader(file)
    for row in reader:
        title = row["title"].strip().upper()
		
		# saving the id to use it as FOREIGN KEY in a bit
		# using the ? as a placeholder
        id = db.execute("INSERT INTO shows (title) VALUES(?)", title)

        for genre in row["genres"].split(", "):
            db.execute("INSERT INTO genres (show_id, genre) VALUES(?, ?)", id, genre)
```

More queries:
- `SELECT title FROM shows WHERE id IN (SELECT show_id FROM genres WHERE genre = "Musical");`

### Data Types in MySQL
-   `INTEGER`
    -   `smallint`, with fewer bits
    -   `integer`
    -   `bigint`, with more bits
-   `NUMERIC`
    -   `boolean`
    -   `date`
    -   `datetime`
    -   `numeric(scale,precision)`, with a fixed number of digits
    -   `time`
    -   `timestamp`
-   `REAL`
    -   `real`
    -   `double precision`, with twice as many bits
-   `TEXT`
    -   `char(n)`, a fixed number of characters
    -   `varchar(n)`, a variable number of characters, up to some limit `n`
    -   `text`, a string with no limit

Imdb schema design
![[Pasted image 20211217073452.png]]

### Indexes
- indexes tell our database program to create additional data structures so we can search and sort with logarithmic time (instead of `O(n)`): `sqlite> CREATE INDEX title_index ON shows (title);`
- this creates  `B-trees`, like binary trees in C, with nodes organized such that we can search faster than linearly
- A `B-tree` is a family tree that is very wide and not that tall (aka it tries to keep the leaf nodes as close to the root as possible)

### `JOIN`
```sql
SELECT title FROM people
JOIN stars ON people.id = stars.person_id
JOIN shows ON stars.show_id = shows.id
WHERE name = "Steve Carell";
```

## Problems
- **SQL injection attacks**: possible in any application that takes in a user input (e.g., Bobby Tables)
- **race conditions:** code in a multi-threaded environment can be commingled or mixed in each thread (e.g., Instagram egg with 50 million likes). The solution is to use `TRANSACTIONS` which lock a specific row in a table to only one update at a time.