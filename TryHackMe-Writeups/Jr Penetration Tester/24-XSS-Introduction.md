# XSS Introduction

## Overview

Learn to detect and exploit XSS to control visitors’ browsers.

## What I Learned

In this room, we explored the essential concepts and practical techniques behind XSS, one of the most common and dangerous vulnerabilities in modern web applications. We began by building a strong foundation, introducing key concepts such as JavaScript execution in the browser, the Document Object Model (DOM), cookies, and URL parameters. Understanding these elements is important because XSS attacks rely on how browsers interpret and execute client-side code.  

## Exercises

### Exercise 1 — [Important Terminologies]

**Q1.** What is the URL parameter in the URL http://google.com/text=?
**Answer:** test

**Q2.** Which is the most renowned scripting language for adding interactivity to the DOM?
**Answer:** Javascript

### Exercise 2 — [XSS Payload]

**Q1.** Which document property could contain the user's session token?
**Answer:** document.cookie

**Q2.** Which JavaScript method is often used as a Proof of Concept?
**Answer:** alert

### Exercise 3 — [Reflected XSS - Non-Persistent]

**Q1.** What is the text shown in the alert pop-up after a successful XSS attack?
**Answer:** Hack

**Q2.** What is the response, if you use the payload <script>alert('Test123')</script>?
**Answer:** Test123

### Exercise 4 — [Stored XSS - Persistant]

**Q1.** What is the alert pop-up after executing the payload mentioned in the task?
**Answer:** you are hacked

### Exercise 5 — [DOM Based XSS - Client Side]

**Q1.** What is the alert pop-up after executing the XSS payload?
**Answer:** Hacked you again

**Q2.** Does DOM XSS also occur on the server side? (yea/nay)
**Answer:** nay

### Exercise 6 — [Blind XSS]

**Q1.** What type of XSS is very similar to Blind XSS?
**Answer:** stored-xss

**Q2.** Extract the user's cookies using netcat and the payload. What is the Connection: value returned in the Netcat output?
**Answer:** keep-alive

### Exercise 7 — [Perfecting your Payload]

**Q1.** What is the flag you received from level six?
**Answer:** THM{XSS_MASTER}

## Key Takeaways

We then walked through the different types of XSS step by step. Starting with Reflected XSS, we observed how malicious input embedded in a URL can be immediately reflected by the application and executed in a victim’s browser. Next, we explored Stored XSS, where attacker-controlled input is saved on the server, such as in comments or user profiles, and later executed whenever other users view that content. We also examined DOM-Based XSS, which occurs entirely on the client side when JavaScript improperly processes user-controlled data within the DOM, allowing attackers to inject and execute scripts without the server being directly involved.

Finally, we looked at Blind XSS, a powerful variant where the attacker may not see the immediate result of their payload. Instead, the malicious script executes later in a different user’s browser, often an administrator reviewing logs, support tickets, or moderation panels. This demonstrates how XSS can be exploited even when attackers do not have direct visibility of the vulnerable interface.

## Notes

Web applications power most business workflows, and Cross-Site Scripting (XSS) remains one of the easiest paths for attackers to compromise users. Recent incidents show that XSS is being used to steal sessions, deliver malware, and escalate attacks within a network. 

- **URL parameters:** URL parameters (query strings) are the bits after ? in a URL that pass data to the site, for example, https://site.com/search?q=hello has a q parameter with the value hello. They’re user-controllable (typed in the address bar or sent by links/forms), so treat their values as untrusted input.
- **JavaScript:** The scripting language that runs inside the browser. XSS payloads are usually small JavaScript snippets that run in the victim’s page context and can read or modify the DOM, make network requests, or access cookies (unless protected).
- **Cookies:** Cookies store small pieces of data in the browser (session IDs, preferences). If a cookie is readable by JavaScript and an attacker can run JS via XSS, they can steal that cookie and hijack a session. HttpOnly is a flag that prevents JavaScript from reading the cookie (good).
- **Escaping:** Escaping (output encoding) means transforming user data so the browser treats it as plain text, not code, for example, turning < into &lt; so <script> becomes harmless text. A filter (input validation) checks that the input looks allowed (letters, numbers, length), but doesn’t stop data from becoming code when it’s later placed into a page. For example, raw user input <script>alert(1)</script> will be  escaped for HTML becomes &lt;script&gt;alert(1)&lt;/script&gt.

**XSS payloads are typically injected into areas of a website that accept and display user input.**
    Search fields
    Comment sections
    Profile names
    Feedback forms
    URL parameters

Reflected XSS occurs when a web app takes user input (such as a query string, form field, or header) and immediately displays it on a page without sanitising it. An attacker crafts a malicious link or form that contains JavaScript and convinces a victim to click it; because the site "reflects" the attacker’s input, the browser runs the injected script in the site’s origin. Typical triggers are search boxes, error messages, or any page that echoes parameters from the URL or POST body.

Stored XSS is more impactful than reflected XSS because the payload persists and can affect many users (admins, site visitors) over time. An attacker can plant a script in a comment, profile bio, message, or admin-only panel; whenever anyone (including admins) views that page, the browser executes the injected JavaScript in the context of the vulnerable origin. That script can steal session tokens and perform actions on behalf of the user. Stored XSS is commonly found in comment sections, user profiles, message boards, product reviews, and file upload features that render metadata.

DOM-based XSS occurs when client-side JavaScript reads attacker-controllable data from the DOM (URL, location.hash, location.search, document.referrer, localStorage, etc.) and writes it back into the page in an unsafe way (e.g. innerHTML, document.write, eval). The payload never needs to touch the server; the browser DOM itself becomes the attack surface, and the injected script runs immediately in the page’s origin.

Blind XSS is similar to a stored XSS (which we covered in Task 5) in that your payload gets stored on the website for another user to view, but in this instance, you can't see the payload working or test it against yourself first.