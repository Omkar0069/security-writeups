# Web Server Attack 2

## Overview

Attack IIS through fingerprinting, tilde enumeration, WebDAV shell upload, and learn automation.

## What I Learned

- Not much just guided attacks

## Exercises

### Exercise 1 — [ISS Fingerprinting and Enumeration]

**Q1.** What HTTP response header reveals the IIS version?
**Answer:** Server

**Q2.** What is the HTTP response code after executing the PUT request on the /webdav directory?
**Answer:**401

### Exercise 2 — [ISS Tilde (Short Filename) Enumeration]

**Q1.** What character in a URL path triggers the IIS tilde enumeration response difference?
**Answer:** ~

**Q2.** What legacy Windows filename format does the tilde enumeration vulnerability exploit? (Answer Format: X.X)
**Answer:** 8.3

**Q3.** What password is stored in the file discovered through tilde enumeration?
**Answer:** P@ssw0rd!123

### Exercise 3 — [WebDAV Expoitation: Uploading an ASPX Shell]

**Q1.** What HTTP status code confirms a file was successfully created via PUT?
**Answer:** 201

**Q2.** What curl flag is required to authenticate with NTLM when uploading via WebDAV?
**Answer:** --ntlm

### Exercise 4 — [ASPX Webshells]

**Q1.** After triggering the ASPX shell, what user account is returned by the whoami command? (Answer Format: lowercase, e.g., nt authority\system)
**Answer:** iis apppool\defaultapppool

**Q2.** What Windows privilege, visible in whoami /priv output from the reverse shell, enables Potato-style privilege escalation from an IIS shell?
**Answer:** SeImpersonatePrivilege

### Exercise 5 — [IIS Misconfigurations]

**Q1.** Navigate to the /uploads/ directory on the target. What sensitive file extension is visible in the directory listing? (Answer Format: include the dot, e.g., .bak)
**Answer:** .bak

**Q2.** What ASP.NET diagnostic handler URL path should be disabled in production as it can expose session data, cookies, and request history?
**Answer:** trace.axd

### Exercise 6 — [Automations]

**Q1.** What nmap NSE script enumerates allowed HTTP methods on a web server?
**Answer:** http-methods

## Key Takeaways

- IIS fingerprinting establishes the version and feature surface before any active exploitation, because the version determines which CVEs apply and enabled features like WebDAV reveal direct attack paths.
- The 8.3 tilde enumeration technique reveals hidden files and directories that wordlist brute-forcing misses, because the short-name format is predictable even when the full filename is not.
- WebDAV shell upload requires three conditions to be met simultaneously: WebDAV enabled, write permission, and Script Execute permission on the same directory. The PUT-MOVE bypass works because handler mappings apply at request time, not at upload time.
- ASPX web shells run under the Application Pool identity, which by default carries SeImpersonatePrivilege, making Potato-style privilege escalation the natural next step after shell acquisition.
- IIS misconfigurations like directory listing, unauthenticated WebDAV, web.config exposure, and trace.axd being accessible each create exploitable conditions independently, without requiring any CVE.

## Notes

**IIS:** Internet Information Services (IIS) is Microsoft's web server platform built into Windows Server. It hosts websites, web applications, and services such as Exchange OWA, SharePoint, and ADFS. IIS logs HTTP requests in W3C format, recording client IPs, requested URIs, status codes, and user agents.

Web Distributed Authoring and Versioning (WebDAV) is an HTTP extension that adds file management verbs: PUT (upload), DELETE, COPY, MOVE, PROPFIND, and LOCK. Legitimate use cases include SharePoint and web-based file editing tools. When left enabled on a directory with write and script execute permissions, it becomes a direct path to uploading an executable shell.

Misconfiguration 1: Directory Listing Enabled
Misconfiguration 2: HTTP PUT and DELETE Without Authentication
Misconfiguration 3: web.config Exposure
Misconfiguration 4: Verbose Error Messages
Misconfiguration 5: trace.axd Left Enabled
Misconfiguration 6: TRACE Method Enabled
Misconfiguration 7: Application Pool Running as a Privileged Account

**Script 	                    What It Does**
http-methods            Sends an OPTIONS request and parses the Allow: header to list permitted methods
http-webdav-scan 	    Probes for WebDAV support and retrieves the server's DAV headers
http-iis-webdav-vuln 	Tests for IIS WebDAV authentication bypass (CVE-2009-1535, affects IIS 5 and 6)
http-ntlm-info 	        Sends an NTLM authentication request to a given path and extracts target information from the NTLM challenge response.