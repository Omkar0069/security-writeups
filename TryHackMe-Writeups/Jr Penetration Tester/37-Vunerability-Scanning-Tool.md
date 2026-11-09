# Vulnerability Scanning Tools

## Overview

Learn about scanning tools such as Nmap, OpenVAS, and Nikto, and explore the world of pentesting.

## What I Learned

- Vulnerability scanning tools play a critical role in modern cyber security by automatically identifying weaknesses, misconfigurations, and outdated software across systems and networks. These tools help pentesters to detect potential attack vectors before adversaries can exploit them, making them essential for maintaining a strong security posture.

## Exercises

### Exercise 1 — [Important Topics]

**Q1.** What is the maximum range for a CVSS score?
**Answer:** 10

**Q2.** Correct Answer

What is a scanner called that examines devices on a network to identify open ports and running services?
**Answer:** network scanner

### Exercise 2 — [Nmap]

**Q1.** What is the FTP port number on the lab machine?
**Answer:** 21

**Q2.** What service is running on port 80 on the lab machine? 
**Answer:** WebSockify

**Q3.** What is the name of the scripting engine that allows Nmap to run specialised scripts written in Lua to extend its functionality?
**Answer:** Nmap Scripting Engine

### Exercise 3 — [Nikto Web Scanner]

**Q1.** What is the Apache Server version?
**Answer:** 2.4.58

**Q2.** Per the Nikto report, which flag is missing from the cookie in the web app?
**Answer:** HttpOnly

**Q3.**  What is the name of the directory with directory listing enabled?
**Answer:** static

**Q4.** What is the parameter vulnerable to RFI?
**Answer:** file

### Exercise 4 — [OpenVAS & Greenbone Vulnerability Management]

**Q1.** What is the severity number for the vulnerablility phpinfo() Output Reporting (HTTP)?
**Answer:** 5.3

**Q2.** What is the CVE value associated with Anonymous FTP Login Reporting?
**Answer:** CVE-1999-0497

**Q3.** What is the target Operating System?
**Answer:** Ubuntu 24.04

### Exercise 5 — [Types of Vulnerability DBs: Other Public VDBs]

**Q1.** What is the EDB-ID associated with CVE-2025-59342?
**Answer:** 52461

**Q2.** What is the author's name for the exploit with CVE-2025-59342?
**Answer:** BYTE REAPER

### Exercise 5 — [Mass Management]

**Q1.** What field in the profile response did you use to identify the escalation path?
**Answer:** role

**Q2.** What value did you set that field to?
**Answer:** admin

**Q3.** What is the flag?
**Answer:** THM{ch41ned_ap1_vulns_f0r_the_w1n}

## Key Takeaways

Start Light: Begin with non-intrusive scans to avoid slowing or disrupting the target system, especially in shared or production environments.
Right Tooling: Match the scanner to the job—use Nmap for network discovery, OpenVAS for deep analysis, and Nikto for web server checks.
Verify Results: Double-check high-severity findings manually because scanners can produce false positives or incomplete information.
Stay Updated: Keep scanning tools and vulnerability feeds up to date so the scanner can identify new CVEs and configuration issues.
Use Credentials: When allowed, run authenticated scans to get more accurate visibility into missing patches and internal weaknesses.
Compare Over Time: Save scan outputs and compare them regularly to track improvements, detect regressions, and monitor newly introduced issues.
Scan Smart: Schedule scans during low-traffic hours since vulnerability scanning can consume noticeable network and system resources.

## Notes

**Core Terminology:**

- Vulnerability: A vulnerability is a weakness or flaw in a system that could be exploited to bypass security or gain unauthorised access. It may result from outdated software, poor configuration, or design mistakes.

- Common Vulnerabilities and Exposure(CVE): A CVE is a unique identification number assigned to publicly known security flaw, enabling consistent tracking across various tools and databases. It helps security teams quickly reference and research the issue.

- Common Vulnerability Scoring System (CVSS): CVSS provides a standardised score (0-9) that measures the serverity or risk of vulnerability based on its impact and exploitability. Higher scores indicates issues that require urgent attention.

- Misconfiguration: A misconfiguration occurs when a system or service is setup incorrectly, creating unnecessary security weaknesses. These issues often arise from default settings, open permissions, or a lack of hardening.

- Software Vulnerability: A Software vulnerability is a flaw in an application's code or logic that allows unintended behaviour or exploitation. These weaknesses often require developers to apply patches or updates.

**Types of Vulnerability Scanner**

A network scanner examines devices on a network to identify open ports, running services, and possible exposure points. It helps map out what systems are accessible and where risks may exist.

A web application scanner analyses websites or web apps for security issues, including outdated components, weak configurations, or risky behaviours. It focuses specifically on the HTTP/HTTPS layer.

A host-based scanner runs directly on a system to check for missing patches, outdated software, and insecure configuration settings. It provides a detailed view of internal system health.

**Nmap**

Network Mapper (Nmap) is widely used network scanning tool that discovers hosts, identifies open ports, and determines which services are running on systems. It plays a key role in the early stages of vulnerability assessment by helping analysts understand what is exposed on a network. Before any vulnerability can be tested or expoited, Nmap is used to map the attack surface and gather essential information about the target environment.

NSE is a powerful framework that automates vulnerability checks. NSE scripts can test for common issues, weak configurations, outdated services, and more enabling Nmap to perform lightweight vulnerability assessments.

Nikto is a widely used web server vulnerability scanner that identifies insecure configurations, outdated components, and common web-based weaknesses. It performs a comprehensive scan of a target web server and checks it against thousands of known issues, including default files, dangerous HTTP methods, misconfigurations, and potential security exposures.

OpenVAS is a powerful vulnerability scanner that assesses both host-level weaknesses and web application security issues. It provides deep, authenticated and unauthenticated scanning, making it ideal for identifying misconfigurations, outdated software, missing patches, and exposed services.