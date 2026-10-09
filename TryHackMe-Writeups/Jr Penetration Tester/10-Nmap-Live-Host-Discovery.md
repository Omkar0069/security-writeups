# Nmap Live Host Discovery

## Overview

Learn how to use Nmap to discover live hosts using ARP, ICMP, and TCP/UDP ping scan.

## What I Learned

- How ARP, ICMP, TCP, and UDP can detect live hosts

## Exercises

### Exercise 1 — [Subnets]

**Q1.** How many devices can see the ARP Request?
**Answer:** 4

**Q2.** Did computer6 receive the ARP Request? (yea/nay)
**Answer:** nay

**Q3.** How many devices can see the ARP Request?
**Answer:** 4

**Q4.** Did computer6 receive the ARP Request? (yea/nay)
**Answer:** yea

### Exercise 2 — [Host Discovery through TCP/IP]

**Q1.** Send a packet with the following:
From computer1
To computer3
Packet Type: “Ping Request”
What type of packet did computer1 send before the ping?
**Answer:** ARP Request

**Q2.** What type of packet did computer1 receive before it was able to send the ping?
**Answer:** ARP Response

**Q3.** How many computers responded to the ping request?
**Answer:** 1

**Q4.** Send a packet with the following:
From computer2
To computer5
Packet Type: “Ping Request”
What is the name of the first device that responded to the first ARP Request?
**Answer:** router

**Q5.** What is the name of the first device that responded to the second ARP Request?
**Answer:** computer5

**Q6.** Send another Ping Request. Did it require new ARP Requests? (yea/nay)
**Answer:** nay

### Exercise 3 — [Enumerating Targets]

**Q1.** What is the first IP address Nmap would scan if you provided 10.10.12.13/29 as your target?
**Answer:** 10.10.12.8

**Q2.** How many IP addresses will Nmap scan if you provide the following range: 10.10.0-255.101-125?
**Answer:** 6400

### Exercise 4 — [Host Discovery through ARP]

**Q1.** How many hosts are found alive after scanning the CONNECTION_IP/24?
**Answer:** 1

### Exercise 5 — [Host Discovery through ICMP]

**Q1.** What is the option required to tell Nmap to use ICMP Timestamp to discover live hosts?
**Answer:** -PP

**Q2.** What is the option required to tell Nmap to use ICMP Address Mask to discover live hosts?
**Answer:** -PM

**Q3.** What is the option required to tell Nmap to use ICMP Echo to discover live hosts?
**Answer:** -PE

### Exercise 6 — [Host Discovery USING TCP AND UDP]

**Q1.** Which TCP ping scan requires a privileged account?
**Answer:** TCP ACK ping

**Q2.** What option do you need to add to Nmap to run a TCP SYN ping scan on the telnet port?
**Answer:** -PS23

**Q3.** Which TCP ping scan does not require a privileged account?
**Answer:** TCP SYN ping

### Exercise 7 — [Using Reverse DNS-lookup]

**Q1.** We want Nmap to issue a reverse DNS lookup for all the possible hosts on a subnet, hoping to get some insights from the names. What option should we add?
**Answer:** -R

## Key Takeaways

Scan Type 	                 Example Command
ARP Scan 	            sudo nmap -PR -sn 10.200.6.0/24
ICMP Echo Scan 	        sudo nmap -PE -sn 10.200.6.0/24
ICMP Timestamp Scan 	sudo nmap -PP -sn 10.200.6.0/24
ICMP Address Mask Scan 	sudo nmap -PM -sn 10.200.6.0/24
TCP SYN Ping Scan   	sudo nmap -PS22,80,443 -sn 10.200.6.0/30
TCP ACK Ping Scan   	sudo nmap -PA22,80,443 -sn 10.200.6.0/30
UDP Ping Scan 	        sudo nmap -PU53,161,162 -sn 10.200.6.0/30

## Notes

Nmap, short for Network Mapper, is free, open-source software released under the GPL license, created by Gordon Lyon (Fyodor), a network security expert and open-source programmer. Nmap is an industry-standard tool for mapping networks, identifying live hosts, and discovering running services. Nmap’s scripting engine can further extend its functionality, from fingerprinting services to exploiting vulnerabilities. A Nmap scan usually goes through the steps shown in the figure below, although many are optional and depend on the command-line arguments you provide.

If you want to check the list of hosts that Nmap will scan, you can use nmap -sL TARGETS. 
If you want to use Nmap to discover online hosts without port-scanning the live systems, you can issue nmap -sn TARGETS. 
To use ICMP echo requests to discover live hosts, add the option -PE option. (Remember to add -sn if you don’t want to follow that with a port scan.)