# DNS in Detail

## Overview

Learn how DNS works and how it helps you access internet services.

## What I Learned

- DNS
- Top Level Domain
- Second Level Domain
- DNS Record Types

## Exercises

### Exercise 1 — [Domain Hierarchy]

**Q1.** What is the maximum length of a subdomain?
**Answer:** 63

**Q2.** Which of the following characters cannot be used in a subdomain ( 3 b _ - )?
**Answer:** _

**Q3.** What is the maximum length of a domain name?
**Answer:** 253

**Q4.** What type of TLD is .co.uk?
**Answer:** ccTLD

### Exercise 2 — [Record Types]
**Q1.** What type of record would be used to advise where to send email?
**Answer:** MX

**Q2.** What type of record handles IPv6 addresses?
**Answer:** AAAA

### Exercise 3 — [Making request]

**Q1.** What type of DNS Server is usually provided by your ISP?
**Answer:** Recursive

**Q2.** What type of server holds all the records for a domain?
**Answer:** Authoritative


## Key Takeaways

DNS converts IP addresses into names which are easy to remember.

## Notes

**DNS** - Domain Name System converts the IP Addresses into name which is easy to remember by the user.
**Top Level Domain** - There are two types of TLD, gTLD (generic Top Level Domain) and ccTLD (country code Top Level Domain), gTLD is used to tell the user domains purpose for e.g., .com for commercial, .edu for education and ccTLD is used for geographical purposes, .in for India.
**Second Level Domain** - Taking tryhackme.com for example, .com is TLD while tryhackme is the Second Level Domain.The Second Level Domain is limited to 63 characters + the TLD and can only use a-z,0-9 and hypens(cannot start or end with hypen or have consecutive hyphen)
**SubDomain** - A subdomain sits on the left-hand side of the Second-Level Domain using a period to separate it; for example, in the name admin.tryhackme.com the admin part is the subdomain. It has same creation restriction.

**DNS record Types:** DNS isn't for just website though, and multiple types of record exist.
A - This record resolve to IPv4 addresses
AAAA - This record resolve to IPv6 addresses
CNAME - This record resolve to another domain name, for e.g., THM's online shop has subdomain name store.tryhackme.com which returns CNAME record shops.shopify.com. Another domain request will be made to shops.shopify.com to work the ip address.
MX Record - This record resolve the address of the servers that handles the email for the domain you are querying.
TXT Records - TXT Records are where any text based data can be stored.It has multiple uses, but the most common ones is to list the server that has the authority to send an email on behalf of the domain.