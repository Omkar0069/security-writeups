
# Moniker Link (CVE-2024-21413)

## Overview

Leak user's credentials using CVE-2024-21413 to bypass Outlook's Protected View.

## What I Learned

- Moniker Link

## Exercises

### Exercise 1 — [Introduction]

**Q1.** What "Severity" rating has the CVE been assigned?
**Answer:** Critical

### Exercise 2 — [Moniker Link]

**Q1.** What Moniker Link type do we use in the hyperlink?
**Answer:** file://

**Q2.** What is the special character used to bypass Outlook's "Protected View"?
**Answer:** !

### Exercise 3 — [Exploitation]

**Q1.** What is the name of the application that we use on the AttackBox to capture the user's hash?
**Answer:** Responder

**Q2.** What type of hash is captured once the hyperlink in the email has been clicked?
**Answer:** netNTLMv2

## Key Takeaways

The CVE is known to affect a large portion of the Office suite, and given its extremely low attack complexity, it's quite a spicy one. 

## Notes

Moniker Link (CVE-2024-21413) is a critical security vulnerability in Microsoft Outlook that allows attackers to bypass security warnings and leak a user's private login details.