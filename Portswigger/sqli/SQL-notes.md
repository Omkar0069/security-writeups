 **SQL** - SQL stands for structured Query Language, it is used to create, retrive, update and delete data from **database**.
There are 2 types of database we'll discuss; Relational and Non-Relational:
1. **Relational** - Table in relational db represents Excel spreadsheet there are rows and columns they confirm relation with eachother using keys.
2. **Non-Relational** - Data is organized in anyform but a table this could include json files, key-value pairs etc.

To utilize data in **Relational database** we use SQL and in **Non-Relational database** we use NO-SQL.

# PRACTICAL IN MYSQL-Workbench:
**To create a database** use *CREATE DATABASE nameofdb;*.
**TO use that database** use *USE nameofdb;*.
How about alter, there's 2 features for beginner; setting a database to read-only and another is enabling encrytion.
**READ ONLY** use *ALTER DATABASE nameofdb READ ONLY = 1;* (use 0 instead of 1 to turn off read only mode)
When we use this query we can only read the database and cannot modify it.
Similarly to drop a database use *DROP DATABASE nameofdb;*

**How to create Tables in mysql:**
Tables in a relational database consist of roads and columns kinda like an excel spreadsheet.
To create a table *CREATE TABLE nameoftb (element datatypes, element datatypes, element datatype);*.

To select the table use *SELECT * FROM employees;*

To rename a table use *RENAME TABLE oldname TO newname;*

To Drop a table use *DROP TABLE tablename;*

To Add data to table use *ALTER TABLE employees ADD newelements datatype;*

To Rename data to table use *ALTER TABLE employees  RENAME oldname TO newname;*

To add or modify datatype use *ALTER TABLE employees  MODIFY COLUMN country varchar(50);*

To Change the column position in table use *ALTER TABLE employees MODIFY element datatype AFTER element;

To add rows in table use *INSERT INTO tablename values (add values here);*
