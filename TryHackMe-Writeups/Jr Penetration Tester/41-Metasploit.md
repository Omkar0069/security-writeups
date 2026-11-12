# Metasploit: The Basics

## Overview

Navigate msfconsole, search for modules, configure exploits, and manage sessions on target systems.

## What I Learned

- Understand the building blocks
- Find the right module
- Configure and launch
- Manage your sessions

## Exercises

### Exercise 1 — [Core Concepts and Module Types]

**Q1.** What is the name of the code that takes advantage of a flaw on the target system?
**Answer:** Exploit

**Q2.** What is the name of the code that runs on the target system after a successful exploit?
**Answer:** Payload

**Q3.** What type of payload is self-contained and does not require a second download?
**Answer:** Singles

**Q3.** What symbol in a payload's path name indicates it is a staged payload?
**Answer:** /

### Exercise 2 — [Navigating Msfconsole]

**Q1.** How would you search for all exploit modules related to Apache?
**Answer:** search type:exploit apache

**Q2.** You found an interesting module in your search results listed as index number 3. What command would you use to view detailed information about it?
**Answer:** info 3

**Q3.** What command would you use to go back from a module's context to the main msf6 > prompt?
**Answer:** back

### Exercise 3 — [Configuration and Running Modules]

**Q1.** How would you set the LPORT value to 6666?
**Answer:** set LPORT 6666

**Q2.** How would you set the global value for RHOSTS to 10.10.19.23?
**Answer:** setg RHOSTS 10.10.19.23

**Q3.** What command would you use to clear a set payload?
**Answer:** unset PAYLOAD

**Q4.** What command do you use to launch an exploit module?
**Answer:** exploit

**Q5.** You want to exploit a target but continue working in msfconsole immediately after the session opens. What flag do you add to the exploit command?
**Answer:** -z

### Exercise 4 — [Managing Sessions]

**Q1.** What command do you use to background a Meterpreter session and return to the msfconsole prompt?
**Answer:** background

**Q2.** What flag do you use with the sessions command to interact with a specific session by ID?
**Answer:** -i

**Q3.** You have three active sessions. You need to terminate session 2 without affecting the others. What full command do you use?
**Answer:** sessions -k 2

## Key Takeaways

In this room, we covered the foundations of the Metasploit Framework.

## Notes

What is the Metasploit Framework?

The Metasploit Framework is the most widely used open-source exploitation framework in the penetration testing industry. Originally created by H.D. Moore in 2003 as a portable networking tool, Metasploit was acquired by Rapid7 in 2009 and has grown into an ecosystem containing over 2,600 exploits and more than 6,100 modules in total. Metasploit supports the full penetration testing lifecycle: information gathering, vulnerability identification, exploitation, post-exploitation, reporting

The Three Pillars of the Framework:

- Msfconsole
- Modules: There are seven categories of modules (exploits, auxiliary, payloads, post-exploitation, encoders, NOPs, and evasion)
- Tools

**Vulnerability:** A design, coding, or configuration flaw in a target system. The flaw itselff does not cause harm; it creates an opportunity for harm. A vulnerability might allow an attacker to execute arbitary code, read files they should not have access to, or bypass authentication entirely.
**Exploit:** A piece of code that takes advantage of a specific vulnerability. The exploit is the mechanism of attack. It targets the flaw and triggers it in a controlled way.
**Payload:** The code that runs on the target system after the exploit succees. The exploit opens the door; the payload is what walks through it. A payload might open a reverse shell back to the attacker, create a new user account, or execute a command on the target.

**The Seven Module Categories:**

**Expoits** modules target a specific vulnerability on a specific platform. They are organized by target operating system and service (e.g., exploits/windows/smb/, exploits/linux/http/). 

**Auxillary** modules handle everything that is not direct exploitation. This includes port scanners, service fingerprinters, brute-force login modules, fuzzers, and network sniffers. If you need to gather information about a target system or teset credentials without delivering an exploit, you are looking for an auxillary module.

**Payloads** Payload modules contain the code that executes on the target after a successful exploit.

**Post-Exploitation** modules run after you have already gained access to a target through an active session. They automates common post-exploitation tasks

**Encoders** modules transform payload data into a different format.

**NOPs** (No Operation) modules generate NOP sleds, sequences of instructions that do nothing. 0x90 which tells the CPU to skip to the next instruction.

**Evasion** modules are purpose-built attempts to bypass specific security controls, such as Windows Defender or AppLocker.

**Payload Types**

**Singles** (also called inline payloads) are self-contained. The entire payload is delivered in a single package. A single payload might add a user account, execute a system command, or open a bind shell.

**Stagers** are small, lightweight payloads whose only job is to establish a communication channel between the attacker and the target. Once connected, the stager downloads the second component.

**Stages** are the larger payload components downloaded by a stager. Together, a stager and its stage form a staged payload. The advantage is a smalled initial footprint; the disadvantage is that the connection must remain stable long enought for the stage to download.