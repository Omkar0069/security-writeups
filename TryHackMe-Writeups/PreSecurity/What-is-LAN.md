# What is LAN?

## Overview

Learn about some of the technologies and designs that power private networks

## What I Learned

- Topologies
- Subnetting
- ARP
- DHCP

## Exercises

### Exercise 1 — [Lan Topologies]

**Q1.** What does LAN stand for?
**Answer:** Local Area Network

**Q2.** What is the verb given to the job that Routers perform?
**Answer:** Routing

**Q3.** What device is used to centrally connect multiple devices on the local network and transmit data to the correct location?
**Answer:** Switch

**Q4.** What topology is cost-efficient to set up?
**Answer:** Bus Topology

**Q5.** What topology is expensive to set up and maintain?
**Answer:** Star Topology

**Q6.** Complete the interactive lab attached to this task. What is the flag given at the end?
**Answer:** THM{TOPOLOGY_FLAWS}

### Exercise 2 — [Subnetting]

**Q1.** What is the technical term for dividing a network up into smaller pieces?
**Answer:** Subnetting

**Q2.** How many bits are in a subnet mask?
**Answer:** 32

**Q3.** What is the range of a section (octet) of a subnet mask?
**Answer:** 0-255

**Q4.** What address is used to identify the start of a network?
**Answer:** Network Address

**Q5.** What address is used to identify devices within a network?
**Answer:** Host Address

**Q6.** What is the name used to identify the device responsible for sending data to another network?
**Answer:** Default Gateway

### Exercise 3 — [ARP]
What does ARP stand for?
**Answer:** Address Resolution Protocol

**Q2.** What category of ARP Packet asks a device whether or not it has a specific IP address?
**Answer:** Request

**Q3.** What address is used as a physical identifier for a device on a network?
**Answer:** MAC Address

**Q4.** What address is used as a logical identifier for a device on a network?
**Answer:** IP Address

### Exercise 4 — [DHCP]

**Q1.** What type of DHCP packet is used by a device to retrieve an IP address?
**Answer:** DHCP Discover

**Q2.** What type of DHCP packet does a device send once it has been offered an IP address by the DHCP server?
**Answer:** DHCP Request
Finally, what is the last DHCP packet that is sent to a device from a DHCP server?
**Answer:** DHCP ACK

## Key Takeaways

Topologies, Subnetting, ARP, DHCP are some key components in network system.

## Notes

Star Topology - All devices are individually connected to each other with a central network such as hub or switch.
Bus Topology - All devices are connected through a central cable line which is called backbone
Ring Topology - All devices are connected through each other in a ring pattern which goes only in one direction.
Switch - A dedicated device in a network to aggregate multiple devices.
Router - Connects devices to the internet.

**Subnetting** - It is use to split the network into small, miniature network of itself
Subnet use the ip address in three different way:
- Identify the network address
- Identify the host address
- Identify the Default Gateway

**ARP** - Address Resolution Protocol, allows devices to communicate with each other using mac address and ip address

**DHCP** - Dynamic Host Configuration Protocol, is used to assign IP addresses on the network. DHCP discover, DHCP Offer, DHCP request, DHCP ACK are the key packets used in assigning the ip addresses
