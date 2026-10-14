# Content Discovery

## Overview

Discover hidden web content using manual techniques, OSINT, and Gobuster enumeration.

## What I Learned

Manual - robots.txt, sitemap.xml, favicon fingerprinting, HTTP headers, framework stack
OSINT - Google dorking, Wappalyzer, Wayback Machine, GitHub, S3 buckets
Automated - Gobuster dir, dns, and vhost modes

## Exercises

### Exercise 1 — [Manual Discover - Common Files]

**Q1.** What is the directory in robots.txt that isn't allowed to be viewed by web crawlers?
**Answer:** /staff-portal

**Q2.** What is the path of the secret area found in sitemap.xml?
**Answer:** /s3cr3t-area

### Exercise 2 — [Manual Discovery - Hewaders & Framework Stack]

**Q1.** What is the flag value from the X-FLAG header?
**Answer:** THM{HEADER_FLAG}

**Q2.** What is the flag from the framework's administration portal?
**Answer:** THM{CHANGE_DEFAULT_CREDENTIALS}

### Exercise 3 — [OSINT - Search Engines & Web Tools]

**Q1.** What Google dork operator limits results to a specific site?
**Answer:** site:

**Q2.** What online tool and browser extension identifies what technologies a website is running?
**Answer:** wappalyzer

### Exercise 4 — [OSINT - Repositories & Archives]

**Q1.** What is the website address for the Wayback Machine?
**Answer:**https://web.archive.org/

**Q2.** What URL format do Amazon S3 buckets end in? (Answer starts with a .)
**Answer:** .s3.amazonaws.com

### Exercise 5 — [Automated Discovery - Gobuster Fundamentals]

**Q1.** What is the name of the directory beginning with /mo that was discovered?
**Answer:** /monthly

**Q2.** What is the name of the log file that was discovered?
**Answer:** /development.log

### Exercise 6 — [Automated Discovery - Subdomains & Virtual Hosts]

**Q1.** Apart from dns and -w, which shorthand flag is required for dns mode?
**Answer:** -d

**Q2.** How many virtual hosts on acmeitsupport.thm respond with status code 200?
**Answer:** 3

## Key Takeaways

Content discovery is one of the msot important phases of web application reconnaissance. The techniques in this room work together: manual checks surface quick wins, OSINT finds information the target has already shared publicly, and automated tools cover the breadth that neither approach can do alone.

## Notes

Content Discovery is the process of finding the content that wasn't meant to me publically accessible or meant to be linked anywhere obivous.

robots.txt - robots.txt file tells the search engine crawlers which pages they may index. Site owners often list sensitive directories here to prevent them from appearing in search results, making it a ready-made list of interesting locations for a penetration tester.

sitemap.xml - unlick robots.txt (which restricts crawlers), sitemap.xml tells search engines which pages the owner wants listed. These files sometimes include staging pages, old content, or URLs that are hard to reach via the normal site.

HTTP Headers - When a web server responds to a request, it includes HTTP headers that can reveal useful technical details. Headers like Server and X-Powered-By often expose the web server software and the language or framework the applicatioin runs on.

There are also external resources available that can help in discovering information about your target website; these resources are often referred to as OSINT (Open-Source Intellegence), as they're freely available tools that collect information:
    Google Hacking/Dorking
