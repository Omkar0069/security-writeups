## TOPIC 1: DATABASE BASICS
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

## TOPIC 2: SELECT
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

## TOPIC 3: WHERE
**WHERE** filters row instead of giving every row in the output it give the row which matches the condition in **WHERE** query. It makes the data less clutter.

Comparison Operators
```
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
```
**Logical Operators**
1. LIKE: Pattern matching with wildcard, % = any number of characters, _ = exactly 1 character.
e.g., SELECT * FROM users WHERE username = 's%';
2. IN: Matches any value in the list.
e.g., SELECT * FROM users WHERE username = '_ohn';
3. BETWEEN: Range check (inclusive).
e.g., SELECT * FROM users WHERE id BETWEEN 1 AND 3;
4. IS NULL/IS NOT NULL: Checking NULL specifically, Note '= NULL' never works in sql you have to use 'IS NULL'.
e.g., SELECT * FROM users WHERE email IS NOT NULL;

## TOPIC 4: ORDER BY
It sorts the result. On its own it doesn't filter anything - it just changes the order row and comes backs in.
Syntax: SELECT * FROM users ORDER BY column_name; By default is orders in ascending order.

ASC and DESC
ASC: ascending (A->Z)(0->9) this is default you rarely need to type this. SELECT * FROM users ORDER BY username ASC;
DESC: descending (Z->A)(9->0) SELECT * FROM users ORDER BY username DESC;

**SORTING USING COLUMN POSITION** 
You can also sort by column position instead of name: SELECT username, country FROM users ORDER BY 2;
This sorts by the 2nd column in your SELECT list (country), without naming it. This looks like a small syntax trick, but it's actually critical for SQL injection.

## TOPIC 5: LIMIT
Limit restricts how many rows come back. Instead of getting all matching rows, you cap the result at fixed numbers
Syntax: SELECT * FROM tablename LIMIT number;
**LIMIT WITH OFFSET** - SELECT * FROM users LIMIT 2 OFFSET 1;
OFFSET says "Skip the 1st row and return the next 2 row"
Short hand syntax: SELECT * FROM users LIMIT 1,2;

## TOPIC 6: AGGREGATE FUNTIONS
Aggregate Functions don't return individual rows - they calculate single summary value across many rows. Instead of "Show me data" you are saying "Give me something about the data as a whole"
1. COUNT(): SELECT COUNT(*) FROM users; - returns the total number of rows in the table.
2. SUM(): SELECT SUM(id) FROM users; - Add all ids together. Not something you'll usually use on username, password tables but critical in real apps. e.g., summing order tables, transaction amounts.
3. AVG(): SELECT AVG(id) FROM users; Averages the numberic column.
4. MIN() and MAX(): SELECT MIN(id) FROM users; SELECT MAX(id) FROM users; Select smallest and largest value in the column. Works on text too - MySQL will find the alphabetically first/last value.

## TOPIC 7: GROUP BY
GROUP BY clutters rows that share the same value in a column, So you can run an aggregate function per group instead of across the whole table.
e.g., SELECT country, COUNT(*) FROM users GROUP BY country;

**GROUP_CONCAT** merges all values in a group into one comma-separated string.
SELECT country, GROUP_CONCAT(username) FROM users GROUP BY country;

## TOPIC 8: HAVING
Having filters after grouping - it's like WHERE but for aggregate results instead of raw rows.
WHERE: Filters row before grouping happens
HAVING: Filters row after aggregation happens
HANDS ON:
SELECT country, COUNT(*) FROM users GROUP BY country HAVING COUNT(*) > 1;
SELECT country, COUNT(*) FROM users GROUP BY country HAVING COUNT(*) = 1;

## TOPIC 9: INSERT
Adds new row to the table.
Syntax: INSERT INTO tablename (columnn1, column2...) VALUES (value1, value2...);

**SQLi relevance**
Low, for the same reason as CREATE TABLE — you're not inserting data into someone else's live application database as an attacker (well, in blind cases you technically could via a stored/second-order XSS-adjacent injection, but that's an edge case, not core SQLi). The main value here is being able to build realistic practice data for yourself, which you're already doing.

One place INSERT-style injection does matter: stored/second-order SQLi, where user input (like a comment or profile bio) gets stored unsanitized via an app's own INSERT statement, and the malicious payload only executes later when that stored data gets pulled into a different, vulnerable SELECT query. Worth knowing the term now — you'll hit it properly later in your roadmap.

## TOPIC 10: UPDATE
Modifies existing row.
Syntax: UPDATE table_name SET column = new_value WHERE condition;

**SQLi relevance**

Low as something you'll write against a target — but understanding UPDATE matters for a specific class of real vulnerabilities: apps that build UPDATE queries from user input unsafely (e.g. a "change my email" form) are just as injectable as SELECT-based ones. The injection mechanics (breaking out of a string with ', using comments) are identical — only the query type differs.

## TOPIC 11: DELETE
Removes rows.
Syntax: DELETE FROM table_name WHERE condition;

Same warning as UPDATE — even more destructive

DELETE FROM users;

No WHERE = every row in the table gone. Unlike UPDATE, there's no "wrong value" to fix afterward — the data is just gone (unless you have a backup). Always run a SELECT with the same WHERE clause first to confirm exactly which rows you're about to hit, before running the DELETE.

SELECT * FROM users WHERE country = 'France'; --check first
DELETE FROM users WHERE country = 'France'; --then delete

## TOPIC 12: CREATE TABLE
Create table in a database
Syntax: CREATE TABLE table_name (
    column1 datatype constraints,
    column2 datatype constraints,
    ...
);
Common data types you'll use: INT, VARCHAR(n), DATE, BOOLEAN, TEXT.
Common keywords: PRIMARY KEY, AUTO_INCREMENT.

e.g.,
CREATE TABLE orders (
    order_id INT PRIMARY KEY AUTO_INCREMENT,
    user_id INT,
    product VARCHAR(100),
    amount DECIMAL(10,2)
);

INSERT INTO orders (user_id, product, amount) VALUES
(1, 'Laptop', 999.99),
(2, 'Mouse', 25.50),
(2, 'Keyboard', 45.00),
(3, 'Monitor', 199.99);

Notice user_id here — it's not marked as a formal FOREIGN KEY constraint (we'll touch that in Topic 15), but it conceptually points to users.id.

**SQLi relevance**

Same as INSERT — low as something you'll run against a target directly. Its value here is purely that you now have a second table with a relationship to users, which is what makes Joins and UNION-based extraction meaningful.

## TOPIC 13: ALTER TABLE
ALTER TABLE modifies the structure of an existing table — adding, removing, or changing columns after the table already exists.

**ADD COLUMN: ALTER TABLE users ADD COLUMN phone VARCHAR(50);**
Adds a new column to the existing table. Existing rows get NULL for this new column since no value was given.
**DROP COLUMN: ALTER TABLE users DROP COLUMN phone;**
Removes a column entirely — including all data in it. No undo.
**MODIFY COLUMN: ALTER TABLE users MODIFY COLUMN username VARCHAR(100);**
Changes a column's data type or size - Widens username from its original size to 100 characters.
**RENAME COLUMN: ALTER TABLE users RENAME COLUMN email TO contact_email;**

**SQLi relevance**

Very low as an attack technique — you're not restructuring a target's live table. But it's worth knowing conceptually because ALTER TABLE (and DDL statements generally) sometimes show up in a different context: privilege escalation once you already have SQLi access. If an attacker's injected user has enough database privileges, they could theoretically use DDL statements like this to modify the schema — but that's an advanced/rare scenario, not something you need to focus energy on now.

**DESCRIBE users; shows you the table's column structure — useful command to know, it's basically "show me the schema" for a table you already have access to.**

## TOPIC 14: DROP/TRUNCATE
Two ways to wipe out a table — but they behave very differently.

**DROP TABLE**
Deletes the entire table — structure, data, indexes, everything. The table stops existing.
Syntax: DROP TABLE table_name;
Once dropped, it's gone. You'd need to CREATE TABLE again from scratch to get it back.

**TRUNCATE TABLE**
Empties all rows from a table, but keeps the table structure intact — columns, data types, constraints all remain.
Syntax: TRUNCATE TABLE table_name;

TRUNCATE is essentially "empty this table instantly," while DROP is "this table no longer exists." DELETE is the only one of the three that can selectively remove some rows via WHERE — the other two are all-or-nothing.

**SQLi relevance**

This is actually worth paying attention to, unlike the last couple topics — DROP TABLE is the classic "destructive" SQLi payload example everyone's seen, most famously from the xkcd "Bobby Tables" comic:

*Robert'); DROP TABLE students;--*

This works via stacked queries — some databases/drivers allow multiple statements separated by ; in a single injection. If the app is vulnerable to this and doesn't sanitize input, an attacker could terminate the intended query early and append a completely different, destructive one.

Worth knowing: MySQL via most standard web app configurations (PHP's mysqli, PDO in default mode) does not allow stacked queries by default — this is more of an MSSQL/PostgreSQL-relevant technique, or requires specific misconfigurations in MySQL. Good to know the concept and the reason it's the "iconic" SQLi example, but don't expect it to be your go-to technique on typical MySQL targets. Extraction (SELECT/UNION-based) is far more common and reliable in real engagements — which is exactly why your roadmap weights UNION and Information Schema so heavily and DROP/TRUNCATE so lightly.

## TOPIC 15: CONSTRAINTS
Constraints are rules attached to columns that enforce data integrity — they restrict what values can actually be stored.
**PRIMARY KEY**
Uniquely identifies each row. No duplicates, no NULLs allowed.
Syntax: id INT PRIMARY KEY AUTO_INCREMENT

**FOREIGN KEY**
Enforces that a column's value must match an existing value in another table's primary key.

CREATE TABLE orders (
    order_id INT PRIMARY KEY AUTO_INCREMENT,
    user_id INT,
    product VARCHAR(100),
    amount DECIMAL(10,2),
    FOREIGN KEY (user_id) REFERENCES users(id)
);
This means: MySQL will reject any INSERT into orders where user_id doesn't already exist in users.id. Your existing orders table (Topic 12) doesn't have this constraint formally defined — it worked anyway because you inserted valid IDs, but nothing was stopping a bad user_id from sneaking in. FOREIGN KEY is what would have blocked that.

**UNIQUE**
No duplicate values allowed in this column (unlike PRIMARY KEY, NULLs are still allowed, and you can have more than one UNIQUE column per table).

Syntax: email VARCHAR(100) UNIQUE

**NOT NULL**

Column must always have a value — can't be left empty.
Syntax: username VARCHAR(50) NOT NULL

**DEFAULT**

If no value is given on INSERT, use this value automatically.
Syntax: country VARCHAR(50) DEFAULT 'Unknown'

**Why this matters for SQLi**

Constraints are actually relevant here in a real way — they're part of why some injection attempts fail or throw errors that leak information. If an attacker's injected UNION SELECT tries to insert/reference a value that violates a NOT NULL or type constraint, the resulting database error can reveal table structure — this is a form of error-based SQL injection, where the error message itself becomes the leak.

More directly: understanding PRIMARY KEY / FOREIGN KEY relationships is what makes Joins (next topic) make sense — the FOREIGN KEY is the relationship JOIN operates on.

## TOPIC 16: JOINS
Joins let you pull data from two or more tables at once, matched on a related column — usually a primary key ↔ foreign key relationship.

**INNER JOIN**
Returns only rows that have a match in both tables.
```
SELECT users.username, orders.product, orders.amount
FROM users
INNER JOIN orders ON users.id = orders.user_id;
```
The ON clause tells MySQL how to match rows: "connect a users row to an orders row when users.id equals orders.user_id."

Run this on your data — you'll get 4 rows (one per order), each showing which user placed it. Notice sara (id=3, no orders) and mike (id=4, no orders)... wait, check your data: your orders table has user_id 1, 2, 2, 3. So user_id 4 (mike) has no order — with INNER JOIN, mike simply won't appear at all, because there's no match on the orders side.

**LEFT JOIN**
Returns all rows from the left table, plus matching rows from the right table. If there's no match, the right table's columns show as NULL.

e.g.,
SELECT users.username, orders.product, orders.amount
FROM users
LEFT JOIN orders ON users.id = orders.user_id;

Now mike does appear, but with NULL for product and amount — because he has no matching order, but LEFT JOIN keeps him anyway since he exists in the "left" table (users).

This is genuinely useful for recon: "show me every user, and their orders if they have any" — you don't lose users just because they have zero related records.

**RIGHT JOIN**
The mirror of LEFT JOIN — all rows from the right table, matched rows from the left, NULL where no match.

e.g.,
SELECT users.username, orders.product, orders.amount
FROM users
RIGHT JOIN orders ON users.id = orders.user_id;

Since every order in your table does have a valid user_id, this looks identical to your INNER JOIN result here — RIGHT JOIN only visibly differs from INNER JOIN when the right table has unmatched rows.

**Why JOIN matters so much for SQLi**

Real applications almost never store everything in one table — usernames/passwords are typically in a users table, but useful data an attacker wants (admin flags, session tokens, financial records, other users' private data) often lives in separate related tables. Understanding JOIN means understanding how to navigate a real schema once you've mapped it out via information_schema (Topic 22) — you'll use JOIN-style thinking (even inside a UNION SELECT) to pull data that spans multiple tables in a single extraction.

## TOPIC 17: UNION
UNION combines the results of two separate SELECT statements into one result set, stacked vertically.

Syntax
SELECT username FROM users
UNION
SELECT product FROM orders;

This runs two completely different queries — one pulling usernames, one pulling products — and glues their results into a single output, one column, all rows stacked together.

This is fundamentally different from JOIN. JOIN combines tables side by side (more columns). UNION combines results top to bottom (more rows, same columns).

**The rule that makes or breaks UNION**
Both SELECT statements must return the exact same number of columns, and the data types should be compatible. This is exactly why you learned ORDER BY N for column-count fingerprinting back in Topic 4 — that skill exists specifically to prepare for this.

Try this — it will error:

e.g.,
SELECT username FROM users
UNION
SELECT product, amount FROM orders;
*ERROR 1222 (21000): The used SELECT statements have a different number of columns*

Left side has 1 column, right side has 2 — mismatch, hard fail. This is the exact error message you'll be hunting for (or avoiding, once you've found the right count) in real UNION-based injection.

**UNION vs UNION ALL**
UNION removes duplicate rows across the combined result. UNION ALL keeps everything, duplicates included, and is faster since MySQL doesn't have to check for dupes.

e.g.,
SELECT country FROM users
UNION
SELECT country FROM users;

**Since both sides pull identical data, plain UNION collapses everything down to just the distinct countries. Compare:**

e.g.,
SELECT country FROM users
UNION ALL
SELECT country FROM users;

This returns every row twice, no deduplication.

In real SQLi, UNION ALL is almost always preferred — you don't want the database silently dropping rows you're trying to steal just because they look similar to something else in the result.

## TOPIC 18: SUBQUERIES
A subquery is a SELECT nested inside another query — you use the result of one query as input to another.

Basic syntax:
SELECT * FROM users
WHERE id IN (SELECT user_id FROM orders);

The inner query (SELECT user_id FROM orders) runs first, producing a list of user_ids that have placed orders. The outer query then checks: "give me users whose id is in that list."
Run it — you should get admin, john, sara (they all have orders), but not mike, since he has no rows in orders.

**Subquery returning a single value**
If a subquery returns exactly one value, you can use it with = instead of IN:
e.g.,
SELECT FROM users
WHERE id = (SELECT MIN(user_id) FROM orders);

Finds the smallest user_id in orders (which is 1), then returns the user matching that id — admin.

**Careful**: if the subquery accidentally returns more than one row, = throws an error. IN is safer when you're not sure how many rows will come back.

**Subquery in the SELECT list**
You can also drop a subquery directly into your column list to pull a related single value per row:
e.g.,
SELECT username, 
    (SELECT COUNT(*) FROM orders WHERE orders.user_id = users.id) AS order_count
FROM users;

This runs the inner subquery once per row of the outer query, correlating on users.id — giving each user their own order count. (This is called a correlated subquery, since the inner query references the outer table.) You'll get 0 for mike, 1 each for admin/sara, 2 for john.

Subquery with NOT IN
e.g.,
SELECT * FROM users
WHERE id NOT IN (SELECT user_id FROM orders);

Flips the earlier example — users who have never placed an order. Should return just mike.

**Why this matters for SQLi**
Subqueries show up constantly in blind SQL injection, especially boolean-based blind. A classic pattern:

' AND (SELECT COUNT(*) FROM information_schema.tables) > 5 --

The attacker can't see query output directly (blind), but they can ask true/false questions using subqueries and observe whether the page behaves differently (loads normally vs. shows an error, or a subtle content difference). Each subquery-based question — "is there a table starting with 'a'?", "does the 5th character of the admin password equal 'p'?" — extracts one bit of information at a time. This is exactly how tools like sqlmap automate blind extraction under the hood.

## TOPIC 19: COMMENTS
The three comment styles in MySQL
sql
```
-- this is a comment (note the required space after --)
# this is also a comment
/* this is a multi-line comment */
```
**-- (double dash)**

Comments out everything to the end of the line. Critical detail: in MySQL, you need a space (or another whitespace character) right after -- for it to be recognized as a comment. --comment (no space) is not a valid comment in MySQL — this trips people up constantly.

SELECT * FROM users WHERE username = 'admin'; -- this part is ignored

**# (hash)**

Same effect as --, MySQL-specific (not standard SQL, won't work on most other databases like PostgreSQL or MSSQL).

SELECT * FROM users WHERE username = 'admin'; # this part is ignored

**/* */ (block comment)**

Comments out everything between the markers, can span multiple lines.

SELECT * FROM users /* this whole part is ignored */ WHERE id = 1;

## TOPIC 20: STRING FUNCTIONS
**CONCAT()**
Joins strings together.
e.g.,
SELECT CONCAT(username, ' - ', email) FROM users;
Merges multiple values into one string.

**LENGTH()**
Returns the number of characters in a string.
e.g.,
SELECT username, LENGTH(username) FROM users;

**SUBSTRING()**
Extracts part of a string. Syntax: SUBSTRING(string, start_position, length). Note: SQL string positions start at 1, not 0.
e.g.,
SELECT SUBSTRING(username, 1, 3) FROM users;

Grabs the first 3 characters of each username.

**UPPER() / LOWER()**
Converts case.
e.g.,
SELECT UPPER(username), LOWER(country) FROM users;

**Why these matter for SQLi — this is the big one**
SUBSTRING() and LENGTH() are the actual engine behind blind SQL injection, specifically when there's no UNION output visible at all — you can't see any data directly, only a true/false signal (page loads differently, response time changes, etc.).

Here's the real pattern. An attacker wants to know the admin's password, character by character, without ever seeing it printed:

sql
' AND SUBSTRING((SELECT password FROM users WHERE username='admin'), 1, 1) = 'a' --

This asks: "is the first character of admin's password the letter 'a'?" If the page behaves as if the condition were true (e.g. logs in, loads a slightly different page, or — in time-based blind SQLi — takes longer to respond), the attacker knows the first character is 'a'. If not, they try 'b', 'c', and so on — one character at a time, one HTTP request at a time.

sql
' AND LENGTH((SELECT password FROM users WHERE username='admin')) = 8 --

This asks: "is admin's password exactly 8 characters long?" — usually the very first question asked, before brute-forcing character-by-character, so the attacker knows when to stop.

This is exactly what sqlmap automates when it says "testing boolean-based blind" — thousands of these SUBSTRING/LENGTH true-false questions fired in sequence, reconstructing the entire password (or table name, or anything else) one character at a time, purely from true/false page behavior.

Hands-on — simulate the blind extraction yourself
sql
SELECT SUBSTRING((SELECT password FROM users WHERE username='admin'), 1, 1);
sql
SELECT LENGTH((SELECT password FROM users WHERE username='admin'));

Now do the true/false version, exactly like an attacker would send it:

sql
SELECT * FROM users WHERE username='admin' AND SUBSTRING(password, 1, 1) = 'a';

Try the real first letter of admin's password (admin123 → first letter a) — you should get the row back. Then try a wrong letter:

sql
SELECT * FROM users WHERE username='admin' AND SUBSTRING(password, 1, 1) = 'z';

Empty result. That difference — row vs. no row — is blind SQLi in its purest form.

Run these, then two topics left: Topic 21: Database Functions.

## TOPIC 21: DATABASE FUNCTIONS
**DATABASE()**
Returns the name of the database you're currently connected to.

SELECT DATABASE();

**VERSION()**
Returns the DBMS version string.

SELECT VERSION();

**USER() / CURRENT_USER()**
Returns the database user you're currently authenticated as.

SELECT USER();
SELECT CURRENT_USER();

They're usually the same, but can differ slightly depending on how the connection was authenticated.

**Why these matter enormously for SQLi**
This is one of the very first things attackers run the moment they confirm a UNION-based injection works — not to steal data yet, just to fingerprint the target:

' UNION SELECT DATABASE(), VERSION() --

# TOPIC 22: INFORMATION SCHEMA
information_schema is a special, built-in database that every MySQL/MariaDB server has automatically. It doesn't store the app's real data — it stores metadata: the structure of every other database on the server. Table names, column names, database names — the blueprint of everything.

**information_schema.tables**

Lists every table across every database on the server.
e.g.,
SELECT table_name, table_schema FROM information_schema.tables;
table_schema here means "which database this table belongs to." This returns a huge list — every table in lab, plus MySQL's own internal tables.

Filter to just your database:
e.g.,
SELECT table_name FROM information_schema.tables WHERE table_schema = 'lab';
You should see users and orders — the exact tables you've been working with all along.

**information_schema.columns**

Lists every column, for every table, across every database.
*SELECT column_name, table_name FROM information_schema.columns WHERE table_schema = 'lab';*

This returns every column name in your lab database, labeled with which table it belongs to — id, username, password, email, country for users, and order_id, user_id, product, amount for orders.

Narrow it to one specific table:
*SELECT column_name FROM information_schema.columns WHERE table_schema = 'lab' AND table_name = 'users';*

