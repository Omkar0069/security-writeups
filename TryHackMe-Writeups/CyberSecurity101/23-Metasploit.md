# Metasploit: Introduction

## Overview

An introduction to the main components of the Metasploit Framework. 

## What I Learned

- Basic of Metasploit

## Exercises

### Exercise 1 — [Components]

**Q1.** What is the name of the code taking advantage of a flaw on the target system?
**Answer:** Exploit

**Q2.** What is the name of the code that runs on the target system to achieve the attacker's goal?
**Answer:** Payload

**Q3.** What are self-contained payloads called?
**Answer:** Singles

### Exercise 2 — [Msfconsole]

**Q1.** How would you search for a module related to Apache?
**Answer:** search apache

**Q3.** Who provided the auxiliary/scanner/ssh/ssh_login module?
**Answer:** todb

### Exercise 3 — [Navigation]

**Q1.** How would you set the LPORT value to 6666?
**Answer:** set lport 6666

**Q2.** How would you set the global value for RHOSTS  to 10.10.19.23 ?
**Answer:**  setg rhosts 10.10.19.23

**Q3.** What command would you use to clear a set payload?
**Answer:** unset PAYLOAD

**Q4.** What command do you use to proceed with the exploitation phase?
**Answer:** exploit

## Key Takeaways

The exploitation process comprises three main steps; finding the exploit, customizing the exploit, and exploiting the vulnerable service.

Metasploit provides many modules that you can use for each step of the exploitation process. Through this room, we have seen the basic components of Metasploit and their respective use.

## Notes

 Metasploit is the most widely used exploitation framework. Metasploit is a powerful tool that can support all phases of a penetration testing engagement, from information gathering to post-exploitation.


Metasploit has two main versions:

    Metasploit Pro: The commercial version that facilitates the automation and management of tasks. This version has a graphical user interface (GUI).
    Metasploit Framework: The open-source version that works from the command line. This room will focus on this version, installed on the AttackBox and most commonly used penetration testing linux distributions.


The Metasploit Framework is a set of tools that allow information gathering, scanning, exploitation, exploit development, post-exploitation, and more. While the primary usage of the Metasploit Framework focuses on the penetration testing domain, it is also useful for vulnerability research and exploit development.

The main components of the Metasploit Framework can be summarized as follows;

    msfconsole: The main command-line interface.
    Modules: supporting modules such as exploits, scanners, payloads, etc.
    Tools: Stand-alone tools that will help vulnerability research,vulnerablility, or penetration testing. Some of these tools are msfvenom, pattern_create and pattern_offset. We will cover msfvenom within this module, but pattern_create and pattern_offset are tools useful in exploit development which is beyond the scope of this module. 

**Exploit:** A piece of code that uses a vulnerability present on the target system.
**Vulnerability:** A design, coding, or logic flaw affecting the target system. The exploitation of a vulnerability can result in disclosing confidential information or allowing the attacker to execute code on the target system.
**Payload:** An exploit will take advantage of a vulnerability. However, if we want the exploit to have the result we want (gaining access to the target system, read confidential information, etc.), we need to use a payload. Payloads are the code that will run on the target system.

**Modules and categories**

**Auxiliary** Any supporting module, such as scanners, crawlers and fuzzers, can be found here. 

**Encoders** Encoders will allow you to encode the exploit and payload in the hope that a signature-based antivirus solution may miss them.
Signature-based antivirus and security solutions have a database of known threats. They detect threats by comparing suspicious files to this database and raise an alert if there is a match. Thus encoders can have a limited success rate as antivirus solutions can perform additional checks. 

**Evasion** While encoders will encode the payload, they should not be considered a direct attempt to evade antivirus software. On the other hand, “evasion” modules will try that, with more or less success.

**Exploits** Exploits, neatly organized by target system.

**NOPs** NOPs (No OPeration) do nothing, literally. They are represented in the Intel x86 CPU family with 0x90, following which the CPU will do nothing for one cycle. They are often used as a buffer to achieve consistent payload sizes.

**Payloads** Payloads are codes that will run on the target system.
Exploits will leverage a vulnerability on the target system, but to achieve the desired result, we will need a payload. Examples could be; getting a shell, loading a malware or backdoor to the target system, running a command, or launching calc.exe as a proof of concept to add to the penetration test report. Starting the calculator on the target system remotely by launching the calc.exe application is a benign way to show that we can run commands on the target system.
Running command on the target system is already an important step but having an interactive connection that allows you to type commands that will be executed on the target system is better. Such an interactive command line is called a "shell". Metasploit offers the ability to send different payloads that can open shells on the target system. 
Types includes: Adapter, Singles, Stagers, Stages
**Post** Post modules will be useful on the final stage of the penetration testing process listed above, post-exploitation.

All parameters are set using the same command syntax:
set PARAMETER_NAME VALUE