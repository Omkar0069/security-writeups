# Nmap Basic Port Scan

## Overview

Learn in-depth how nmap TCP connect scan, TCP SYN port scan, and UDP port scan work.

## What I Learned

- Nmap basic portscans

## Exercises

### Exercise 1 — [TCP and UDP Ports]

**Q1.** Which service uses UDP port 53 by default?
**Answer:** DNS

**Q2.** Which service uses TCP port 22 by default?
**Answer:** SSH

**Q3.** How many port states does Nmap consider?
**Answer:** 6

**Q4.** Which port state is the most interesting to discover as a pentester?
**Answer:** OPEN

### Exercise 2 — [TCP Flags]

**Q1.** What 3 letters represent the Reset flag?
**Answer:** RST

**Q2.** Which flag needs to be set when you initiate a TCP connection (first packet of TCP 3-way handshake)?
**Answer:** SYN

### Exercise 3 — [TCP Connect Scan]

**Q1.** What is the state of the FTP service running on port 21?
**Answer:** open

**Q2.** What is Nmap’s guess about the service running on port 53?
**Answer:** domain

### Exercise 4 — [TCP SYN Scan]

**Q1.** How many ports are open on the target machine?
**Answer:** 4

**Q2.** After launching a TCP SYN scan, how many SYN-ACK packets are successfully received in AttackBox?
**Answer:** 4

### Exercise 5 — [UDP Scan]

**Q1.** What is the state of port number 161 over UDP in the target machine?
**Answer:** closed

**Q2.** What is the service name according to Nmap on port 161?
**Answer:** snmp

### Exercise 6 — [Fine-Tuning Scope and Performance]

**Q1.** What is the option to scan all the TCP ports between 5000 and 5500?
**Answer:** -p5000-5500

**Q2.** How can you ensure that Nmap will run at least 64 probes in parallel?
**Answer:** --min-parallelism=64

**Q3.** What option would you add to make Nmap very slow and paranoid?
**Answer:** -T0

## Key Takeaways

This room covered three types of scans.
Port Scan Type 	            Example Command
TCP Connect Scan 	    nmap -sT 10.48.166.207
TCP SYN Scan 	        sudo nmap -sS 10.48.166.207
UDP Scan 	            sudo nmap -sU 10.48.166.207

## Notes

-sA Acknowlegde Scan
You can choose to run a TCP connect scan using -sT.
Note that we can use -F to enable fast mode and decrease the number of scanned ports from 1000 to 100 most common ports.
It is worth mentioning that the -r option can also be added to scan the ports in consecutive order instead of random order. This option is useful for testing whether ports open consistently, for instance, when a target boots up.
We can select stealth scan scan type by using the -sS option. (root/sudo previlege)
You can select UDP scan using the -sU option; moreover, you can combine it with another TCP scan.

**These scan types should get you started discovering running TCP and UDP services on a target host.**

**Option 	                    Purpose**
-p- 	                all ports
-p1-1023 	            scan ports 1 to 1023
-F 	                    100 most common ports
-r 	                    scan ports in consecutive order
-T<0-5> 	            -T0 being the slowest and T5 the fastest
--max-rate 50 	        rate <= 50 packets/sec
--min-rate 15 	        rate >= 15 packets/sec
--min-parallelism 100 	at least 100 probes in parallel