# Command Injection

## Overview

Learn about a vulnerability allowing you to execute commands through a vulnerable app, and its remediations.

## What I Learned

- Command Injection

## Exercises

### Exercise 1 — [Discovering Command Injection]

**Q1.** What variable stores the user's input in the PHP code snippet in this task?
**Answer:** $title

**Q2.** What HTTP method is used to retrieve data submitted by a user in the PHP code snippet?
**Answer:** GETE

**Q3.** If I wanted to execute the id command in the Python code snippet, what route would I need to visit?
**Answer:** /id

### Exercise 2 — [Exploiting Command Injection]

**Q1.** What payload would I use if I wanted to determine what user the application is running as?
**Answer:** whoami

**Q2.** What popular network tool would I use to test for blind command injection on a Linux machine?
**Answer:** ping

**Q3.** What payload would I use to test a Windows machine for blind command injection?
**Answer:** timeout

### Exercise 3 — [Remediation]

**Q1.** What is the term for the process of "cleaning" user input that is provided to an application?
**Answer:** sanitisation

## Key Takeaways

We started by looking at what command injection is and why it's such a high-impact vulnerability. From there, we explored how it happens in real application code by examining PHP and Python examples where user input flows directly into system calls. We then walked through how to detect both blind and verbose command injection, and looked at useful payloads for exploiting it on Linux and Windows systems. On the defensive side, we covered remediation techniques including input validation, sanitisation, and why defence in depth matters when filters can be bypassed. Finally, you put all of that into practice by exploiting a live vulnerable application to retrieve a flag.

## Notes

Web applications frequently execute commands on the underlying operating system as part of their normal functionality. When a developer builds an application that takes user input and passes it into a system command without proper checks, an attacker can inject additional commands alongside the legitimate ones. This is command injection, a vulnerability that allows arbitrary OS-level commands to be executed through a vulnerable application.

The injected commands run with the same privileges as the application itself. If a web server runs as a user called joe, every injected command executes as joe and inherits whatever permissions that account holds. If the application runs with elevated privileges, the impact scales accordingly.