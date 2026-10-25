# Broken Authentication

## Overview

Learn how to defeat logins and other authentication mechanisms to allow you access to unpermitted areas.

## What I Learned



## Exercises

### Exercise 1 — [Type of Authentication Bypass]

**Q1.** What is the name for the practice of reusing credentials recovered from one application against unrelated applications?
**Answer:** Credential reuse

### Exercise 2 — [Username Enumeration]

**Q1.** What type of action is usually required for a CSRF attack to succeed?
**Answer:** State-Changing

### Exercise 3 — [Finding CSRF Vulerabilites]

**Q1.** What HTTP request method do many developers incorrectly believe prevents CSRF?
**Answer:** POST

**Q2.** What mechanism is commonly used to protect applications from CSRF attacks?
**Answer:** CSRF Tokens

### Exercise 4 — [Exploitation Over Weak Tokens]

**Q1.** In the above example, what is the name of the encoding scheme used by the developer for encoding CSRF tokens?
**Answer:** base64

## Key Takeaways



## Notes

**Four Classes of Authentication Bypass**

- Username enumeration is used to produce a list of accounts registered on the target application. This is done by submitting candidate usernames to a form that responds differently for registered and unregistered values, such as a signup or password reset page. The output is a short list of real accounts, which feeds directly into the credential attacks that follow.

- Credential brute force uses that list together with a dictionary of common passwords to find accounts whose passwords can be guessed. In the most basic case, the attacker pairs every username with every password in the dictionary and submits each combination to the login form. When the application does not apply rate limits or lockouts, the attack is inexpensive to run and frequently produces a working credential pair within seconds.

- Logic flaws occur when the intended flow of an authentication-related workflow can be redirected by valid-looking input. Password reset and account recovery workflows are a frequent source of such flaws, because they commonly split input across multiple HTTP parameters, cookies, and session variables. A mistake in how those inputs are combined can allow the reset link for one account to be delivered to a different address than the one on file.

- Cookie manipulation targets the session state that the server returns to the client after a successful login. Cookies that are not cryptographically signed can be edited by the client to change the authentication decision the server makes on subsequent requests. Common formats are plain text cookies, cookies containing a hash of an underlying value, and cookies containing a reversibly encoded payload such as base64.