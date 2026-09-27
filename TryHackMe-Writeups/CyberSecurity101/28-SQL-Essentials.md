# SQL Fundamentals

## Overview

Learn how to perform basic SQL queries to retrieve and manage data in a database.

## What I Learned

- SQL Essentials

## Exercises

### Exercise 1 — [Essential concepts]

**Q1.** What type of database should you consider using if the data you're going to be storing will vary greatly in its format?
**Answer:** Non-relational Database

**Q2.** What type of database should you consider using if the data you're going to be storing will reliably be in the same structured format?
**Answer:** Relational Database

**Q3.** In our example, once a record of a book is inserted into our "Books" table, it would be represented as a ___ in that table?
**Answer:** Row

**Q4.** Which type of key provides a link from one table to another?
**Answer:** Foreign key

**Q5.** which type of key ensures a record is unique within a table?
**Answer:** Primary Key

### Exercise 2 — [SQL]

**Q1.** What serves as an interface between a database and an end user?
**Answer:** DBMS

**Q2.** What query language can be used to interact with a relational database?
**Answer:** SQL

### Exercise 3 — [CRUD Operations]

**Q1.** Using the tools_db database, what is the name of the tool in the hacking_tools table that can be used to perform man-in-the-middle attacks on wireless networks?
**Answer:** Wi-Fi Pineapple

**Q2.** Using the tools_db database, what is the shared category for both USB Rubber Ducky and Bash Bunny?
**Answer:** USB attacks

### Exercise 4 — [Clauses]

**Q1.** Using the tools_db database, what is the total number of distinct categories in the hacking_tools table?
**Answer:** 6

**Q2.** Using the tools_db database, what is the first tool (by name) in ascending order from the hacking_tools table?
**Answer:** Bash Bunny

**Q3.** Using the tools_db database, what is the first tool (by name) in descending order from the hacking_tools table?
**Answer:** Wi-Fi Pineapple

### Exercise 5 — [Operators]

**Q1.** WUsing the tools_db database, which tool falls under the Multi-tool category and is useful for pentesters and geeks?
**Answer:** Flipper Zero

**Q2.** Using the tools_db database, what is the category of tools with an amount greater than or equal to 300?
**Answer:** RFID Cloning

**Q3.** Using the tools_db database, which tool falls under the Network intelligence category with an amount less than 100?
**Answer:** Lan Turtle

### Exercise 6 — [Functions]

**Q1.** Using the tools_db database, what is the tool with the longest name based on character length?
**Answer:** USB Rubber Ducky

**Q2.** Using the tools_db database, what is the total sum of all tools?
**Answer:** 1444

**Q3.** Using the tools_db database, what are the tool names where the amount does not end in 0, and group the tool names concatenated by " & ".
**Answer:** Flipper Zero & iCopy-XS

## Key Takeaways

Understood what databases are, as well as key terms and concepts
Understood the different types of databases 
Understood what SQL is
Understood and be able to use SQL CRUD Operations
Understood and be able to use SQL Clauses Operations
Understood and be able to use SQL Operations
Understood and be able to use SQL Operators
Understood and be able to use SQL Functions

## Notes

- Once a database is no longer needed use drop database_name; to stop using it.
- Similarly we could drop a table using, DROP TABLE table_name;
- A clause is a part of a statement that specifies the criteria of the data being manipulated, usually by an initial statement. Clauses can help us define the type of data and how it should be retrieved or sorted. 

**Logical Operators**
LIKE Operator: The LIKE operator is commonly used in conjunction with clauses like WHERE in order to filter for specific patterns within a column. Let's continue using our DataBase to query an example of its usage.

AND Operator: The AND operator uses multiple conditions within a query and returns TRUE if all of them are true.

OR Operator: The OR operator combines multiple conditions within queries and returns TRUE if at least one of these conditions is true.

NOT Operator: The NOT operator reverses the value of a boolean operator, allowing us to exclude a specific condition.

BETWEEN Operator: The BETWEEN operator allows us to test if a value exists within a defined range.

**Comparison Operators**
Equal To Operator: The = (Equal) operator compares two expressions and determines if they are equal, or it can check if a value matches another one in a specific column.

Not Equal To Operator: The != (not equal) operator compares expressions and tests if they are not equal; it also checks if a value differs from the one within a column.

Less Than Operator: The < (less than) operator compares if the expression with a given value is lesser than the provided one.

Greater Than Operator: The > (greater than) operator compares if the expression with a given value is greater than the provided one.

Less Than or Equal To and Greater  Than or Equal To Operators: The <= (Less than or equal) operator compares if the expression with a given value is less than or equal to the provided one. On the other hand, The >= (Greater than or Equal) operator compares if the expression with a given value is greater than or equal to the provided one. Let's observe some examples of both below.

**FUNCTIONS** 
CONCAT() Function - This function is used to add two or more strings together. It is useful to combine text from different columns.

GROUP_CONCAT() Function - This function can help us to concatenate data from multiple rows into one field. Let's explore an example of its usage.

SUBSTRING() Function - This function will retrieve a substring from a string within a query, starting at a determined position. The length of this substring can also be specified.

LENGTH() Function - This function returns the number of characters in a string. This includes spaces and punctuation. We can find an example below.

COUNT() Function - This function returns the number of records within an expression.

SUM() Function - This function sums all values (not NULL) of a determined column.

MAX() Function - This function calculates the maximum value within a provided column in an expression.

MIN() Function - This function calculates the minimum value within a provided column in an expression.

