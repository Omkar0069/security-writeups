# OWASP top 10: Basics

## Overview



## What I Learned

- 

## Exercises

### Exercise 1 — [IAAA]

**Q1.** What does IAAA stand for?
**Answer:** Identity, Authentication, Authorisation, Accountability

### Exercise 2 — [A01 Broken Access Control]

**Q1.** If you don't get access to more roles but can view the data of another users, what type of privilege escalation is this?
**Answer:** Horizontal

**Q2.** What is the note you found when viewing the user's account who had more than $ 1 million?
**Answer:** THM{Found.the.Millionare!}

### Exercise 3 — [A07 Authentication Failure]

**Q1.** What is the flag on the admin user's dashboard?
**Answer:** THM{Account.confusion.FTW!}

### Exercise 4 — [A09 Logging & Alerting Failures]

**Q1.** It looks like an attacker tried to perform a brute-force attack, what is the IP of the attacker?
**Answer:** 203.0.113.45

**Q2.** Looks like they were able to gain access to an account! What is the username associated with that account?
**Answer:** admin

**Q3.** What action did the attacker try to do with the account? List the endpoint the accessed.
**Answer:** /supersecretadminstuff

### Exercise 5 — [A02 Security Misconfiguration]

**Q1.** What's the flag?
**Answer:** THM{V3RB0S3_3RR0R_L34K}

### Exercise 6 — [A03 Software Supply Chain Failure]

**Q1.** What's the flag?
**Answer:** THM{SUPPLY_CH41N_VULN3R4B1L1TY}

### Exercise 7 — [A04 Cryptographic Failure]

**Q1.** What's the flag?
**Answer:** THM{CRYPTO_FAILURE_H4RDCOD3D_K3Y}, THM{WEAK_CRYPTO_FLAG}

### Exercise 8 — [A06 Insecure Design]

**Q1.** What's the flag?
**Answer:** THM{1NS3CUR3_D35IGN_4SSUMPT10N}

### Exercise 9 — [A05 Injection]

**Q1.** What's the flag?
**Answer:** THM{SSTI_FLAG_OBTAINED}

### Exercise 9 — [A08 Software or Data Integrity Failure]

**Q1.** What's the flag?
**Answer:** THM{INSECURE_DESERIALIZATION}

## Key Takeaways

A01 Broken Access Control: Enforce server-side checks on every request
A07 Authentication Failures: Enforce unique indexes on the canonical form, rate-limit/lock out brute force, and rotate sessions on password/privilege changes.
A09 Logging & Alerting Failures: Log the full auth lifecycle (fail/success, password/2FA/role changes, admin actions), centralise logs off-host with retention, and alert on anomalies (e.g., brute-force bursts, privilege elevation).

## Notes

The IAAA is a simple way to think about how users and their actions are verified on applications. Each item plays a crucial role and it isn't possible to skip a level. That means if a previous item isn't being performed the next item cannot be performed. The four items are:
**Identity** - The unique account that represent the person or service.
**Authentication** - Providing the identity (password, OTPs, passkeys).
**Authorisation** - What that is allowed to do.
**Accountability** - recording or alerting on who did what, when, and from where.

The three categories of OWASP Top 10:2025 discussed in this room relates to failures in how IAAA was implemented. Weaknesses here can be incredibly detrimental, as it can allow threat actors to either access the data of other users or gain more privileges than they are suppose to have.

**A01 Broken Access Control:** Broken Access Control happens when the server doesn't properly enforce who can access what on every request. A common occurance of this is IDOR(Insecure Direct Object Reference) where changing the parameters let you access someone else's data.

**A02 Security Misconfiguration** Security misconfiguration happens when systems, servers or applications are deployed with unsafe defaults, incomplete settings or exposed services. These are not code bugs but mistakes in environments, software, and network is set up. They create easy entry points for the attackers.

**AS03 Software Supply Chain Failure** Software supply chain failures happen when applications rely on components, libraries, services, or models that are compromised, outdated, or improperly verified. These weaknesses are not inherent in your code, but rather in the software and tools you depend on. Attackers exploit these weak links to inject malicious code, bypass security, or steal sensitive data.

**A04 Cryptographic Failure** Cryptographic failures happen when encryption is used incorrectly or not at all. This includes weak algorithms, hard-coded keys, poor key handling, or unencrypted sensitive data. These flaws let attackers access information that should be private.

**A05 Injection** Injection occurs when an application takes user input and mishandles it. Instead of processing the input securely, the application passes it directly into a system that can execute commands or queries, such as a database, a shell, a templating engine or API.

**A06 Insecure Design** Insecure design happens when flawed logic or architecture is built into a system from the start. These flaws stem from skipped threat modelling, no design requirements or reviews, or accidental errors.

**A07 Authentication Failure:** Authentication Failure happens when a user can't reliably verify or bind user's identity. Common issues include, username enumeration, weak guessable passwords, logic flaws in login/registration flow, insecure session or cookie handling.

**A08 Software or Data Integrity Failures** Software or Data Integrity Failures occur when an application relies on code, updates, or data it assumes are safe, without verifying their authenticity, integrity, or origin. This includes trusting software updates without verification, loading scripts or configuration files from untrusted sources, failing to validate data that impacts application logic, or accepting data such as binaries, templates, or JSON files without confirming whether it has been altered.

**A09 Logging & Alert Failures** When applications don't record or alert on security-relevant events, defender cannot detect or investigate the attacks. Good logging underpins accountability.