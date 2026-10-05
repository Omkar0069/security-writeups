# Passive Reconnaissance

## Overview

Learn about the essential tools for passive reconnaissance, such as whois, nslookup, and dig.

## What I Learned

- This room covered gathering intelligence without direct interaction with the target: the stealthiest phase of reconnaissance.

## Exercises

### Exercise 1 — [Passive VS Active Recon]

**Q1.** You visit the Facebook page of the target company, hoping to get some of their employee names. What kind of reconnaissance activity is this? (A for active, P for passive)
**Answer:** P

**Q2.** You ping the IP address of the company webserver to check if ICMP traffic is blocked. What kind of reconnaissance activity is this? (A for active, P for passive)
**Answer:** A

**Q3.** You happen to meet the IT administrator of the target company at a party. You try to use social engineering to get more information about their systems and network infrastructure. What kind of reconnaissance activity is this? (A for active, P for passive)
**Answer:** A

### Exercise 2 — [Whois]

**Q1.** When was TryHackMe.com registered?
**Answer:** 20180705

**Q2.** What is the registrar of TryHackMe.com?
**Answer:** namecheap.com

**Q3.** Which company is TryHackMe.com using for name servers?
**Answer:** Cloudflare.com

### Exercise 3 — [nslookup & dig]

**Q1.** Check the TXT records of thmlabs.com. What is the flag there?
**Answer:** THM{a5b83929888ed36acb0272971e438d78}

### Exercise 4 — [DNSDumpster]

**Q1.** Lookup tryhackme.com on DNSDumpster. Under Services / Banners, which one has the highest count?
**Answer:** cloudflare

### Exercise 5 — [Shodan.io]

**Q1.** According to Shodan.io, what is the first country in the world in terms of the number of publicly accessible Apache servers?
**Answer:** United States

**Q2.** Based on Shodan.io, what is the 3rd most common port used for Apache?
**Answer:** 8080

**Q3.** Based on Shodan.io, what is the most common port used for nginx?
**Answer:** 80

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



## Notes

**Passive reconnaissance** refers to gathering information from public sources without contacting the target.
**WHOIS** is a query response protocol, listens on TCP port 43 and provides registration details for domain names.

From WHOIS response the following details may available (When not redacted)
- Registrar
- Registrant Contact Information
- Dates (Creation, Updated and Expiration)
- Name Server
- Status Codes
- Abuse Contacts