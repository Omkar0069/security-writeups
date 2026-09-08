# What is Networking?

## Overview

Begin learning the fundamentals of computer networking in this bite-sized and interactive module.

## What I Learned

- Internet
- IP addresses and it's type and mac addresses
- Ping

## Exercises

### Exercise 1 — [Internet]

**Q1.** Who invented the World Wide Web?
**Answer:** Tim Berners-Lee

### Exercise 2 — [Identifying devices on internet]

**Q1.** What does the term "IP" stand for?
**Answer:** Internet Protocol

**Q2.** What is each section of an IP address called?
**Answer:** Octet

**Q3.** How many sections (in digits) does an IPv4 address have? 
**Answer:** 4

**Q4.** What does the term "MAC" stand for?
**Answer:** Media Access Control

**Q5.** Deploy the interactive lab using the "View Site" button and spoof your MAC address to access the site.  What is the flag?
**Answer:** THM{YOU_GOT_ON_TRYHACKME}

### Exercise 3 — [PING]

**Q1.** What protocol does ping use?
**Answer:** ICMP

**Q2.** What is the syntax to ping 10.10.10.10?
**Answer:** Ping 10.10.10.10

**Q3.** What flag do you get when you ping 8.8.8.8?
**Answer:** THM{I_PINGED_THE_SERVER}

## Key Takeaways

Networks is a group of connected devices.
Each network is connected and idenfied using IP addresses.
To ping or check connection between devices use this command: ping ipaddress

## Notes

**What is Network?**
Network are simply devices connected together it may be from 2 to billions of devices. This devices includes everything from laptop, mobile, tv, fridge etc

**The key term for devices that are connected together - Network**

**Internet -**  Internet is one giant network consist of many small networks within itself. The internet is made up of many small networks called as private networks, where networks connecting this small network is called public network.
 
**IP Addresses:** IP addresses or Internet Protocol Addresses can be used as a way of identifying a host on the network for a particular period of time - it is different for a public address and private addresses, public address is used to identify host on the internet whereas private addresses are used to identify device amongst other devices.
Types of IP addresses:
IPv4 - Supports 2^32 IP addresses (4.29 billion)
IPv6 - Supports 2^128 IP addresses (340 trillion +)

**MAC Addresses:** MAC Addresses are the permenant addresses of the devices comes preinstalled in the factory. It is a 12 character hexadecimal split in 2s seperated by colon. The first six character represents the company while the last six characters represents the device's unique number.

**Ping uses ICMP(Internet Control Message Protocol) packets to determine the performance of connection between devices.**