# Extending your network

## Overview



## What I Learned



## Exercises

### Exercise 1 — [Introduction]

**Q1.** What is the name of the device that is used to configure port forwarding?
**Answer:** Router

### Exercise 2 — [Firewalls]

**Q1.** What layers of the OSI model do firewalls operate at?
**Answer:** 3&4

**Q2.** What category of firewall inspects the entire connection?
**Answer:** stateful

**Q3.** What category of firewall inspects individual packets?
**Answer:** stateless

### Exercise 3 — [VPN Basics]
**Q1.** What VPN technology only encrypts & provides the authentication of data?
**Answer:** PPP

**Q2.** What VPN technology uses the IP framework?
**Answer:** IPSec

### Exercise 4 — [LAN networking devices]

**Q1.** What is the verb for the action that a router does?
**Answer:** Routing

**Q2.** What are the two different layers of switches? Separate these by a comma I.e.: Layer X,Layer Y
**Answer:** Layer 2, Layer 3

### Exercise 5 — [Layer 4 - Transport]

**Q1.** What is the name of this Layer?
**Answer:** Transport

**Q2.** What does TCP stand for?
**Answer:** Transmission Control Protocol

**Q3.** What does UDP stand for?
**Answer:** User Datagram Protocol

**Q4.** What protocol guarantees the accuracy of data?
**Answer:** TCP

**Q5.** What protocol doesn't care if data is received or not by the other device?
**Answer:** UDP

**Q6.** What protocol would an application such as an email client use?
**Answer:** TCP

**Q7.** What protocol would an application that downloads files use?
**Answer:** TCP

**Q8.** What protocol would an application that streams video use?
**Answer:** UCP

### Exercise 6 — [Layer 5 - Session]

**Q1.** What is the name of this layer?
**Answer:** Session

**Q2.** What is the technical term for when a connection is succesfully established?
**Answer:** Session

### Exercise 7 — [Layer 6 - Presentation]

**Q1.** What is the name of this Layer?
**Answer:** Presentation

**Q2.** What is the main purpose that this Layer acts as?
**Answer:** Translator

### Exercise 8 — [Layer 7 - Application]

**Q1.** What is the name of this Layer?
**Answer:** Application

**Q2.** What is the technical term that is given to the name of the software that users interact with?
**Answer:** Graphical User Interface

## Key Takeaways



## Notes

Port Forwarding is configured at the router of the internet

A firewall is a device within a network responsible for determining what traffic is allowed to enter and exit. Think of a firewall as border security for a network. An administrator can configure a firewall to permit or deny traffic from entering or exiting a network based on numerous factors such as:


    Where the traffic is coming from? (has the firewall been told to accept/deny traffic from a specific network?)
    Where is the traffic going to? (has the firewall been told to accept/deny traffic destined for a specific network?)
    What port is the traffic for? (has the firewall been told to accept/deny traffic destined for port 80 only?)
    What protocol is the traffic using? (has the firewall been told to accept/deny traffic that is TCP,UDP or both?)

A Virtual Private Network (or  for short) is a technology that allows devices on separate networks to communicate securely by creating a dedicated path between each other over the Internet (known as a tunnel). Devices connected within this tunnel form their own private network.

