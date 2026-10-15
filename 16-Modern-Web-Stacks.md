# Modern Web Stacks

## Overview

Four web stacks, four CVEs: fingerprint MERN, Next.js, Django, and LAMP, then exploit each one.

## What I Learned

- Fingerprinted four stacks and exploited four CVEs using the same three-step workflow every time: read the signals, confirm the version, execute the chain.

## Exercises

### Exercise 1 — [MERN Stack]

**Q1.** What HTTP response header confirms an Express.js backend is running? (Answer Format: Header-Name: Value)
**Answer:** X-Powered-By: Express

**Q2.** What is the name of the Express session cookie you will use to replay requests after polluting the prototype? (Answer Format: cookie-name)
**Answer:** Connect-sid

**Q3.** Send the prototype pollution payload to the merge endpoint. What is the flag returned by the admin route after the bypass succeeds?
**Answer:** THM{pr0t0_p0llut3d}

### Exercise 2 — [React/Next.js]

**Q1.** What HTML artifact in the page source confirms a Next.js App Router application?
**Answer:** window.__next_f

**Q2.** Send the CVE-2025-29927 bypass header to the protected /dashboard route. What flag is displayed on the page? (Answer Format: THM{...})
**Answer:** THM{m1ddl3w4r3_byp4ss3d}

### Exercise 3 — [DJANGO]

**Q1.** What hidden form field in Django POST forms is a near-certain stack fingerprint? 
**Answer:** csrfmiddlewaretoken

**Q2.** Using manual curl payloads, what is the name of the vulnerable database?
**Answer:** vuln_db

### Exercise 4 — [LAMP]

**Q1.** What exact Server header value identifies this target as vulnerable to CVE-2021-41773? (Answer Format: Apache/X.X.XX (OS)
**Answer:** APACHE/2.4.49 (Unix)

**Q2.** What curl flag is required to prevent curl from normalising the traversal sequences in the URL before sending?
**Answer:** --path-as-is

**Q3.** What are the contents of the flag.txt file?
**Answer:** THM{4p4ch3_p4th_tr4v3rs4l}

## Key Takeaways

Every stack leaks its identity. Once you can read those signals, you stop guessing and start targeting. That is the shift this room was built to provide you with. As a penetration tester, the focus should always be on understanding why a vulnerability exists before reaching for an exploit. Every signal you read, every header you inspect, and every version you confirm brings you closer to a targeted, evidence-driven attack chain rather than a noisy scanner run.

## Notes

**Webstack** - A web stack refers to the collection of technologies used to build and run a web application. Typically, it includes the front-end technologies (like HTML, CSS, and JavaScript), back-end technologies (such as server-side languages like Python, Ruby, or Node.js), databases (like MySQL or MongoDB), and server environments (like Apache or Nginx).

**CVE** stands for Common Vulnerabilities and Exposures. It is a public, standardized identifier assigned to a specific security vulnerability or exposure in software or hardware. Each CVE entry gives a unique ID, a brief description of the vulnerability, and references to technical details and advisories so security teams can unambiguously discuss, track, and remediate the issue.

MERN apps are the default choice for JavaScript-only shops that want one language across the full stack. On Ubuntu, the typical deployment is Node.js from the NodeSource PPA, Express listening on port 3000 or 5000, and MongoDB on port 27017. A reverse proxy (usually Nginx) sits in front in production, but in misconfigured environments and internal tools, the Express process is often directly exposed.

Express is the foundation of the MERN stack we just exploited. Next.js builds on top of it, adding abstractions like the App Router, React Server Components, and middleware that create a different and more severe attack surface.

Django powers a large share of Python-backed web applications. On Ubuntu, it runs under Gunicorn or Django's built-in development server, typically on port 8000. The Django admin panel at /admin/ and CSRF middleware are enabled by default in virtually every Django project. The admin panel alone is a reliable stack signal before you send a single exploit payload.

On Ubuntu, Apache usually runs under www-data, serves files from /var/www/html, and passes dynamic requests to PHP through mod_php or PHP-FPM. MySQL stores the application data, while PHP handles server-side logic. This classic Linux, Apache, MySQL, and PHP combination creates common attack surfaces such as exposed PHP files, database errors, weak file permissions, and misconfigured Apache/PHP settings.

Manual fingerprinting teaches you what signals matter and why. When you are working through a scope with many hosts, Nikto gives you a quick first pass; it probes each service, reads response headers, and surfaces stack signals and known misconfigurations without you writing a single payload.