# Nmap Advanced Port Scan

## Overview

Learn advanced scanning and spoofing techniques covering null, FIN, Xmas, and idle scans.

## What I Learned

- Nmap Advanced Port Scan (Didn't understood much)

## Exercises

### Exercise 1 — [TCP Null Scan, FIN Scan and XMAS Scan]

**Q1.** In a null scan, how many flags are set to 1?
**Answer:** 0

**Q2.** In a FIN scan, how many flags are set to 1?
**Answer:** 1

**Q3.** In a Xmas scan, how many flags are set to 1?
**Answer:** 3

**Q4.** Launch a FIN scan against the target VM. How many ports appear as open|filtered?
**Answer:** 9

**Q5.** Repeat your scan launching a null scan against the target VM. How many ports appear as open|filtered?
**Answer:** 9

### Exercise 2 — [TCP Maimon Scan]

**Q1.** In the Maimon scan, how many flags are set?
**Answer:** 2

### Exercise 3 — [TCP/ACK Windows, and Custom Scan]

**Q1.** In TCP Window scan, how many flags are set?
**Answer:** 1

**Q2.** You decided to experiment with a custom TCP scan that has the reset flag set. What would you add after --scanflags?
**Answer:** RST

**Q3.** Launch an ACK scan against the target VM with the firewall enabled. How many ports appear unfiltered?
**Answer:** 5

**Q4.** What is the new port number that appeared? To determine the new port you need to compare the scan results of Task 2 to the ones of this task.
**Answer:** 443

**Q5.** Is there any service behind the newly discovered port number? (yea/nay)
**Answer:** yea

### Exercise 4 — [Spoofing and Decoys]

**Q1.** What do you need to add to the command sudo nmap 10.49.163.100 to make the scan appear as if coming from the source IP address 10.10.10.11 instead of your IP address?
**Answer:** -S 10.10.10.11

**Q2.** What do you need to add to the command sudo nmap 10.49.163.100 to make the scan appear as if coming from the source IP addresses 10.10.20.21 and 10.10.20.28 in addition to your IP address?
**Answer:** -D 10.10.20.21,10.10.20.28,ME

### Exercise 5 — [Fragmented Packets]

**Q1.** If the TCP segment has a size of 64, and the -ff option is being used, how many IP fragments will you get?
**Answer:** 4

### Exercise 6 — [Idle/Zombie Scan]

**Q1.** You discovered a rarely-used network printer with the IP address 10.10.5.5, and you decide to use it as a zombie in your idle scan. What argument should you add to your Nmap command?
**Answer:** -sI 10.10.5.5

### Exercise 7 — [Getting More Detail]

**Q1.** Use Nmap with nmap -sS -F --reason 10.49.163.100 to scan the VM. What is the reason provided for the stated port(s) being open?
**Answer:** syn-ack

## Key Takeaways

These scan types rely on setting TCP flags in unexpected ways to prompt ports for a reply. Null, FIN, and Xmas scans provoke a response from closed ports, while Maimon, ACK, and Window scans provoke a response from open and closed ports.

## Notes

**NULL Scan:** The null scan does not set any flag; all six flag bits are set to zero. You can choose this scan using the -sN option. A TCP packet with no flags set will not trigger any response when it reaches an open port, as shown in the figure below. Therefore, from Nmap’s perspective, a lack of reply in a null scan indicates that either the port is open or a firewall is blocking the packet.

**FIN Scan:** The FIN scan sends a TCP packet with the FIN flag set. You can choose this scan type using the -sF option. Similarly, no response will be sent if the TCP port is open. Again, Nmap cannot be sure whether the port is open or whether a firewall is blocking traffic on this TCP port.

**Xmas Scan:** The Xmas scan gets its name from the Christmas tree lights. An Xmas scan sets the FIN, PSH, and URG flags simultaneously. You can select the Xmas scan with the option -sX.

**Maimon Scan:** Uriel Maimon first described this scan in 1996. In this scan, the FIN and ACK bits are set. The target should send an RST packet as a response. However, certain BSD-derived systems drop the packet if it is an open port exposing the open ports. This scan won’t work on most targets encountered in modern networks; however, we include it in this room to better understand the port scanning mechanism and the hacking mindset. To select this scan type, use the -sM option.

**TCP ACK Scan:** Let’s start with the TCP ACK scan. As the name implies, an ACK scan will send a TCP packet with the ACK flag set. Use the -sA  option to choose this scan. As shown in the figure below, the target would respond to the ACK with RST regardless of the port's state. This behaviour occurs because a TCP packet with the ACK flag set should be sent only in response to a received TCP packet to acknowledge receipt of data, unlike in our case. Hence, this scan won’t tell us whether the target port is open in a simple setup.

**Windows Scan:** Another similar scan is the TCP window scan. The TCP window scan is almost identical to the ACK scan; however, it examines the TCP Window field of the RST packets returned. On specific systems, this can reveal that the port is open. You can select this scan type with the option -sW. As shown in the figure below, we expect to get an RST packet in reply to our “uninvited” ACK packets, regardless of whether the port is open or closed.

**Custom Scans:** If you want to experiment with a new TCP flag combination beyond the built-in TCP scan types, you can do so using --scanflags. For instance, if you want to set SYN, RST, and FIN simultaneously, you can do so using --scanflags RSTSYNFIN.

**FIREWALL:** A firewall is a piece of software or hardware that either permits or blocks packets. It functions based on firewall rules, summarised as blocking all traffic with exceptions or allowing all traffic with exceptions. For instance, you might block all traffic to your server except that coming to your web server. A traditional firewall inspects at least the IP and transport layer headers. A more sophisticated firewall would also try to examine the data carried by the transport layer.

**IDS:** An Intrusion Detection System (IDS) inspects network packets for select behavioural patterns or specific content signatures. It raises an alert whenever a malicious rule is met. In addition to the IP and transport layer headers, an IDS would inspect the transport layer data and check whether it matches any malicious patterns. How can you make it less likely for a traditional firewall/IDS to detect your Nmap activity? It is not easy to answer this; however, depending on the type of firewall/IDS, you might benefit from dividing the packet into smaller packets.

**Fragments:** Nmap provides the option -f to fragment packets. Once chosen, the IP data will be divided into 8 bytes or fewer. Adding another -f (-f -f or -ff) will split the data into 16 byte-fragments instead of 8. You can change the default value by using the --mtu; however, you should always choose a multiple of 8.