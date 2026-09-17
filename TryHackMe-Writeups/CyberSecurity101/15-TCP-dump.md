
# Tcpdump: Basics

## Overview

Learn how to use Tcpdump to save, filter, and display packets.

## What I Learned

- Tcpdump and it's use

## Exercises

### Exercise 1 — [Introduction]

**Q1.** What is the name of the library that is associated with tcpdump?
**Answer:** libpcap

### Exercise 2 — [Packet Dissection]

**Q1.** How many packets in traffic.pcap use the ICMP protocol?
**Answer:** 26

**Q2.** What is the IP address of the host that asked for the MAC address of 192.168.124.137?
**Answer:** 192.168.124.148

**Q3.** What hostname (subdomain) appears in the first DNS query?
**Answer:** mirrors.rockylinux.org

### Exercise 3 — [Packet Navigation]

**Q1.** How many packets have only the TCP Reset (RST) flag set?
**Answer:** 57

**Q2.**  What is the IP address of the host that sent packets larger than 15000 bytes?
**Answer:** 185.117.80.53 (tcpdump -r traffic.pcap "len > 15000" -c 5 -n)

### Exercise 4 — [Packet Filtering]

**Q1.** What is the MAC address of the host that sent an ARP request?
**Answer:** 52:54:00:7c:d3:5b

### Exercise 5 — [SMTPS,POP3S and IMAPS]

**Q1.** What would you use to connect the various company sites so that users at a remote office can access resources located within the main branch?
**Answer:** VPN

## Key Takeaways

In this room, we have covered various Tcpdump options. Along with Wireshark and Tshark, Tcpdump is an excellent tool for better understanding networking protocols. We kept this room’s level easy; however, we showed much of Tcpdump’s power, especially when you have to sift through thousands and millions of packets.

## Notes

**tcpdump is a command-line network packet analyzer used to capture, inspect, and troubleshoot network traffic on a system. It allows administrators, security analysts, and developers to see packets flowing through network interfaces in real time.**

**Specify the network interface:** Use -i flag to specify the network interface e.g., sudo tcpdump -i eth0 You can use -i any to listen on all available interface.
**Save the capture packets:** Use -s filename to save packets to any file directly without dumping everything into termial. The file extension is commonly set to .pcap. The saved packets can later be analyze using another program like wireshark.
**Read the captured packets from file:** You can use tcpdump to read captured packets to read packets from file. For this we use -r flag.
**Limit the number of packets:** You can use the number of packets to capture by specifying the count using -c count. Without specifying a count, the packet will continue capturing till you interupt it. 


**Filtering by Host**
Let’s say you are only interested in IP packets exchanged with your network printer or a specific game server. You can easily limit the captured packets to this host using host IP or host HOSTNAME. In the terminal below, we capture all the packets exchanged with example.com and save them to http.pcap. It is important to note that capturing packets requires you to be logged-in as root or to use sudo.
If you want to limit the packets to those from a particular source IP address or hostname, you must use src host IP or src host HOSTNAME. Similarly, you can limit packets to those sent to a specific destination using dst host IP or dst host HOSTNAME.

**Filtering by Protocol**
The final type of filtering we will cover is filtering by protocol. You can limit your packet capture to a specific protocol; examples include: ip, ip6, udp, tcp, and icmp.

**Logical Operators**
Three logical operators that can be handy:
    and: Captures packets where both conditions are true. For example, tcpdump host 1.1.1.1 and tcp captures tcp traffic with host 1.1.1.1.
    or: Captures packets when either one of the conditions is true. For instance, tcpdump udp or icmp captures or ICMP traffic.
    not: Captures packets when the condition is not true. For example, tcpdump not tcp captures all packets except segments; we expect to find UDP, ICMP, and ARP packets among the results.

**Tcpdump is a rich program with many options to customize how the packets are printed and displayed. We have selected to cover the following five options:**
    -q: Quick output; print brief packet information
    -e: Print the link-level header
    -A: Show packet data in ASCII
    -xx: Show packet data in hexadecimal format, referred to as hex
    -X: Show packet headers and data in hex and ASCII
