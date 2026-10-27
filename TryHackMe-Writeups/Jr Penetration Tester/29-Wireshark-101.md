# Wireshark 101

## Overview

Learn the basics of Wireshark and how to analyze various protocols and PCAPs

## Notes

Wireshark, a tool used for creating and analyzing PCAPs (network packet capture files), is commonly used as one of the best packet analysis tools.

**Wireshark Collection Methods:**

**Network Taps:** Network taps are a physical implant in which you physically tap between a cable, these techniques are commonly used by Threat Hunting/DFIR teams and red teams in an engagement to sniff and capture packets.

**MAC Floods** MAC Floods are a tactic commonly used by red teams as a way of actively sniffing packets. MAC Flooding is intended to stress the switch and fill the CAM table. Once the CAM table is filled the switch will no longer accept new MAC addressees and so in order to keep the network alive, the switch will send out packets to all ports of the switch.

**ARP Poisioning** ARP Poisioning is another technique used by red teams to actively sniff packets. By ARP Poisioning you can redirect the traffic from the host(s) to the machine you're monitoring from. This technique will not stress network equipment like MAC Flooding however should still be used with caution and only if other techniques like network taps are unavailable.


**Filtering Captures** 
**Filtering Operators:** Wireshark's filter syntax can be simple to understand making it easy to get a hold of quickly. To get the most of these filters you need to have a basic understanding of boolean and logic operators.

and - operator: and / &&
or - operator: or / ||
equals - operator: eq / ==
not equal - operator: ne / !=
greater than - operator: gt /  >
less than - operator: lt / <

**Basic Filtering:**
Filtering gives us a very large scope of what we can do with the packets, because of this there can be a lot of different filtering syntax options. 
ip.addr == <ip address>
ip.src == <source ip>
ip.dst == <destination ip>
tcp.port eq <port> or <protocol name>
udp.port eq <port> or <protocol name>

**7 Layers of the OSI Model**
- Application: End user layer; HTTP, FTP, IRC, SSH, DNS
- Presentation: Syntax layer: SSL, SSH IMAP, FTP, MPEG, JPEG
- Session: Synch & send to port; API's, Sockets, WinSock
- Transport: End-to-end connections; TCP, UDP
- Network: Packets; IP, ICMP, IPSec, IGMP
- Data link: Frames; Ethernet, PPP, Switch, Bridge
- Physical: Physical structure; Coax, Fiber, Wireless, Hubs, Repeaters

**ARP** or Address Resolution Protocol is a Layer 2 protocol that is used to connect OP Addresses with MAC Addresses. They will contain REQUEST messages and RESPONSE messages. To identify packets the message header will contain one of two operation codes:
    - Request(1)
    - Reply(2)

The Opcode is short for operation code and will tell you wheather it is an ARP Request or Reply. 

**ICMP** ICMP or Internet Control Message Protocol is used to analyze various nodes on a network. This is most commonly used with utilities like ping and traceroute.

There are two other details within the packet that are useful to analyze: timestamp and data. The timestamp can be useful for identifying the time the ping was requested it can also be useful to identify suspicious activity in some cases. We can also look at the data string which will typically just be a random data string.

**TCP** TCP or Transmission Control Protocol handles the delivery of packets including sequencing and errors.
The main thing we want to look for when looking at a TCP packet is the sequence number and acknowlegment number.
    - The acknowlegdement number is not set in a TCP SYN packet because the client is not acknowleging any data from the server. It is typically 0 in the initial SYN packet.

**DNS** DNS or Domain Name Service protocol is used to resolves names with IP addresses. Just like the other protocols, you should be familiar with DNS.

**HTTP** or Hypertext Transfer Protocol is a commonly used port for the world wide web and used by some websites, however, its encrypted counterpart: HTTPS is more common which we will discuss in the next text. HTTP is used to send GET and POST requests to a web server in order to receive things like webpages. Knowing how to analyze HTTP can be useful to quickly spot things like SQLi, Web Shells, and other web-related attack vectors.