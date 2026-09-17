
# Nmap: Basics

## Overview

Learn how to use Nmap to discover live hosts, find open ports, and detect service versions.

## What I Learned



## Exercises

### Exercise 1 — [Host Discovery]

**Q1.** What is the last IP address that will be scanned when your scan target is 192.168.0.1/27?
**Answer:** 192.168.0.31

### Exercise 2 — [Port Scanning]

**Q1.** How many TCP ports are open on the target system at 10.48.186.200?
**Answer:** 6

**Q2.** Find the listening web server on 10.48.186.200 and access it with your browser. What is the flag that appears on its main page?
**Answer:** THM{SECRET_PAGE_38B9P6}

### Exercise 3 — [Version Detection]

**Q1.** What is the name and detected version of the web server running on 10.48.186.200?
**Answer:** lighttpd 1.4.74

### Exercise 4 — [Timing]

**Q1.** What is the non-numeric equivalent of -T4?
**Answer:** -T aggressive

### Exercise 5 — [Output Controlling]

**Q1.** What option must you add to your nmap command to enable debugging?
**Answer:** -d

**Q2.** What kind of scan will Nmap use if you run nmap 10.48.186.200 with local user privileges?
**Answe:** Connect Scan

## Key Takeaways

In this room, we learned how to use Nmap to discover live hosts on any network. We also explored the common types of port scans and how we can use Nmap to find service version numbers. We also learned how to control the timing of the scan, and finally, we covered the different formats for saving Nmap scan results.

It is worth noting that it is best to run Nmap with sudo privileges so that we can make use of all its features. Running Nmap with local user privileges will still work; however, you should expect many features to be unavailable. You get a minimal portion of Nmap’s power when running it as a local user. For instance, Nmap would automatically use SYN scan (-sS) if you are running it with sudo privileges and will default to connect scan (-sT) if run as a local user. The reason is that crafting certain packets, such as sending a TCP SYN packet, requires root privileges.

## Notes

**Nmap:** Nmap is an open-source network scanner that was first published in 1997. Since then, plenty of features and options have been added. It is a powerful and flexible network scanner that can be adapted to various scenarios and setups.

IP range using -: If you want to scan all the IP addresses from 192.168.0.1 to 192.168.0.10, you can write 192.168.0.1-10
IP subnet using /: If you want to scan a subnet, you can express it as 192.168.0.1/24, and this would be equivalent to 192.168.0.0-255
Hostname: You can also specify your target by hostname, for example, example.thm

**Connect Scan**
The connect scan can be triggered using -sT. It tries to complete the TCP three-way handshake with every target TCP port. If the TCP port turns out to be open and Nmap connects successfully, Nmap will tear down the established connection.

**SYN Scan (Stealth)**
Unlike the connect scan, which tries to connect to the target TCP port, i.e., complete a three-way handshake, the SYN scan only executes the first step: it sends a TCP SYN packet. Consequently, the TCP three-way handshake is never completed. The advantage is that this is expected to lead to fewer logs as the connection is never established, and hence, it is considered a relatively stealthy scan. You can select the SYN scan using the -sS flag.

**Scanning UDP ports**
Nmap offers the option -sU to scan for services. Because UDP is simpler than TCP, we expect the traffic to differ. The screenshot below shows several ICMP destination unreachable (port unreachable) responses as Nmap sends UDP packets to closed UDP ports.

**Limiting the Target Ports**

Nmap scans the most common 1,000 ports by default. However, this might not be what you are looking for. Therefore, Nmap offers you a few more options.
    -F is for Fast mode, which scans the 100 most common ports (instead of the default 1000).
    -p[range] allows you to specify a range of ports to scan. For example, -p10-1024 scans from port 10 to port 1024, while -p-25 will scan all the ports between 1 and 25. Note that -p- scans all the ports and is equivalent to -p1-65535 and is the best option if you want to be as thorough as possible.
    Tip: The most common services use a port number between 1 and 1024 for either UDP or TCP. These ports are also known as well-known ports. Use -p1-1023 to scan for the well-known ports.

**Service and Version Detection**
You discovered several open ports and want to know what services are listening on them. -sV enables version detection. This is very convenient for gathering more information about your target with fewer keystrokes. The terminal output below shows an additional column called “VERSION”, indicating the detected SSH server version.

**Forcing the Scan**
When we run our port scan, such as using -sS, there is a possibility that the target host does not reply during the host discovery phase (e.g. a host doesn’t reply to ICMP requests). Consequently, Nmap will mark this host as down and won’t launch a port scan against it. We can ask Nmap to treat all hosts as online and port scan every host, including those that didn’t respond during the host discovery phase. This choice can be triggered by adding the -Pn option.

Running your scan at its normal speed might trigger an or other security solutions. It is reasonable to control how fast a scan should go. Nmap gives you six timing templates, and the names say it all: paranoid (0), sneaky (1), polite (2), normal (3), aggressive (4), and insane (5). You can pick the timing template by its name or number. For example, you can add -T0 (or -T 0) or -T paranoid to opt for the slowest timing.