# Gobuster: The Basics

## Overview

This room focuses on an introduction to Gobuster, an offensive security tool used for enumeration.

## What I Learned

- Gobuster Basics

## Exercises

### Exercise 1 — [Introduction]

**Q1.** What flag do we use to specify the target URL?
**Answer:** -u

**Q2.** What command do we use for the subdomain enumeration mode?
**Answer:** dns

### Exercise 2 — [Directory and File Enumeration]

**Q1.** Which flag do we have to add to our command to skip the TLS verification? Enter the long flag notation.
**Answer:** --no-tls-validation

**Q2.** Enumerate the directories of www.offensivetools.thm. Which directory catches your attention?
**Answer:** secret

**Q3.** Continue enumerating the directory found in question 2. You will find an interesting file there with a .js extension. What is the flag found in this file?
**Answer:** THM{ReconWasASuccess}

### Exercise 3 — [Subdomain Enumeration]

**Q1.** Apart from the dns keyword and the -w flag, which shorthand flag is required for the command to work?
**Answer:** -d

**Q2.** Use the commands learned in this task, how many subdomains are configured for the offensivetools.thm domain?
**Answer:** 4

### Exercise 4 — [Vhost Enumeration]

**Q1.** Use the commands learned in this task to answer the following question: How many vhosts on the offensivetools.thm domain reply with a status code 200?
**Answer:** 4

## Key Takeaways

Understanding the basics of enumeration
How to use Gobuster to enumerate web directories and files
How to use Gobuster to enumerate subdomains
How to use Gobuster to enumerate virtual hosts
How to use a wordlist

## Notes

Gobuster is an open-source offensive tool written in Golang. It enumerates web directories, DNS subdomains, vhosts, Amazon S3 buckets, and Google Cloud Storage by brute force, using specific wordlists and handling the incoming responses. Many security professionals use this tool for penetration testing, bug bounty hunting, and cyber security assessments. Looking at the phases of ethical hacking, we can place Gobuster between the reconnaissance and scanning phases.

Enumeration - Enumeration is the act of accessing all the available resources weather they are accessible or not. For example, Gobuster enumerates web directories.

Brute Force - Brute Force is the act of trying every possiblity until a match is found

**Some useful flag:**
**-t or --threads** This flag configures the number of threads to use for the scan. Each of these threads sends out requests with a slight delay. The default number of threads is 10. This number may be slow when using large wordlists. You can increase or decrease the number of threads depending on the available system resources.
**-w or --wordlist** The flag configures a wordlist to use for iterating. Each wordlist entry is attached to the URL you included in the command.
**--delay** This flag defines the amount of time to wait between sending requests. Some web servers include mechanisms to detect enumeration by looking at how many requests are received in a certain period of time. We can increase the delay between subsequent requests to make it look like normal web traffic.
**--debug** This flag helps us to troubleshoot when our command gives unexpected errors.
**-o or --output** This flag writes the enumeration results to a file we choose.

dir: gobuster dir -u "http://www.example.thm" -w /path/to/wordlist
dns: gobuster dns -d example.thm -w /path/to/wordlist
vhost: gobuster vhost -u "http://example.thm" -w /path/to/wordlist
