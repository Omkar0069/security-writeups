# SQLMap: Basics

## Overview

Learn about SQL injection and exploit this vulnerability through the SQLMap tool.

## What I Learned

- Basics of SQLMap

## Exercises

### Exercise 1 — [Introduction]

**Q1.** Which language builds the interaction between a website and its database?
**Answer:** sql

### Exercise 2 — [SQL Injection Vulnerability]

**Q1.** Which boolean operator checks if at least one side of the operator is true for the condition to be true?
**Answer:** or

**Q2.** Is 1=1 in an SQL query always true? (YEA/NAY)
**Answer:** YEA

### Exercise 3 — [Automated SQL Injection Tool]

**Q1.** Which flag in the SQLMap tool is used to extract all the databases available?
**Answer:** --dbs

**Q2.** Listening below which port number requires root access or privileged permissions?
**Answer:** 1024

### Exercise 4 — [Shell Listener]

**Q1.** Which flexible networking tool allows you to create a socket connection between two data sources?
**Answer:** socat

**Q2.** What would be the full command of SQLMap for extracting all tables from the "members" database? (Vulnerable URL: http://sqlmaptesting.thm/search/cat=1)
**Answer:** sqlmap -u http://sqlmaptesting.thm/search/cat=1 -D members --tables

### Exercise 5 — [Practical]

**Q1.** How many databases are available in this web application?
**Answer:** 6

**Q2.** What is the name of the table available in the "ai" database?
**Answer:** user

**Q3.** What is the password of the email test@chatai.com?
**Answer:** 12345678

## Key Takeaways

SQL injection vulnerability
Hunting SQL injection through the SQLMap tool

## Notes

SQLMap is an automated tool for detecting and exploiting SQL injection vulnerabilities in web applications. It simplifies the process of identifying these vulnerabilities. This tool is built into some Linux distributions, but you can easily install it if it's not.