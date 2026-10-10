# Nmap Post Port Scan

## Overview

Learn how to leverage Nmap for service and OS detection, use Nmap Scripting Engine (NSE), and save the results.

## What I Learned

- 

## Exercises

### Exercise 1 — [Service Detection]

**Q1.** What is the detected version for port 143?
**Answer:** Dovecot imapd
Which service did not have a version detected with --version-light? 
**Answer:** rpcbind

### Exercise 2 — [OS Detection and Traceroute]

**Q1.** Per nmap, which one is the closest OS match after running with the nmap with -O option against 10.49.184.99? (Windows/Linux)
**Answer:** Linux

### Exercise 3 — [NSE]

**Q1.** Knowing that Nmap scripts are saved in /usr/share/nmap/scripts on the AttackBox. What does the script http-robots.txt check for?
**Answer:** disallowed entries

**Q2.** Can you figure out the name for the script that checks for the remote code execution vulnerability MS15-034 (CVE-2015-1635)?
**Answer:** http-vuln-cve2015-1635

**Q3.** On the AttackBox, run Nmap with the default scripts -sC against 10.49.184.99. You will notice that a page is hosted on port 80. What is the http-title value?
**Answer:** Welcome to nginx on Debian!

**Q4.** Based on its description, the script ssh2-enum-algos “reports the number of algorithms (for encryption, compression, etc.) that the target SSH2 server offers.” What is the name of the server host key algorithm that relies on SHA2-512 and is supported by 10.49.184.99?
**Answer:** rsa-sha2-512

### Exercise 4 — [Spoofing and Decoys]

**Q1.** What parameter is used to save the output in a greppable format? Write with a dash (-).
**Answer:** -oG

**Q2.** Is it possible to save Nmap output in XML format (yea/nay)?
**Answer:** yea

## Key Takeaways

In this room, we learned how to detect running services, their versions, and the host operating system. We learned how to enable traceroute and how to select one or more scripts to aid in penetration testing. Finally, we covered the different formats for saving scan results for future reference.

## Notes

A script is a piece of code that does not need to be compiled. In other words, it remains in its original human-readable form and does not need to be converted to machine language. Many programs provide additional functionality via scripts; moreover, scripts enable adding custom functionality that was not available via built-in commands. Similarly, Nmap supports scripts written in Lua. A part of Nmap, the Nmap Scripting Engine (NSE) is a Lua interpreter that allows Nmap to execute Nmap scripts written in Lua. However, we don’t need to learn Lua to make use of Nmap scripts.

**Script Category 	                Description**
auth 	                        Runs authentication-related scripts
broadcast 	                    Discovers hosts by sending broadcast messages
brute 	                        Performs brute-force password auditing against logins
default 	                    Runs default scripts (same as -sC)
discovery 	                    Retrieves accessible information, such as database tables and DNS names
dos 	                        Detects servers vulnerable to Denial of Service (DoS)
exploit 	                    Attempts to exploit various vulnerable services
external 	                    Checks using a third-party service, such as Geoplugin and Virustotal
fuzzer 	                        Launches fuzzing attacks
intrusive 	                    Runs intrusive scripts such as brute-force attacks and exploitation
malware 	                    Scans for backdoors
safe 	                        Runs safe scripts that won't crash the target
version 	                    Retrieves service versions
vuln 	                        Checks for vulnerabilities or exploits in a vulnerable service