# API Pentesting

## Overview

Explore how to identify and exploit common API security vulnerabilities.

## What I Learned

- REST API and API vulnerablilitesx`

## Exercises

### Exercise 1 — [How REST APIs Work]

**Q1.** Decode the JWT returned by the login endpoint. What role is assigned to the testuser account?
**Answer:** customer

### Exercise 2 — [Broken Object Level Authentication]

**Q1.** Access user 1's profile through the BOLA vulnerability. What is their email address?
**Answer:** admin@shop.thm

**Q2.** Retrieve user 1's order history. What is the flag contained in one of their orders?
**Answer:** THM{b0la_1s_the_numb3r_0ne_ap1_r1sk}

**Q3.** Were you able to modify another user's data using a PATCH request? (yea/nay)
**Answer:** yea

### Exercise 3 — [Broken Authentication and Excessive Data Exposure]

**Q1.** What HTTP status code indicates that rate limiting is in effect?
**Answer:** 429

**Q2.** What password did you discover for the admin account?
**Answer:** sunshine

**Q3.**  In the raw API response for sarah.chen, what sensitive field contains a bcrypt hash?
**Answer:** password-hash

**Q4.** Correct Answer

What information is revealed in the internal_notes field of sarah.chen's profile?
**Answer:** Flagged for suspicious activity on 2025-01-15

### Exercise 4 — [Mass Assignment and Rate Limiting]

**Q1.** What HTTP status code indicates that rate limiting is in effect?
**Answer:** 429

**Q2.** What password did you discover for the admin account?
**Answer:** sunshine

**Q3.**  In the raw API response for sarah.chen, what sensitive field contains a bcrypt hash?
**Answer:** password-hash

**Q4.** Correct Answer

What information is revealed in the internal_notes field of sarah.chen's profile?
**Answer:** Flagged for suspicious activity on 2025-01-15

### Exercise 5 — [Mass Management]

**Q1.** What is the term for the developer practice of applying all client-supplied fields directly to a data model without filtering?
**Answer:** mass assignment

**Q2.** After adding "role": "admin" to the PATCH request, what is your new role?
**Answer:** admin

**Q3.** Using your escalated privileges, access the admin users endpoint. How many total users are registered on the platform?
**Answer:** 7

**Q4.** What is the flag returned by the admin endpoint?
**Answer:** THM{m4ss_4ss1gnm3nt_pr1v_3sc}

### Exercise 5 — [Mass Management]

**Q1.** What field in the profile response did you use to identify the escalation path?
**Answer:** role

**Q2.** What value did you set that field to?
**Answer:** admin

**Q3.** What is the flag?
**Answer:** THM{ch41ned_ap1_vulns_f0r_the_w1n}

## Key Takeaways

Task 2 established the foundation: HTTP methods and their CRUD mappings, status codes relevant to security testing, JSON request and response structure, and the three common authentication mechanisms (API keys, Bearer tokens, and JWTs).

Task 3 introduced BOLA, the number one OWASP API Security Top 10 risk. You accessed other users' profiles and orders by changing object IDs in requests, and confirmed that the vulnerability extended to write operations.

Task 4 demonstrated brute-forcing an unprotected login endpoint and examined how APIs that return entire database objects in their responses leak sensitive data to anyone who inspects the raw JSON.

Task 5 escalated privileges through mass assignment by injecting a role field into a profile update request, and covered rate limiting abuse beyond authentication endpoints.

Task 6 required you to chain these techniques without guidance, progressing from profile inspection to privilege escalation to flag retrieval.

## Notes

An API(Application Programming Interface) is a structured interface that enables software componenets to communicate with each other. When a user logs into a mobile banking app, scrolls through reels or palces an order on a delivery platform, a client makes API calls to backend-server to fetch data and perform various operations.

**REST API** Representational State Transfer is not a protocol or a strict standard. It is an architectural style, a set of coventions that develops follow when building APIs over HTTP. 
- The core concept of RESTful API is the resources.

HTTP Methods - GET, POST, PUT, POST, PATCH, DELETE.

API Keys: The client includes a static key in a header and the server looks up the key to identify the client.
Bearer Tokens: In this authentication method, the client first authenticates by submitting credentials to login endpoint, and the server returns a token.
JSON Web Tokens: This is the most common format for bearer tokens. A JWT consists of three Base64-encoded parts separated by dots: a header (specifying the algorithm), a payload (containing claims such as user ID, role, and expiration), and a signature (ensuring the token has not been tampered with). The payload is not encrypted, only encoded. Anyone with the token can read its contents.

BOLA is an like an IDOR occurs when an API returns a requested object without verifying whether the requesting user is permitted to access it. BOLA holds top position in OWASP Top 10 because it appears in a large number of real-world APIs and frequently leads to mass data exposure.

Broken Authentication: Broken Authentication is a broad category of flaws in how an API verifies a user's identity. 

Mass Assignment: It is a vulnerablility that occurs when an API takes data from a client's request and applies it directly to an internal object without filtering which fields the client is permitted to set.