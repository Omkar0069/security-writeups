# Host-Server Configuration Reviews

## Overview

Learn the basics of host-server configuration reviews.

## What I Learned

In this room, we covered the foundational concepts behind host and server configuration reviews. You now understand the distinction between vulnerability-based and configuration-based privilege escalation, and why misconfigurations remain among the most common and reliable escalation vectors encountered during penetration tests.

## Exercises

### Exercise 1 — [What is Configuration Reviews]

**Q1.** Yay or Nay: a host that passes a vulnerability scan with no findings is guaranteed to have a secure configuration.
**Answer:** nay

### Exercise 2 — [Security Baselines and Frameworks]

**Q1.** In a DISA STIG, which severity category represents the highest risk?
**Answer:** CAT I

### Exercise 3 — [Automated Compliance Tooling]

**Q1.** What commercial vulnerability scanner, developed by Tenable, includes compliance auditing functionality against CIS Benchmarks?
**Answer:** Nessus

### Exercise 4 — [Categories of Misconfiguration]

**Q1.** What special permission bit on Linux causes an executable to run with the privileges of the file's owner?
**Answer:** SUID

### Exercise 5 — [Structured Enumeration Methodolgy]

**Q1.** In the methodology described above, what is the first phase you should complete before checking for specific misconfigurations?
**Answer:** Situational Awareness

### Exercise 6 — [Reading a CIS Benchmark]

**Q1.** What Meterpreter command displays information about the compromised system, including OS and hostname?
**Answer:** sysinfo

## Key Takeaways

You have been introduced to the industry frameworks that define what a secure configuration baseline looks like. CIS Benchmarks and DISA STIGs provide comprehensive, auditable standards against which any host can be measured. Automated compliance tools such as Nessus, Lynis, OpenSCAP, and CIS-CAT make it practical to assess hosts against these standards at scale, and their output serves both defensive remediation and offensive enumeration.

The six categories of misconfiguration covered in this room, specifically user and group configuration, file and directory permissions, service configurations, scheduled tasks and cron jobs, credential storage, and network configuration, form the backbone of the structured enumeration methodology you will carry into subsequent rooms. Each category maps to specific checks in the frameworks and tools discussed, and each represents a class of finding that appears repeatedly in real-world engagements.

## Notes

A configuration review is a structured audit of a host's settings, permissions, services, and policies, measured against an accepted secured baseline. Its purpose is to identify deviations from that baseline that could introduce security risk. In the context of penetration testing, those deviations are potential vectors for privilege escalation.

Exploitation asks "what is broken in this software?" Configuration review asks "what is set up incorrectly on this system?"

A security baseline is a documented standart that defines how a system should be configured to meet an acceptable level of security. Rather than relying on individual judgement about what constitutes a "secure" setup, organisations adopt bselines that provide specific, measurable recommendations for every configurable aspect of a system, from password policies and file permissions to service configurations and network settings.

**CIS Benchmarks** The Center for Internet Security (CIS) publishes configuration benchmarks for a wide range of operating systems, cloud platforms, applications, and network devices. CIS Benchmarks are developed through a consensus-driven process involving security professionals from government, industry, and academia.

**DISA STIGs** The Defense Information Systems Agency (DISA), part of the U.S. Department of Defense, publishes Security Technical Implementation Guides (STIGs). STIGs prescribe hardening requirements for systems used in government and military environments. They are more prescriptive than CIS Benchmarks and are mandatory for systems within U.S. government networks.

**Nessus** is a commercial vulnerability scanner developed by Tenable. While it is best known for vulnerability scanning , Nessus also includes compliance auditing functionality. Administrators can configure Nessus to scan hosts against CIS Benchmarks, DISA STIGs, and custom audit policies. The resulting compliance report lists each check, its pass or fail status, and remidiation guidance for failed checks.

Structured Enumeration Methodolgy:
- Phase 1 - Situational Awareness
- Phase 2 - Category-Based Enumeration
- Phase 3 - Prioritisation and Exploitation