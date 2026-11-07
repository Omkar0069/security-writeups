# File Inclusion

## Overview

This room introduces file inclusion vulnerabilities, including Local File Inclusion (LFI), Remote File Inclusion (RFI), and directory traversal.

## What I Learned

- File Inclusion Vulnerablility

## Exercises

### Exercise 1 — [Path Traversal]

**Q1.** What function causes path traversal vulnerabilities in PHP?
**Answer:** file_get_contents

### Exercise 2 — [Local File Inclusion]

**Q1.** Give Lab #1 a try to read /etc/passwd. What would the request URI be?
**Answer:** /lab1.php?file=/etc/passwd

**Q2.** In Lab #2, what is the directory specified in the include function?
**Answer:** includes

### Exercise 3 — [Local File Inclusion - Continued]

**Q1.** Give Lab #3 a try to read /etc/passwd. What is the request look like?
**Answer:** /lab3.php?file=../../../../etc/passwd

**Q2.** Which function is causing the directory traversal in Lab #4?
**Answer:** file_get_contents


**Q3.** Try out Lab #6 and check what is the directory that has to be in the input field?
**Answer:** THM-profile

**Q4.** Try out Lab #6 and read /etc/os-release. What is the VERSION_ID value?
**Answer:** 12.04

## Key Takeaways

File inclusion vulnerabilities let an attacker trick a web application into exposing, or even executing, files that were never meant to be accessible. The underlying weaknesses span several categories in the OWASP Top 10. Path traversal falls under Broken Access Control (A01), file inclusion through unsanitised input maps to Injection (A03), and the server configurations that enable remote inclusion relate to Security Misconfiguration (A05). These vulnerabilities remain one of the most common flaws found in real-world web application assessments.

## Notes

file inclusion vulnerabilities let an attacker trick a web application into exposing, or even executing files that were never meant to be accessible. The underlying weaknesses span several categories in OWASP Top 10.