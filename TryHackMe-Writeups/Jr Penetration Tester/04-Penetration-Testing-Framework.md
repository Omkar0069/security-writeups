# Penetration Testing Framework

## Overview

Explore the landscape of penetration testing frameworks.

## What I Learned

- Some Frameworks

## Exercises

### Exercise 1 — [Introduction]

**Q1.** A penetration tester runs several tools against a target but skips network mapping entirely and does not document the scope beforehand. Which benefit of using a framework would have most directly prevented this situation?
**Answer:** Thoroughness

**Q2.** Your client operates in the healthcare sector and must demonstrate compliance with HIPAA. Beyond identifying vulnerabilities, which benefit of using a recognized framework would matter most to this client?
**Answer:** compliance

### Exercise 2 — [OSSTMM]

**Q1.** What OSSTMM metric quantifies the balance between an organization's attack surface and its controls?
**Answer:** Risk Assessment Values

**Q2.** During an OSSTMM assessment, you complete Induction and Interaction, identifying 6 hosts running unpatched services. Which phase do you enter next, and what is the primary objective?
**Answer:** Inquiry

### Exercise 3 — [OWASP WSTG]

**Q1.** The WSTG organizes its test cases using a specific identifier format. What identifier would you look for to find test cases related to input validation?
**Answer:** WSTG-INPV

**Q2.** A development team has just finished coding a new feature and wants to check it against WSTG before deployment. Which SDLC-aligned phase number are they in?
**Answer:** 3

### Exercise 4 — [NIST SP 800-115]

**Q1.** During the Execution phase, your vulnerability scanner flags 15 potential issues on a web application. Before attempting exploitation, which NIST SP 800-115 technique category should you apply to these findings?
**Answer:** Target Vulnerability Validation

### Exercise 5 — [PTES]

**Q1.** Which PTES phase number specifically addresses defining the scope, rules of engagement, and legal authorization for a penetration test?
**Answer:** 1

### Exercise 6 — [ISSAF]

**Q1.** ISSAF's nine-step assessment model begins with information gathering. What is the ninth and final step?
**Answer:** Covering Tracks

### Exercise 7 — [MITRE ATT&CK]

**Q1.** In the ATT&CK matrix, what do the columns represent?
**Answer:** Tactics

**Q2.** In the ATT&CK matrix, what do the rows within each column represent?
**Answer:** Techniques

**Q3.** You compromised a web server by exploiting an unpatched vulnerability in its public-facing application. What ATT&CK technique ID would you use to classify this finding?
**Answer:** T1190

### Exercise 8 — [Other Notable Frameworks]

**Q1.** Your client is a European online retailer that processes credit card payments through their website. Which framework from this task would most directly govern the penetration testing requirements for this engagement?
**Answer:** PCI DSS Penetration Testing Guidelines

**Q2.** A client asks you to assess the security of their iOS banking application, including how it stores credentials locally and communicates with backend APIs. Which framework from this task is the most appropriate testing reference?
**Answer:** OWASP Mobile Application Security Testing Guide

**Q3.** Your team is evaluating a client's AWS infrastructure to determine whether their cloud configurations meet industry security standards. They are not asking for a penetration test but rather a controls assessment. Which framework is most relevant?
**Answer:** CSA Cloud Control Matrix

### Exercise 8 — [Choosing the Right Framework]

**Q1.** A U.S. federal agency needs a security assessment of its internal network. The results must align with federal guidelines, and the assessment should include both document reviews and active penetration testing. Which framework is the most natural primary choice?
**Answer:** NIST SP 800-115

**Q2.** Your client is an e-commerce company with a web storefront, a mobile shopping app, and a payment processing system. Which combination of frameworks would you recommend to cover all three components? (comma-separrated)
**Answer:** WSTG,MASTG,PCI DSS

## Key Takeaways

We began with OSSTMM and its scientific, metrics-driven philosophy, where security is not a subjective opinion but a measurable property expressed through Risk Assessment Values. We then examined OWASP WSTG, the web application tester's roadmap, with its 90+ test cases organized across the Software Development Life Cycle. NIST SP 800-115 showed us how security testing fits into the government and enterprise world, structuring assessment techniques from passive document review through active exploitation. PTES brought us closest to the day-to-day reality of penetration testing, mapping seven phases from the first client call to the final report. ISSAF, though no longer maintained, gave us one of the clearest models of adversarial progression through its nine-step assessment. And MITRE ATT&CK provided the common vocabulary for describing what adversaries actually do, enriching findings from any framework with technique IDs grounded in real-world threat intelligence.

We surveyed five additional frameworks, each serving a specialized niche, from mobile application testing (OWASP MSTG) to regulatory mandates in the payment card industry (PCI DSS) and the UK financial sector (CBEST). Finally, we practiced the applied skill of framework selection, recognizing that real engagements often require a primary methodology supplemented by domain-specific or regulatory frameworks.

## Notes

Without a structured approach, a penetration test quickly becomes a disorganized collection of random checks. You might miss critical attack surfaces, skip important documentation, or deliver findings that the client cannot act on. Worse, you might test systems that were never in scope and find yourself in legal trouble. This is exactly the problem that penetration testing frameworks solve.

The OSSTMM testing cycle has four phases.

Phase 1: Induction covers enumeration and verification.
Phase 2: Interaction covers qualification and quantification. 
Phase 3: Inquiry covers privilege escalation and verification escalation.
Phase 4: Intervention covers quarantine, audit, and enticement.

OSSTMM (Open Source Security Testing Methodology Manual) applies the scientific method to security testing it defines the characteristics in metrics rather than opinions.

OSSTMM manages testing over 5 Security Channel:

**Human Security:** Social Engineering and human-factor authentication.
**Physical Security:** Physical Access control from badge reader to tailgating.
**Wireless Communications:** Wi-Fi, Bluetooth, RFID, and other electromagnetic signals.
**Telecommunication:** Phone Systems, VoIP, fax, and modern infrastructure.
**Data Security:** Network Services, firewall and application layer protocol.


OWASP(Open Web Application Security Project) addresses the problem with Web Security Testing Guide(WSTG). While OWASP is mostly known for the OWASP top 10 list of critical vulnerabilities; the WSTG goes deeper. It is a comprehensive, community-driven framework that organizes web application testing into over 90 discrete test cases grouped across twelve categories.