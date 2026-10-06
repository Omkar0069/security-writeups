# Active Reconnaissance

## Overview

Learn how to use simple tools such as traceroute, ping, telnet, and a web browser to gather information.

## What I Learned

- 

## Exercises

### Exercise 1 — [Web Browser]

**Q1.** Browse to the following website and ensure that you have opened your Developer Tools on AttackBox Firefox, or the browser on your computer. Using the Developer Tools, figure out the total number of questions.
**Answer:** 8

### Exercise 2 — [Ping]

**Q1.** Which option would you use to set the size of the data carried by the ICMP echo request?
**Answer:** -s

**Q2.** What is the size of the ICMP header in bytes?
**Answer:** 8

**Q3.** Does MS Windows Firewall block ping by default? (Y/N)
**Answer:** Y

**Q4.** Deploy the VM for this task and using the AttackBox terminal, issue the command ping -c 10 10.49.190.235. How many ping replies did you get back?
**Answer:** 10

### Exercise 3 — [Traceroute]

**Q1.** In Traceroute A, what is the IP address of the last router/hop before reaching tryhackme.com?
**Answer:** 100.92.9.83

**Q2.** In Traceroute B, what is the IP address of the last router/hop before reaching tryhackme.com?
**Answer:** 99.83.89.19

**Q3.** In Traceroute B, how many routers are between the two systems?
**Answer:** 25

### Exercise 4 — [Telnet]

**Q1.** Start the attached VM from Task 3 if it is not already started. On the AttackBox, open the terminal and use the telnet client to connect to the VM on port 80. What is the name of the running server?
**Answer:** Apache

**Q2.** What is the version of the running server (on port 80 of the VM)?
**Answer:** 2.4.61

### Exercise 5 — [Netcat]

**Q1.** Start the VM and open the AttackBox. Once the AttackBox loads, use Netcat to connect to the VM port 21. What is the version of the running server?
**Answer:** 0.17

## Key Takeaways

This room covered five core tools for active reconnaissance. The web browser with Developer Tools reveals server technologies, headers, JavaScript sources, and certificate details. ping confirms whether a target is reachable and provides TTL-based clues about its operating system. traceroute maps the network path between you and the target, revealing intermediate routers and potential filtering points. telnet and netcat connect to individual ports to grab banners and identify running services along with their versions.

## Notes

Active Recon is the process of directly interacting with the target. Active techniques leaves traces in the form of log entries, IDS alert, WAF block and honeypot triggers.

**Ping** - Its sends a small packet(usually ICMP) to listner and wait for the echo if it replies back the host is up.
How ping works: Ping uses the ICMP protocol (Internet Control Message Protocol). It sends an ICMP Echo Request packet (type 8). If the target receives the packet and is permitted to answer, it sends back an ICMP Echo Reply (type 0). This exchange is very lightweight and fast, which is why ping became the standard first check before spending time on more detailed scanning.
