# IDOR

## Overview

Learn how to find and exploit IDOR vulnerabilities in a web application giving you access to data that you shouldn't have.

## What I Learned

- IDOR is classified as an access control vulnerability. It sits within the Broken Access Control category at position one in the OWASP Top 10. The same underlying flaw appears in the OWASP API Security Top 10 under the name Broken Object Level Authorisation (BOLA). The terminology differs depending on context, but the root cause is identical: the server does not verify that the authenticated user has permission to interact with the specific object they are requesting.

## Exercises

### Exercise 1 — [Introduction]

**Q1.** What does IDOR stand for?

### Exercise 2 — [An IDOR Example]

**Q1.** What is the Flag from the IDOR example website?
**Answer:** THM{IDOR-VULN-FOUND}

### Exercise 3 — [Finding IDORs in Encoded IDs]

**Q1.** What is a common type of encoding used by websites?
**Answer:** base64

### Exercise 4 — [Finding IDORs in Hashed IDs]

**Q1.** What is a common algorithm used for hashing IDs?
**Answer:** MD5

### Exercise 5 — [Finding IDORs in Unpredictable IDs]

**Q1.** What is the minimum number of accounts you need to create to check for IDORs between accounts?
**Answer:** 2

### Exercise 6 — [Practical]

**Q1.** What is the username for user id 1?
**Answer:** adam84

**Q2.** What is the email address for user id 3?
**Answer:** j@fakemail.thm

## Key Takeaways

What makes IDOR significant is the gap between its simplicity and its impact. Exploiting the vulnerability often requires nothing more than changing a number in a URL or request body. There is no need for injection, no need for session hijacking, and no need for any specialised tooling. Yet the consequences can range from mass data disclosure to full account takeover, depending on what the vulnerable endpoint exposes.

## Notes

Web applications rely on identifiers to distinguish one object from another. A user profile, an invoice, a support ticket, and a private document each have some kind of reference (often a number or a string) that the application uses internally to locate them. When an application allows the user to supply that reference and then retrieves the corresponding object without checking whether the user is permitted to access it, the result is an Insecure Direct Object Reference (IDOR).