# Networking Essentials

## Overview

Explore networking protocols from automatic configuration to routing packets to the destination.

## What I Learned

- DHCP
- ARP
- ICMP
- UDP and TCP
- Encapsulation
- Telnet
- NAT

## Exercises

### Exercise 1 — [DHCP]

**Q1.** How many steps does DHCP use to provide network configuration?
**Answer:** 4

**Q2.** What is the destination IP address that a client uses when it sends a DHCP Discover packet?
**Answer:** 255.255.255.255

**Q3.** What is the source IP address a client uses when trying to get IP network configuration over DHCP?
**Answer:** 0.0.0.0

### Exercise 2 — [ARP]

**Q1.** What is the destination MAC address used in an ARP Request?
**Answer:** ff.ff.ff.ff.ff.ff

**Q2.** In the example above, what is the MAC address of 192.168.66.1?
**Answer:** 44:df:65:d8:fe:6c

### Exercise 3 — [ICMP]

**Q1.** Using the example images above, how many bytes were sent in the echo (ping) request?
**Answer:** 40

**Q2.** Which IP header field does the traceroute command require to become zero?
**Answer:** TTL

### Exercise 4 — [UDP and TCP]

**Q1.** In the network diagram above, what is the public IP that the phone will appear to use when accessing the Internet?
**Answer:** 212.3.4.5

**Q2.** Assuming that the router has infinite processing power, approximately speaking, how many thousand simultaneous TCP connections can it maintain?
**Answer:** 65

### Exercise 5 — [Encapsulation]

**Q1.** On a WiFi, within what will an IP packet be encapsulated?
**Answer:** Frame

**Q2.** What do you call the UDP data unit that encapsulates the application data?
**Answer:** Datagram

**Q3.** What do you call the data unit that encapsulates the application data sent over TCP?
**Answer:** Segment

### Exercise 6 — [Telnet]

**Q1.** Use telnet to connect to the web server on 10.49.182.248. What is the name and version of the HTTP server?
**Answer:** lighttpd/1.4.63

**Q2.** What flag did you get when you viewed the page?
**Answer:** THM{TELNET_MASTER}

## Key Takeaways

This room introduced various protocols that we constantly use directly or indirectly. We have covered ICMP, , , NAT, and routing. Although we use the Internet daily without coming across most of this room’s acronyms, these protocols are the foundation for a functional network.

## Notes

**DHCP:** Dynamic Host Configuration Protocol is a server that allocates ip addresses in the network.
DHCP follows four steps: Discover, Offer, Request and Acknowlege
DHCP Discover: The client broadcasts a DHCPDISCOVER message seeking the local DHCP server if one exists.
DHCP Offer: The server responds with a DHCPOFFER message with an IP address available for the client to accept.
DHCP Request: The client responds with a DHCPREQUEST message to indicate that it has accepted the offered IP.
DHCP Acknowledge: The server responds with a DHCPACK message to confirm that the offered IP address is now assigned to this client.

**ARP:** Address Resolution Protocol (ARP) makes it possible to find the MAC address of another device on the Ethernet. In the example below, a host with the IP address 192.168.66.89 wants to communicate with another system with the IP address 192.168.66.1. It sends an ARP Request asking the host with the IP address 192.168.66.1 to respond. The Request is sent from the MAC address of the requester to the broadcast MAC address, ff:ff:ff:ff:ff:ff as shown in the first packet. The ARP Reply arrived shortly afterwards, and the host with the IP address 192.168.66.1 responded with its MAC address. From this point, the two hosts can exchange data link layer frames.

**ICMP:** Internet Control Message Protocol (ICMP) is mainly used for network diagnostics and error reporting. Two popular commands rely on ICMP, and they are instrumental in network troubleshooting and network security.

**NAT:** The idea behind NAT lies in using one public IP address to provide Internet access to many private IP addresses. In other words, if you are connecting a company with twenty computers, you can provide Internet access to all twenty computers by using a single public IP address instead of twenty public IP addresses. (Note: Technically speaking, the number of IP addresses is always expressed as a power of two. To be technically accurate, with NAT, you reserve two public IP addresses instead of thirty-two. Consequently, you would have saved thirty public IP addresses.)