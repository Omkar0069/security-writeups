# Burp Suite: The Basics

## Overview

An introduction to using Burp Suite for web application pentesting.

## What I Learned

- Basics of Burp Suite

## Exercises

### Exercise 1 — [Essential concepts]

**Q1.** Which edition of Burp Suite runs on a server and provides constant scanning for target web apps?
**Answer:** Burp Suite Enterprise

**Q2.** Burp Suite is frequently used when attacking web applications and ______ applications.
**Answer:** Mobile

### Exercise 2 — [Features of Burp Suite]

**Q1.** Which Burp Suite feature allows us to intercept requests between ourselves and the target?
**Answer:** Proxy

**Q2.** Which Burp tool would we use to brute-force a login form?
**Answer:** Intruder

### Exercise 3 — [The Dashboard]

**Q1.** What menu provides information about the actions performed by Burp Suite, such as starting the proxy, and details about connections made through Burp?
**Answer:** Event Log

### Exercise 4 — [Navigation]

**Q1.** Which tab Ctrl + Shift + P will switch us to?
**Answer:** Proxy Tab

### Exercise 5 — [Operators]

**Q1.** In which category can you find a reference to a "Cookie jar"?
**Answer:** Sessions

**Q2.** In which base category can you find the "Updates" sub-category, which controls the Burp Suite update behaviour?
**Answer:** Suite

**Q3.** What is the name of the sub-category which allows you to change the keybindings for shortcuts in Burp Suite?
**Answer:** Hotkeys

**Q4.** If we have uploaded Client-Side TLS certificates, can we override these on a per-project basis (yea/nay)?
**Answer:** yea

### Exercise 6 — [Site Map]

**Q1.** What is the flag you receive after visiting the unusual endpoint?
**Answer:** THM{NmNlZTliNGE1MWU1ZTQzMzgzNmFiNWVk}

## Key Takeaways

You now have a solid understanding of the Burp Suite interface, configuration options, and the Burp Proxy. These skills will be essential as you continue your journey in web and mobile application penetration testing.

## Notes

In essence, Burp Suite is a Java-based framework designed to serve as a comprehensive solution for conducting web application penetration testing. It has become the industry standard tool for hands-on security assessments of web and mobile applications, including those that rely on application programming interfaces (APIs).

Simply put, Burp Suite captures and enables manipulation of all the HTTP/HTTPS traffic between a browser and a web server. This fundamental capability forms the backbone of the framework. By intercepting requests, users have the flexibility to route them to various components within the Burp Suite framework, which we will explore in upcoming sections. The ability to intercept, view, and modify web requests before they reach the target server or even manipulate responses before they are received by our browser makes Burp Suite an invaluable tool for manual web application testing.

**Features of Burpsuite Community:**
Proxy, Repeater, Intruder, Decoder, Comparer, Sequencer.

