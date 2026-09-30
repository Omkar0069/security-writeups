# Shell Overview

## Overview

Learn about the different types of shells.

## What I Learned

- Shell Overview and some hands on

## Exercises

### Exercise 1 — [Shell Overview]

**Q1.** What is the command-line interface that allows users to interact with an operating system?
**Answer:** shell

**Q2.** What process involves using a compromised system as a launching pad to attack other machines in the network?
**Answer:** pivoting

**Q3.** What is a common activity attackers perform after obtaining shell access to escalate their privileges?
**Answer:** privilege escalation

### Exercise 2 — [Reverse Shell]

**Q1.** What type of shell allows an attacker to execute commands remotely after the target connects back?
**Answer:** Reverse Shell

**Q2.** What tool is commonly used to set up a listener for a reverse shell?
**Answer:** Netcat

### Exercise 3 — [Bind Shell]

**Q1.** What type of shell opens a specific port on the target for incoming connections from the attacker?
**Answer:** Bind Shell

**Q2.** Listening below which port number requires root access or privileged permissions?
**Answer:** 1024

### Exercise 4 — [Shell Listener]

**Q1.** Which flexible networking tool allows you to create a socket connection between two data sources?
**Answer:** socat

**Q2.** Which command-line utility provides readline-style editing and command history for programs that lack it, enhancing the interaction with a shell listener?
**Answer:** rlwrap

**Q3.** What is the improved version of Netcat distributed with the Nmap project that offers additional features like SSL support for listening to encrypted shells?
**Answer:** ncat

### Exercise 5 — [Shell Payloads]

**Q1.** Which Python module is commonly used for managing shell commands and establishing reverse shell connections in security assessments?
**Answer:** Subprocess

**Q2.** What shell payload method in a common scripting language uses the exec, shell_exec, system, passthru, and popen functions to execute commands remotely through a TCP connection?
**Answer:** php

**Q3.** Which scripting language can use a reverse shell by exporting environment variables and creating a socket connection?
**Answer:** Python

### Exercise 5 — [Web Shell]

**Q1.** What vulnerability type allows attackers to upload a malicious script by failing to restrict file types?
**Answer:** Unrestricted File Upload

**Q2.** What is a malicious script uploaded to a vulnerable web application to gain unauthorized access?
**Answer:** Web Shell

## Key Takeaways

In this room, we learned about Reverse Shells, Bind Shells, and Web Shells, how they are critical for attackers, penetration testers, and defenders, and how to identify them.

Reverse Shells establish a connection from a compromised machine back to an attacker's system. Bind Shells, on the other hand, listen for incoming connections on a compromised machine, and Web Shells offer attackers a unique avenue for exploiting vulnerabilities in web applications.

## Notes

A shell is software that allows a user to interact with an OS. It can be a graphical interface, but it is usually a command-line interface, and this will depend on the operating system running on the target system.

**Remote System Control** Allows the attacker to execute commands or software remotely to the target system.
**Privilige Escalation** If initial access is limited attacker finds other ways to escalate priviliges
**Data Exfiltration** Once attacker have access to execute commands through an obtain shell, they can explore the system to read and copy data from it.
**Persistance and Maintenance Access** Once shell access is obtained attacker can create access through users and credentials or copy backdoor software to maintain access to target system for later usage.
**Post Exploitation Activities** After the initial access attacker can do number of post exploitation activites such as deploying malware, creating hidden account and deleting information.
**Lateral Movement** After the inital access point depending on the attacker's intentions, the obtained shell can be used to hop on other systems on the same network. Also known as pivoting.


**Reverse Shell** sometimes also referred to as "connect back shell", is one of the most popular techinques to gaining access to a system in cyberattacks. The connection initiates from the target system to attacker's machine, which can help avoid detection from network firewall and other security appliances.
 
 **Bind Shell** As the name indicates, a bind shell will bind a port on the compromised system and listen for a connection; when this connection occurs, it exposes the shell session so the attacker can execute commands remotely.
rm -f /tmp/f; mkfifo /tmp/f; cat /tmp/f | bash -i 2>&1 | nc -l 0.0.0.0 8080 > /tmp/f
