# Broken Authentication

## Overview

Learn how to defeat logins and other authentication mechanisms to allow you access to unpermitted areas.

## What I Learned



## Exercises

### Exercise 1 — [What is Session Management?]

**Q1.** Which state in the session management lifecycle deals with user's pressing the logout button?
**Answer:** Session Termination

**Q2.** Which state in the session management lifecycle deals with user's providing their credentials?
**Answer:** Session Creation

**Q3.** Which state in the session management lifecycle deals with user's actions performed after authentication?
**Answer:** Session Tracking

**Q4.** Which state in the session management lifecycle deals with user's that forget to log out of the application?
**Answer:** Session Expiry

### Exercise 2 — [Authentication VS Authorisation]

**Q1.** What is the name of the process in the IAAA model that would be responsible for tracking your actions and logging them?
**Answer:** Accountability

**Q2.** What is the name of the process in the IAAA model that would be responsible for granting you a session value?
**Answer:** Authentication

**Q3.** What is the name of the process in the IAAA model that would be responsible for verifying that you have the relevant permissions to perform an action?
**Answer:** Authorisation

### Exercise 3 — [Cookies VS Tokens]

**Q1.** What cookie attribute can be used to ensure that the cookie is only transmitted via secure HTTPS channels?
**Answer:** secure

**Q2.** What HTTP header is used in the response to inform the browser that a cookie is being sent?
**Answer:** Set-cookie

**Q3.** What is the name of the process in the IAAA model that would be responsible for verifying that you have the relevant permissions to perform an action?
**Answer:** Authorization: Bearer

### Exercise 4 — [Securing the Session Lifecycle]

**Q1.** What phase of the session management lifecycle would be vulnerable if you could predict what the value of a session would be?
**Answer:** Session Creation

**Q2.** What phase of the session management lifecycle would be vulnerable if you don't have the ability to flush a threat actor's access to your session?
**Answer:** Session Termination

**Q3.** What phase of the session management lifecycle would be vulnerable if there wasn't sufficient information to piece together what happened during an incident?
**Answer:** Session Tracking

**Q4.** What phase of the session management lifecycle would be vulnerable if the session value itself was transmitted through an insecure redirect?
**Answer:** Session Creation

## Key Takeaways



## Notes

Authentication is the process by which a web application verifies the identity of the user making a request. When the credentials match, the server issues a session token that is returned on every subsequent request until the session expires, and the application uses that token to decide what the request is allowed to do.