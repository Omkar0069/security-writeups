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

To Remove a table use *DROP TABLE tablename;*

To Add data to table use *ALTER TABLE employees ADD newelements datatype;*

To Rename data to table use *ALTER TABLE employees  RENAME oldname TO newname;*

To add or modify datatype use *ALTER TABLE employees  MODIFY COLUMN country varchar(50);*

To Change the column position in table use *ALTER TABLE employees MODIFY element datatype AFTER element;

To add rows in table use *INSERT INTO tablename values (add values here);*

**SELECT**
To select only specific column you can use: *SELECT element1, element2 FROM table;*
To select only specific row you can use: *SELECT * FROM table WHERE element = 1;*

**Comparison operators:**
- **= - Equal to**
- **!= - Not equal to**
- **> - Greater than**
- **< - Less than**
- **>= - Greater than equal to**
- **<= - Less than equal to**

**UPDATE AND DELETE**
To update data from the table we use *UPDATE tablename SET element = smth;*(You can also use NULL to remove the element and keep it empty).

To delete the column use *DELETE FROM table WHERE argumentforsepcificvalue* (Do not use only DELETE FROM table as it will delete the entire table).

**AUTO-COMMIT COMMIT AND ROLLBACK**
*SET AUTOCOMMIT = OFF;* - This will not save the transactions.
*COMMIT* - To save the table.
*ROLLBACK* - It will save the current transaction to the last commit.

**DATE AND TIME**
To set current date - *CURRENT_DATE()*
To set current time - *CURRENT_TIME()*
To set current date and time - *NOW()*

USE - OR + TO ADD OR DELETE VALUES

**UNIQUE CONSTRAINT**
*CREATE TABLE products(*
	*product_id INT,*
 *   *product_name VARCHAR(25) UNIQUE,*
 *    *product_price DECIMAL(4,2)*
*);*
With this unique keyword we can't insert product with same name we must keep them UNIQUE.

If you want to add UNIQUE after you created a product you can use:
*ALTER TABLE products*
*ADD CONSTRAINT*
*UNIQUE (product_name);*

**NOT NULL CONSTRAINT**
*CREATE TABLE products(*
	*product_id INT,*
 *   *product_name VARCHAR(25) UNIQUE,*
 *    *product_price DECIMAL(4,2) NOT NULL*
*);*

AFTER CREATING ONE:
INSERT INTO products
VALUES (5, "GULABJAMUN", NULL);

This will give error as we previously set NOT NULL value so we need to give some value to the price element.

**CHECK CONSTRAINT**
CONSTRAINT chk_pay CHECK(hourly_pay >= 10.00);
Meaning check in the column hourly_pay and it should be greater than 10.00, chk_pay is just a nickname for check.
To drop the check 
ALTER TABLE tablename
DROP CHECK checkname;

**DEFAULT CONSTRAINT**
Default constraint give some default value if the value is not provided

WHILE CREATING A TABLE:
CREATE TABLE products(
    product_id INT,
    product_name VARCHAR(25),
    product_price DECIMAL(4, 2) DEFAULT 0.00
)

INSIDE EXISTING ONE:
ALTER TABLE products
ALTER product_price SET DEFAULT 0.00;