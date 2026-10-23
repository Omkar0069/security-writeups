# CSRF Introduction: Introduction

## Overview

Understand CSRF vulnerability and practice exploiting insecure state-changing requests.

## What I Learned

In this room, we explored the concept of CSRF and how attackers can abuse a victim’s authenticated session to perform unintended actions. Through practical exercises, we observed that simple actions, such as submitting a hidden form or interacting with a webpage element, can trigger malicious requests.

We also saw that even applications that implement CSRF protection can remain vulnerable if the protection mechanism is weak or predictable. By reversing a poorly designed token, you recreated a valid request and successfully bypassed the defence. Finally, we reviewed important practices that pentesters should follow when identifying CSRF vulnerabilities during assessments. 

## Exercises

### Exercise 1 — [What is CSRF?]

**Q1.** What relationship between the browser and the web application does a CSRF attack abuse?
**Answer:** Trust

**Q2.** What does the browser automatically include with requests after login?
**Answer:** Cookies

### Exercise 2 — [Why CSRF Works?]

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

- Focus on state-changing requests: Prioritise requests that modify data, such as password changes, email updates, account settings, or financial transactions. These endpoints are the most common targets for CSRF attacks.
- Inspect requests for CSRF tokens: Check whether sensitive actions include a CSRF token. If no token exists, or if the token appears static or predictable, the request may be vulnerable. 
- Analyse HTTP methods: Sensitive actions should typically use POST requests. If important operations are performed through GET requests, they may be easier to exploit using images or simple links. 
- Test the requests outside of the application: Copy the request and try to reproduce it from an external HTML page. If the action succeeds without additional verification, the endpoint is likely vulnerable to CSRF. 
- Observe cookie behaviour: Check whether authentication relies only on session cookies. If the application automatically accepts requests containing the session cookie without validating the request origin, CSRF attacks become possible.

## Notes

**CSRF:**
Instead of stealing credentials, CSRF tricks a victim’s browser into performing actions on a website where the victim is already authenticated. Because the browser automatically includes cookies with requests, the web application may treat the malicious request as legitimate.

**What is CSRF?**
CSRF is a web vulnerability where an attacker tricks a user’s browser into sending a request to a website where the user is already authenticated. Because the browser automatically includes session cookies with every request, the web application assumes the request was made intentionally by the user.

Instead of stealing login credentials, the attacker abuses the trust relationship between the browser and the web application. If the request performs a sensitive action, such as changing an email address or updating account settings, the attacker may be able to modify the victim’s account without their knowledge.

For example, imagine a user is logged in to an internal portal while browsing the internet. If the user visits a malicious webpage, that page can silently trigger a request to the portal. If the application does not verify the origin of the request, it may process it as if the user initiated it.