# SSRF Introduction

## Overview

Learn how to exploit Server-Side Request Forgery (SSRF) vulnerabilities, allowing you to access internal server resources.  

## What I Learned

- SSRF

## Exercises

### Exercise 1 — [Introduction]

**Q1.** What does SSRF stand for?
**Answer:** Server-Side Request Forgery

**Q2.** As opposed to a regular SSRF, what is the other type?
**Answer:** Blind

### Exercise 2 — [Examples]

**Q1.** What is the flag from the SSRF Examples site?
**Answer:** THM{SSRF_MASTER}

### Exercise 3 — [Finding an SSRF]

**Q1.** Based on simple observation, which of the following URLs is more likely to be vulnerable to SSRF?
    https://website.thm/index.php
    https://website.thm/list-products.php?categoryId=5325
    https://website.thm/fetch-file.php?fname=242533.pdf&srv=filestorage.cloud.thm&port=8001
    https://website.thm/buy-item.php?itemId=213&price=100&q=2
**Answer:** 3

### Exercise 4 — [Defeating Common SSRF Defense]

**Q1.** What method can be used to bypass strict rules?
**Answer:** Open Redirect

**Q2.** What IP address may contain sensitive data in a cloud environment?
**Answer:** 169.254.169.254

**Q3.** What type of list is used to permit only certain input?
**Answer:** Allow List

**Q4.** What type of list is used to stop only certain input?
**Answer:** Deny List

## Key Takeaways

SSRF exploits the trust that internal systems place in the application server. Backend services, databases, and cloud infrastructure often accept requests from the server without additional authentication, because they assume any request arriving from a trusted internal IP address is legitimate. An attacker who can control where the server sends its requests effectively inherits that trust.

## Notes

Server-Side Request Forgery (SSRF) is a vulnerability that allows an attacker to cause the server-side application to make HTTP requests to a destination of the attacker's choosing. In a typical SSRF attack, the attacker manipulates a parameter that the application uses to construct a server-side request, redirecting it to an internal service, a cloud metadata endpoint, or an external server under their control.