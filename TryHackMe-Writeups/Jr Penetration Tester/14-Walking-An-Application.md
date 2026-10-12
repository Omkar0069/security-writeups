# Nmap Post Port Scan

## Overview

Manually review a web application for security issues using only your browser's developer tools. 

## What I Learned

- Manual testing sharpens your pentesting mindset. Before relying on automated tools, learning to observe, question, and analyse what’s happening in the browser will make you far more effective. Tools are powerful, but a trained eye and a curious mindset are even more powerful.

## Exercises

### Exercise 1 — [Exploring the Website]

**Q1.** What is the endpoint for creating new tickets?
**Answer:** /customers/ticket/new

### Exercise 2 — [Viewing the Source Page]

**Q1.** What is the flag from the HTML comment?
**Answer:** THM{HTML_COMMENTS_ARE_DANGEROUS}

**Q2.** What is the flag from the secret link?
**Answer:** THM{NOT_A_SECRET_ANYMORE}

**Q3.** What is the directory listing flag?
**Answer:** THM{INVALID_DIRECTORY_PERMISSIONS}

**Q4.** What is the framework flag?
**Answer:** THM{KEEP_YOUR_SOFTWARE_UPDATED}

### Exercise 3 — [Developer Tools - Inspector]

**Q1.** What is the flag behind the paywall?
**Answer:** THM{NOT_SO_HIDDEN}

### Exercise 4 — [Developer Tools - Debugger]

**Q1.** What is the flag in the red box?
**Answer:** THM{CATCH_ME_IF_YOU_CAN}

### Exercise 5 — [Developer Tools - Networks]

**Q1.** What is the flag under the Response tab on the contact-msg network request?
**Answer:** THM{GOT_AJAX_FLAG}

### Exercise 6 — [Developer Tools - Storage]

**Q1.** What is the value of the HttpOnly flag after logging in?
**Answer:** False

## Key Takeaways

By diving into the developer tools, including the Inspector, Debugger, Network, and Storage tabs, we explored how modern web applications function behind the scenes. We saw how content can be manipulated client-side, how network requests expose application behaviour, and how cookies and local storage handle session data. Understanding these components helps build a strong foundation in identifying client-side weaknesses. 

## Notes

**Inspector** - The Inspector tab provides a live vew of what is currently on the website. In addition to viewing this live view, we can also edit and interact with page elements, which is helpful for web developers to debug issues.

**Debugger** - This panel in the developer tools is intended for debugging JavaScript, and again is an excellent feature for web developers wanting to work out why something might not be working. But as penetration testers, we can dig deep into the JavaScript code. In Firefox and Safari, this feature is called Debugger, but in Google Chrome, it's called Sources.