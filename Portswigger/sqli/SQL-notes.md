# TOPIC 1: DATABASE BASICS
1. DBMS: The engine itself, it stores, manages, organizes and retrive data.
2. Database: A container holding related tables. A webapp has usually 1 database
3. Tables: It is like a spreadsheet, fixed column and unlimited rows
4. Row(Record): One entry. One row = one user, one order, one comment
5. Column(Field): One attribute shared by every row.
6. Primary Key — a column that uniquely identifies each row (usually id, auto-incrementing). No two rows share one. Attackers target primary keys constantly — WHERE id=1, WHERE id=2, etc. — to pull specific records one at a time.
7. Foreign Key — a column in one table pointing to the primary key of another, linking them. Example: orders.user_id points to users.id. This relationship is the entire basis of JOINs (topic 16), which matter a lot once you're chaining SQLi across tables.
8. NULL — means "no value" — not zero, not an empty string. You'll see IS NULL / IS NOT NULL used in injection filtering to test column counts and structure.
9. Data Types — every column has a type restricting what it stores:
INT — whole numbers
VARCHAR(n) — variable-length text, max n chars
TEXT — long text
DATE / DATETIME — dates
BOOLEAN — true/false

# TOPIC 2: SELECT
**Most important command!**

Syntax: SELECT column_name FROM table_name;
* -> Everything

e.g., SELECT * FROM users;

**SELECT DISTINCT**
Removes duplicate values from the result.

SELECT DISTINCT country FROM users;

If 500 users are from India, this returns "India" once instead of 500 times. Useful for recon — e.g. figuring out how many unique roles exist in a users table.

**SELECT AS**
Renames a column in the output only — doesn't touch the actual table.
e.g., SELECT username AS user_name FROM users;

# TOPIC 3: WHERE
**WHERE** filters row instead of giving every row in the output it give the row which matches the condition in **WHERE** query. It makes the data less clutter.

Comparison Operators

=      -- equal to
!=     -- not equal to
<>     -- not equal to (same as !=, ANSI standard)
>      -- greater than
<      -- less than
>=     -- greater than or equal
<=     -- less than or equal

e.g., 
MariaDB [lab]> SELECT * FROM users WHERE username = 'admin';
+----+----------+----------+----------------+---------+
| id | username | password | email          | country |
+----+----------+----------+----------------+---------+
|  1 | admin    | admin123 | admin@site.com | USA     |
+----+----------+----------+----------------+---------+
1 row in set (0.016 sec)

**Logical Operators**
1. LIKE: Pattern matching with wildcard, % = any number of characters, _ = exactly 1 character.
e.g., SELECT * FROM users WHERE username = 's%';
2. IN: Matches any value in the list.
e.g., SELECT * FROM users WHERE username = '_ohn';
3. BETWEEN: Range check (inclusive).
e.g., SELECT * FROM users WHERE id BETWEEN 1 AND 3;
4. IS NULL/IS NOT NULL: Checking NULL specifically, Note '= NULL' never works in sql you have to use 'IS NULL'.
e.g., SELECT * FROM users WHERE email IS NOT NULL;

# TOPIC 4: ORDER BY
It sorts the result. On its own it doesn't filter anything - it just changes the order row and comes backs in.
Syntax: SELECT * FROM users ORDER BY column_name; By default is orders in ascending order.

ASC and DESC
ASC: ascending (A->Z)(0->9) this is default you rarely need to type this. SELECT * FROM users ORDER BY username ASC;
DESC: descending (Z->A)(9->0) SELECT * FROM users ORDER BY username DESC;

**SORTING USING COLUMN POSITION** 
You can also sort by column position instead of name: SELECT username, country FROM users ORDER BY 2;
This sorts by the 2nd column in your SELECT list (country), without naming it. This looks like a small syntax trick, but it's actually critical for SQL injection.

# TOPIC 5: LIMIT
Limit restricts how many rows come back. Instead of getting all matching rows, you cap the result at fixed numbers
Syntax: SELECT * FROM tablename LIMIT number;
**LIMIT WITH OFFSET** - SELECT * FROM users LIMIT 2 OFFSET 1;
OFFSET says "Skip the 1st row and return the next 2 row"
Short hand syntax: SELECT * FROM users LIMIT 1,2;

# TOPIC 6: AGGREGATE FUNTIONS
Aggregate Functions don't return individual rows - they calculate single summary value across many rows. Instead of "Show me data" you are saying "Give me something about the data as a whole"
1. COUNT(): SELECT COUNT(*) FROM users; - returns the total number of rows in the table.
2. SUM(): SELECT SUM(id) FROM users; - Add all ids together. Not something you'll usually use on username, password tables but critical in real apps. e.g., summing order tables, transaction amounts.
3. AVG(): SELECT AVG(id) FROM users; Averages the numberic column.
4. MIN() and MAX(): SELECT MIN(id) FROM users; SELECT MAX(id) FROM users; Select smallest and largest value in the column. Works on text too - MySQL will find the alphabetically first/last value.

# TOPIC 7: GROUP BY
GROUP BY clutters rows that share the same value in a column, So you can run an aggregate function per group instead of across the whole table.
e.g., SELECT country, COUNT(*) FROM users GROUP BY country;

**GROUP_CONCAT** merges all values in a group into one comma-separated string.
SELECT country, GROUP_CONCAT(username) FROM users GROUP BY country;

# TOPIC 8: HAVING
Having filters after grouping - it's like WHERE but for aggregate results instead of raw rows.
WHERE: Filters row before grouping happens
HAVING: Filters row after aggregation happens
HANDS ON:
SELECT country, COUNT(*) FROM users GROUP BY country HAVING COUNT(*) > 1;
SELECT country, COUNT(*) FROM users GROUP BY country HAVING COUNT(*) = 1;

# TOPIC 9: INSERT
Adds new row to the table.
Syntax: INSERT INTO tablename (columnn1, column2...) VALUES (value1, value2...);

**SQLi relevance**
Low, for the same reason as CREATE TABLE — you're not inserting data into someone else's live application database as an attacker (well, in blind cases you technically could via a stored/second-order XSS-adjacent injection, but that's an edge case, not core SQLi). The main value here is being able to build realistic practice data for yourself, which you're already doing.

One place INSERT-style injection does matter: stored/second-order SQLi, where user input (like a comment or profile bio) gets stored unsanitized via an app's own INSERT statement, and the malicious payload only executes later when that stored data gets pulled into a different, vulnerable SELECT query. Worth knowing the term now — you'll hit it properly later in your roadmap.

# TOPIC 10: UPDATE
Modifies existing row.
Syntax: UPDATE table_name SET column = new_value WHERE condition;

**SQLi relevance**

Low as something you'll write against a target — but understanding UPDATE matters for a specific class of real vulnerabilities: apps that build UPDATE queries from user input unsafely (e.g. a "change my email" form) are just as injectable as SELECT-based ones. The injection mechanics (breaking out of a string with ', using comments) are identical — only the query type differs.

# TOPIC 11: DELETE
Removes rows.
Syntax: DELETE FROM table_name WHERE condition;

Same warning as UPDATE — even more destructive

DELETE FROM users;

No WHERE = every row in the table gone. Unlike UPDATE, there's no "wrong value" to fix afterward — the data is just gone (unless you have a backup). Always run a SELECT with the same WHERE clause first to confirm exactly which rows you're about to hit, before running the DELETE.

SELECT * FROM users WHERE country = 'France'; --check first
DELETE FROM users WHERE country = 'France'; --then delete
