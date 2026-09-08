# OSI model

## Overview

Learn about the fundamental networking framework that determines the various stages in which data is handled across a network

## What I Learned

- 7 layers of OSI Model

## Exercises

### Exercise 1 — [Introduction]

**Q1.** What does the "OSI" in "OSI Model" stand for?
**Answer:** Open Source Interconnection

**Q2.** How many layers (in digits) does the OSI model have?
**Answer:** 7

**Q3.** What is the key term for when pieces of information get added to data?
**Answer:** Encapsulation

### Exercise 2 — [Layer 1 - Physical]

**Q1.** What is the name of this Layer?
**Answer:** Physical

**Q2.** What is the name of the numbering system that is both 0's and 1's?
**Answer:** Binary

**Q3.** What is the name of the cables that are used to connect devices?
**Answer:** Ethernet

### Exercise 3 — [Layer 2 - Data Link]
**Q1.** What is the name of this Layer?
**Answer:** Data Link

**Q2.** What is the name of the piece of hardware that all networked devices come with?
**Answer:** Network Interface Card

### Exercise 4 — [Layer 3 - Network]

**Q1.** What type of DHCP packet is used by a device to retrieve an IP address?
**Answer:** DHCP Discover

**Q2.** What type of DHCP packet does a device send once it has been offered an IP address by the DHCP server?
**Answer:** DHCP Request

**Q3.** Finally, what is the last DHCP packet that is sent to a device from a DHCP server?
**Answer:** DHCP ACK

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

OSI model is the order how data is sent and received by the user.

## Notes

Layer 1 - Physical: The physical components of the hardware used in the networking and the lowest layer, data transmits in binary numbering system.
Layer 2 - Data Link: Layer 2 focuses on the physical addressing of the transmission. Mac addresses are dealt on this level.
Layer 3 - Network Layer: Routing, decides the most optimal path the data should be sent. IP addresses are dealt in this level.
Layer 4 - Transport: This layer deals with the transmission of data over the networks. TCP and UDP comes in play on this level.
Layer 5 - Session: This layer will create and maintain the connection to the other computer. When a connection is established the session is created, Whilst the connection is active so as the session.
Layer 6 - Presentation: In this layer standardization takes place, this layer act as a translator for data to and from application layer.
Layer 7 - Application: In this layer the protocols and rules are in place to determine how the user should interact with data sent or received.
