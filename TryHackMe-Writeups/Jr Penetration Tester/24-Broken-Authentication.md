# Broken Authentication

## Overview

Learn how to defeat logins and other authentication mechanisms to allow you access to unpermitted areas.

## What I Learned

- Mitigating Username Enumeration
- Mitigating Brute Force
- Mitigating Logic Flaw
- Mitigating Cookie Tamepring

## Exercises

### Exercise 1 — [Type of Authentication Bypass]

**Q1.** What is the name for the practice of reusing credentials recovered from one application against unrelated applications?
**Answer:** Credential reuse

### Exercise 2 — [Username Enumeration]

**Q1.** What is the username starting with si*** ?
**Answer:** simon

**Q2.** What is the username starting with st*** ?
**Answer:** steve

**Q3.** What is the username starting with ro**** ?
**Answer:** robert

### Exercise 3 — [Brute Forcing a Login Form]

**Q1.** What is the valid username and password (format: username/password)?
**Answer:** steve/thunder

### Exercise 4 — [Logic Flaw]

**Q1.** What is the flag from Robert's support ticket?
**Answer:** THM{AUTH_BYPASS_COMPLETE}

### Exercise 5 — [Cookie Manipulation]

**Q1.** What is the flag from changing the plain text cookie values?
**Answer:** THM{COOKIE_TAMPERING}

**Q2.** What is the value of the md5 hash 3b2a1053e3270077456a79192070aa78 ?
**Answer:** 463729

**Q3.** What is the base64 decoded value of VEhNe0JBU0U2NF9FTkNPRElOR30= ?
**Answer:** THM{BASE64_ENCODING}

**Q4.** Encode the following value using base64 {"id":1,"admin":true}
**Answer:** eyJpZCI6MSwiYWRtaW4iOnRydWV9

## Key Takeaways

Authentication bypass vulnerabilities are usually caused by poorly coded web applications or poorly configured session management. There are, however, secure coding methods and design patterns that reduce the chances of being vulnerable to each class of attack covered in this room.

## Notes

**Four Classes of Authentication Bypass**

- Username enumeration is used to produce a list of accounts registered on the target application. This is done by submitting candidate usernames to a form that responds differently for registered and unregistered values, such as a signup or password reset page. The output is a short list of real accounts, which feeds directly into the credential attacks that follow.

- Credential brute force uses that list together with a dictionary of common passwords to find accounts whose passwords can be guessed. In the most basic case, the attacker pairs every username with every password in the dictionary and submits each combination to the login form. When the application does not apply rate limits or lockouts, the attack is inexpensive to run and frequently produces a working credential pair within seconds.

- Logic flaws occur when the intended flow of an authentication-related workflow can be redirected by valid-looking input. Password reset and account recovery workflows are a frequent source of such flaws, because they commonly split input across multiple HTTP parameters, cookies, and session variables. A mistake in how those inputs are combined can allow the reset link for one account to be delivered to a different address than the one on file.

- Cookie manipulation targets the session state that the server returns to the client after a successful login. Cookies that are not cryptographically signed can be edited by the client to change the authentication decision the server makes on subsequent requests. Common formats are plain text cookies, cookies containing a hash of an underlying value, and cookies containing a reversibly encoded payload such as base64.