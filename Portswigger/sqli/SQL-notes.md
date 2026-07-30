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

# TOPIC 2: SELECT'
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