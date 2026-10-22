# SQL Injection: Introduction

## Overview

Learn how to detect and exploit SQL Injection vulnerabilities.

## What I Learned

- Identified the SQL syntax attackers use in injection payloads (UNION, LIKE, comments, information_schema)
- Understood how SQL Injection occurs when user input gets concatenated into queries
- Detected injection points by testing with special characters and watching application responses
- Exploited In-Band SQL Injection with Error-Based and Union-Based techniques to extract database contents
- Bypassed authentication using Blind SQL Injection
- Extracted data character-by-character using Boolean-Based and Time-Based Blind SQL Injection
- Understood Out-of-Band SQL Injection and DNS/HTTP exfiltration
- Applied remediation strategies: prepared statements, input validation, and least privilege

## Exercises

### Exercise 1 — [SQL Essentials for Injection]

**Q1.** What SQL statement combines results from two SELECT queries into one result set?
**Answer:** Union

**Q2.** What built-in database contains metadata about all other databases, tables, and columns in MySQL?
**Answer:** information_schema

### Exercise 2 — [What is SQL Injection]

**Q1.** What character is commonly used as a first test when probing for SQL Injection?
**Answer:** '

**Q2.** What type of SQL Injection returns results directly in the web page?
**Answer:** In-Band

### Exercise 3 — [In-Band SQL injection]

**Q1.** What subtype of In-Band SQLi relies on database error messages to extract information?
**Answer:** Error-Based

**Q2.** What SQL function returns the name of the current database in MySQL?
**Answer:** database()

### Exercise 4 — [Authentication Bypass]

**Q1.** What boolean condition is commonly injected to make a WHERE clause always evaluate to true?
**Answer:** 1=1

### Exercise 5 — [Boolean & Time-Based]

**Q1.** What MySQL function causes a deliberate time delay in a query's response?
**Answer:** SLEEP

### Exercise 6 — [Out-of-Band SQL Injection]

**Q1.** What protocol beginning with D is commonly used to exfiltrate data in Out-of-Band SQLi?
**Answer:** DNS

**Q2.** What MSSQL stored procedure can be used to trigger DNS lookups for data exfiltration?
**Answer:** xp_dirtree

### Exercise 7 — [Remediation and Prevention]

**Q1.** What is the primary and most effective defence against SQL Injection?
**Answer:** Prepared Statements

## Key Takeaways

This room covered a lot of ground. You picked up the SQL injection syntax, saw how the vulnerability occurs when apps shove user input into queries, and worked through the main SQLi types: In-Band (Error-Based and Union-Based), Blind (Authentication Bypass, Boolean-Based, Time-Based), and Out-of-Band. The four lab levels had you pulling credentials out of databases, bypassing logins, and guessing passwords one character at a time. On the defence side, you looked at prepared statements, input validation, and least privilege.

## Notes

Two tables within information_schema are particularly valuable during SQL Injection.
- information_schema.tables: list every table. The table_schema column holds the database names and the table_name holds the table name.
information_schema.columns: list every column. The table_name and column_name lets you discover the structure of any table.

What Makes It "Blind"?
Blind SQL Injection occurs when the application does not show query results or error messages to the user. The injection still works: the database still processes your malicious input,  but you have no direct way to see the output. Instead, you must infer whether your injection succeeded from the application's behaviour: did you get logged in? Did the page content change? Did the response take longer?

Out-of_Band SQL Injection: Instead of reading results through the web response, you force the database server to reach out to a server you control through a separate channel, usually DNS or HTTP, and carry the stolen data with it.