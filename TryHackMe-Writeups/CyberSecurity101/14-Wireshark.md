
# Wireshark

## Overview

Learn the basics of Wireshark and how to analyse protocols and PCAPs.

## What I Learned



## Exercises

### Exercise 1 — [Tool Overview]

**Q1.** Use the "Exercise.pcapng" file to answer the questions.
Read the "capture file comments". What is the flag?
**Answer:** TryHackMe_Wireshark_Demo

**Q2.** What is the total number of packets?
**Answer:** 58620

**Q3.** What is the SHA256 hash value of the capture file?
**Answer:** f446de335565fb0b0ee5e5a3266703c778b2f3dfad7efeaeccb2da5641a6d6eb

### Exercise 2 — [Packet Dissection]

**Q1.** Use the "Exercise.pcapng" file to answer the questions. View packet number 38. Which markup language is used under the HTTP protocol?
**Answer:** eXtensible Markup Language

**Q2.** What is the arrival date of the packet? (Answer format: Month/Day/Year)
**Answer:** 05/13/2004

**Q3.** What is the TTL value?
**Answer:** 47

**Q4.** What is the TCP payload size?
**Answer:** 424

**Q5.** What is the e-tag value?
**Answer:** 9a01a-4696-7e354b00

### Exercise 3 — [Packet Navigation]

**Q1.** Use the "Exercise.pcapng" file to answer the questions. Search the "r4w" string in packet details. What is the name of artist 1?
**Answer:** r4w8173

**Q2.** Go to packet 12 and read the packet comments. What is the answer?
**Answer:** 911cd574a42865a956ccde2d04495ebf

**Q3.** There is a ".txt" file inside the capture file. Find the file and read it; what is the alien's name?
**Answer:** PACKETMASTER

**Q4.** Look at the expert info section. What is the number of warnings?
**Answer:** 1636

### Exercise 4 — [Packet Filtering]

**Q1.** Use the "Exercise.pcapng" file to answer the questions.
Go to packet number 4. Right-click on the "Hypertext Transfer Protocol" and apply it as a filter.
Now, look at the filter pane. What is the filter query?
**Answer:** http

**Q2.** What is the number of displayed packets?
**Answer:** 1089

**Q3.** Go to packet number 33790, follow the HTTP stream, and look carefully at the responses.
Looking at the web server's response, what is the total number of artists?
**Answer:** 3

**Q4.** What is the name of the second artist?
**Answer:** Blad3

### Exercise 5 — [SMTPS,POP3S and IMAPS]

**Q1.** What would you use to connect the various company sites so that users at a remote office can access resources located within the main branch?
**Answer:** VPN

## Key Takeaways



## Notes

Wireshark is an open-source, cross platform network packet analyzer tool capable of sniffing and investigating live traffic and inspecting traffic captures (PCAP)
 There are multiple purposes for its use:
    Detecting and troubleshooting network problems, such as network load failure points and congestion.
    Detecting security anomalies, such as rogue hosts, abnormal port usage, and suspicious traffic.
    Investigating and learning protocol details, such as response codes and payload data.

Contains three important panes
    Packet list
    Packet details
    Packet bytes

**Packet Dissection**
Packet dissection is also known as protocol dissection, which investigates packet details by decoding available protocols and fields. Wireshark supports a long list of protocols for dissection, and you can also write your dissection scripts. 
We can see seven distinct layers to the packet: frame/packet,source **[MAC],source [IP]**,protocol,protocol errors, application protocol, and application data. Below we will go over the layers in more detail.

The Frame (Layer 1):This will show you what frame/packet you are looking at and details specific to the Physical layer of the OSI model.
Source [MAC] (Layer 2):This will show you the source and destination MAC Addresses; from the Data Link layer of the OSI model.
Source [IP] (Layer 3):This will show you the source and destination IPv4 Addresses; from the Network layer of the OSI model.
Protocol (Layer 4):This will show you details of the protocol used (TCP/UDP) and source and destination ports; from the Transport layer of the OSI model.
Protocol Errors:This continuation of the 4th layer shows specific segments from TCP that needed to be reassembled.
Application Protocol (Layer 5):This will show details specific to the protocol used, such as HTTP, FTP, SMB and . From the Application layer of the OSI model.
Application Data: This extension of the 5th layer can show the application-specific data.

**Packet Numbers**
Wireshark calculates the number of investigated packets and assigns a unique number for each packet. This helps the analysis process for big captures and makes it easy to go back to a specific point of an event.

**Find Packets**
Apart from packet number, Wireshark can find packets by packet content. You can use the "Edit --> Find Packet" menu to make a search inside the packets for a particular event of interest. This helps analysts and administrators to find specific intrusion patterns or failure traces.

**Mark Packets**
Marking packets is another helpful functionality for analysts. You can find/point to a specific packet for further investigation by marking it. It helps analysts point to an event of interest or export particular packets from the capture. You can use the "Edit" or the "right-click" menu to mark/unmark packets.

**Packet Comments**
Similar to packet marking, commenting is another helpful feature for analysts. You can add comments for particular packets that will help the further investigation or remind and point out important/suspicious points for other layer analysts. Unlike packet marking, the comments can stay within the capture file until the operator removes them.

**Export Packets**
Capture files can contain thousands of packets in a single file. As mentioned earlier, Wireshark is not an IDS, so sometimes, it is necessary to separate specific packages from the file and dig deeper to resolve an incident. This functionality helps analysts share the only suspicious packages (decided scope). Thus redundant information is not included in the analysis process. You can use the "File" menu to export packets.

**Export Objects (Files)**
Wireshark can extract files transferred through the wire. For a security analyst, it is vital to discover shared files and save them for further investigation. Exporting objects are available only for selected protocol's streams (DICOM, HTTP, IMF, SMB and TFTP).

**Time Display Format**
Wireshark lists the packets as they are captured, so investigating the default flow is not always the best option. By default, Wireshark shows the time in "Seconds Since Beginning of Capture", the common usage is using the UTC Time Display Format for a better view. You can use the "View --> Time Display Format" menu to change the time display format.

**Packet Filtering**
Wireshark has a powerful filter engine that helps analysts to narrow down the traffic and focus on the event of interest. Wireshark has two types of filtering approaches: capture and display filters. Capture filters are used for "capturing" only the packets valid for the used filter. Display filters are used for "viewing" the packets valid for the used filter. We will discuss these filters' differences and advanced usage in the next room. Now let's focus on basic usage of the display filters, which will help analysts in the first place.
Filters are specific queries designed for protocols available in Wireshark's official protocol reference. While the filters are only the option to investigate the event of interest, there are two different ways to filter traffic and remove the noise from the capture file. The first one uses queries, and the second uses the right-click menu. Wireshark provides a powerful , and there is a golden rule for analysts who don't want to write queries for basic tasks: "If you can click on it, you can filter and copy it"