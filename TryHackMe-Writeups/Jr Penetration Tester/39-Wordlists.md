# Introduction to Wordlists

## Overview

Learn to build targeted wordlists using OSINT and apply them in penetration testing.

## What I Learned

- By tailoring our wordlists to the target and keeping them clean, we improve efficiency and success rates when conducting enumeration or password-cracking tasks. Remember that these techniques should always be used responsibly and only against systems we're authorised to test. We can continue practising these skills in other rooms and experiment with additional tools and sources to further sharpen our custom-wordlist workflow.

## Exercises

### Exercise 1 — [Wordlists]

**Q1.** What tool can generate a custom wordlist based on known patterns?
**Answer:** Crunch

### Exercise 2 — [Gathering Information for Custom Wordlist]

**Q1.** After running the CeWL command shown in the task, how many unique email addresses did you scrape?
**Answer:** 4

**Q2.** How many PDF files were you able to find?
**Answer:** 1

**Q3.** How many email addresses (or new emails) were you able to extract from the PDF files?
**Answer:** 4

**Q4.** What is the last username in the users_from_emails.txt file?
**Answer:** security

### Exercise 3 — [Creating and Cleaning Wordlists]

**Q1.** How many words are in words_clean.txt after cleaning up the file?
**Answer:** 161

**Q2.** What is the 10th password in the pass_helios.txt file?
**Answer:** Helios2009!

**Q3.** What flag does sort use to remove duplicate lines?
**Answer:** -u

**Q4.** What crunch template character represents a digit?
**Answer:** %

### Exercise 4 — [Using Your Wordlist]

**Q1.** What HTTP status code does ffuf report for helios/?
**Answer:** 200

**Q2.** What is the username that Hydra discovers?
**Answer:** alex.johnson

**Q3.** What is the flag?
**Answer:** THM{w0rdlists_win_rooms}

## Key Takeaways

Explored what wordlists are, how they're used, and why generic lists often fall short.
Used OSINT techniques, such as harvesting names from social media, WHOIS lookups, and site crawling, to create company-specific lists.
Combined and cleaned our raw lists, then applied filters to remove duplicates, normalise the case, and eliminate noise.
Generated pattern-based passwords with crunch, merged multiple username formats, and prepared clean words_clean.txt, users.txt, and pass_helios.txt files.
Used ffuf to discover hidden directories on the target website and employed Hydra to brute-force the login form using our custom lists.

## Notes

A wordlist is simply a text file where each line contains a potential word, phrase, password, filename or other string. In cybersecurity these lists are used for automated guessing: instead of human trying thousands of possible passwords, a tool feeds each entry from the file into a login form or a search field.

Where are wordlists used?

- Password guessing and cracking
- Service login brute-forcing
- Directory brute-forcing
- Subdomain discovery