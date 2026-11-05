# Session Management

## Overview

Learn about session management and the different attacks that can be performed against insecure implementations.

## What I Learned

To defend against these attacks, it is important to implement a secure session management lifecycle. 

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

- The session's values must be stored securely, regardless of being a cookie or a token.
- The session values themselves must be either sufficiently random and non-guessable or use a signing mechanism to ensure that they cannot be tampered with.
- Sessions should be used to track user actions and perform authorisation checks to ensure the user can perform the requested action.
- Sessions should expire after a set amount of time to prevent them from being used for persistent access.
- If the logout button is pressed, the session should be removed client-side and invalidated server-side. Otherwise, a user would be unable to destroy their session if it was compromised.

## Notes

While interactions with web applications, you should realise that you do not provide a web application with your username and password on every request. Instead, after authentication, you are provided with a session. This session is used by the web application to keep your state, track your actions, and decide whether or not you are allowed to do what are you trying to do.

**Session Management Life Cycle:**

Session Creation: Once you provide your username and password, you receive a session value that is then sent with each new request.

Session Tracking: This session is submitter with each new request. This allows the web application to track your actions even though the HTTP protocol is stateless in nature.

Session Expiry: Session has an Expiry set to it when the session is expired the user is prompted again to authenticate themselves.

Session Termination: In some cases, user might forceibly perform a logout action. In the event that this occurs, the web application should terminate the user's session.

*IAAA stands for Identification, Authentication, Authorization, and Accountability. It is a security principle that is used to protect systems and data. IAAA ensures that only authorized users can access a system and that their actions can be tracked.*

**IAAA Model**

Identification: Identification is the process of verifying who the user is.

Authentication: Authentication is the process of ensuring that the user is who they say they are. If it is valid; this is the point where session creation would kick in.

Authorisation: What user can Access.

Accountability: Accountability is a process of creating a record of the actions performed by users.


**Cookie-Based Session Management**

Cookie-based session management is often called the old-school way of managing sessions. Once the web application wants to begin tracking, in a response, the Set-Cookie header value will be sent. Your browser will interpret this header to store a new cookie value. 

**Token-Based Session Management**

Token-based session management is a relatively new concept. Instead of using the browser's automatic cookie management features, it relies on client-side code for the process. After authentication, the web application provides a token within the request body. Using client-side js code, this token is then stored in the browser's localstorage.

**Vulnerabilities:**

- Weak Session Values
- Controllable Session Values
- Session Fixation
- Insecure Session Transmission

- Authorisation Bypass
- Insufficient Logging
- Session Expiry
- Session Termination