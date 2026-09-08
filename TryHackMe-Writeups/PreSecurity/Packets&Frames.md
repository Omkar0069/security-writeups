# What are Packets and Frames?

## Overview

Understand how data is divided into smaller pieces and transmitted across a network to another device.

## What I Learned

- Frames
- Packets
- Ports
- TCP/IP
- UDP/IP

## Exercises

### Exercise 1 — [Introduction]

**Q1.** What is the name for a piece of data when it does have IP addressing information?
**Answer:** Packet

**Q2.** What is the name for a piece of data when it does not have IP addressing information?
**Answer:** Frame

### Exercise 2 — [TCP/IP]

**Q1.** What is the header in a TCP packet that ensures the integrity of data?
**Answer:** Checksum

**Q2.** Provide the order of a normal Three-way handshake (with each step separated by a comma)
**Answer:** SYN,SYN/ACK,ACK

### Exercise 3 — [UDP/IP]
**Q1.** What does the term "UDP" stand for?
**Answer:** User Datagram Protocol

**Q2.** What type of connection is "UDP"?
**Answer:** Stateless

**Q3.** What protocol would you use to transfer a file?
**Answer:** TCP

**Q4.** What protocol would you use to have a video call?
**Answer:** UDP

### Exercise 4 — [DHCP]

**Q1.** What type of DHCP packet is used by a device to retrieve an IP address?
**Answer:** DHCP Discover

**Q2.** What type of DHCP packet does a device send once it has been offered an IP address by the DHCP server?
**Answer:** DHCP Request
Finally, what is the last DHCP packet that is sent to a device from a DHCP server?
**Answer:** DHCP ACK

## Key Takeaways

-

## Notes

**Packets** - A Packet is a piece from layer 3 of OSI model containing information such as payload and IP header
**Frames** - Frames however work at level 2 which encapsulates the packets and adds additional information such as mac address

**Step	Message 	Description**
1	    SYN	        A SYN message is the initial packet sent by a client during the handshake. This packet is used to initiate a connection and synchronise the two devices together (we'll explain this further later on).
2	    SYN/ACK	    This packet is sent by the receiving device (server) to acknowledge the synchronisation attempt from the client.
3	    ACK     	The acknowledgement packet can be used by either the client or server to acknowledge that a series of messages/packets have been successfully received.
4	    DATA    	Once a connection has been established, data (such as bytes of a file) is sent via the "DATA" message.
5   	FIN	        This packet is used to cleanly (properly) close the connection after it has been complete.
-	    RST     	This packet abruptly ends all communication. This is the last resort and indicates there was some problem during the process. For example, if the service or application is not working correctly, or the system has faults such as low resources. 