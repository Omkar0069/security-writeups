# Shells & Listeners Fundamentals

## Overview

Learn how to create, stabilise, and secure reverse and bind shells for penetration testing.

## What I Learned

- Reverse vs bind shells
- Netcat and socat
- Shell stabilisation
- Encrypted shells

## Exercises

### Exercise 1 — [Reverse vs Bind Shells]

**Q1.** Which type of shell connects back to a listening port on your computer, Reverse (R) or Bind (B)?
**Answer:** R

**Q2.** When using a bind shell, would you execute a listener on the Attacker (A) or the Target (T)?
**Answer:** T

**Q3.** A target machine sits behind a strict firewall that blocks all inbound connections but allows outbound traffic. Which shell type would work here, Reverse (R) or Bind (B)?
**Answer:** R

### Exercise 2 — [Tools for Remote Shells]

**Q1.** YWhich tool can allocate pseudo-terminals (PTYs) for fully interactive shell sessions?
**Answer:** socat

**Q2.** Which Metasploit component generates payloads in formats such as executables, scripts, and shellcode?
**Answer:** msfvenom

### Exercise 3 — [Working with Netcat]

**Q1.** Which option tells netcat to listen?
**Answer:** -l

**Q2.** How would you connect to a bind shell on the IP address: 10.10.10.11 with port 8090?
**Answer:** nc 10.10.10.11 8090

**Q3.** Which netcat flag skips DNS resolution and uses numeric IP addresses only?
**Answer:** -n

### Exercise 4 — [Working with Socat]

**Q1.** How would we get socat to listen on TCP port 8080?
**Answer:** TCP-L:8080

**Q2.** When creating a socat reverse shell on a Windows target, which option must you add after the executable name for proper I/O handling?
**Answer:** pipes

### Exercise 5 — [Shell Stabilisation]

**Q1.** After running stty raw -echo, what command brings your backgrounded shell back to the foreground?
**Answer:** Repeater

**Q2.** How would you change your terminal size to have 238 columns?
**Answer:** stty cols 238

**Q3.** What command would you use to set up a Python3 web server on port 80 to transfer socat to a target? (Provide the full command with sudo)
**Answer:** sudo python3 -m http.server 80

### Exercise 6 — [Encrypted Shells]

**Q1.** Which socat parameter disables certificate verification for self-signed certificates?
**Answer:** verify=0

**Q2.** What OpenSSL flag generates a 2048-bit RSA key pair when creating a self-signed certificate?
**Answer:** -newkey rsa:2048

## Key Takeaways

You can now catch, stabilise, and encrypt remote shells on both Linux and Windows targets.

## Notes

A reverse shell occurs when the target (the compromised machine) initiates an outbound connection to your listener; this is often effective when a firewall blocks inbound connections to the target.
A bind shell is when the target opens a listening port and waits for you to connect; this removes the need to accept inbound traffic, but the target's firewall may block it.

Reverse shells work best when:

- The target can make outbound connections
- Firewalls block inbound connections to the target
- The target is behind NAT without port forwarding
- You want to control the listening port on your own machine

Bind shells work best when:

- Outbound connections from the target are heavily restricted 
- You cannot accept inbound connections on your machine
- The target has accessible ports 
- You need multiple people to access the same shell

Tools for Remote Shells:

Netcat (nc) is the Swiss Army knife of networking tools and your first choice for quick shell connections. Think of it as a simple pipe that can either listen for incoming connections or reach out to connect to another system. When someone connects, netcat passes data back and forth between the network socket and your terminal.

Rlwrap (readline wrapper) solves one of netcat's biggest annoyances: the lack of command history and line editing features. Raw Netcat shells don't respond to arrow keys, don't remember previous commands, and don't support tab completion. Rlwrap wraps around Netcat to add these missing readline features.

Socat (SOcket CAT) does everything netcat does, plus a lot more. Where netcat just passes raw bytes between two endpoints, socat can manipulate the data flow, allocate terminals, and encrypt connections.

Msfvenom and Metasploit's multi/handler provide enterprise-grade capabilities for payload generation and handling. Msfvenom generates payloads in various formats (executables, scripts, shellcode) for different platforms, while multi/handler provides a sophisticated listener that understands advanced payload protocols.