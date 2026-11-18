# Shells & Listeners Fundamentals

## Overview

Generate, customise, and deploy shell payloads with msfvenom, Metasploit, and webshells

## What I Learned

- Combined with the shell-catching and stabilisation techniques from the Shells & Listeners Fundamentals room, we now have the full picture from listener setup to stable foothold. The natural next step is privilege escalation, covered in the Linux Privilege Escalation and Windows Privilege Escalation rooms in the TryHackMe Jr Penetration Tester learning path.

## Exercises

### Exercise 1 — [Common Shell Payloads]

**Q1.** What technique allows you to create a reverse or bind shell with netcat when the -e flag is unavailable?
**Answer:** named pipe

**Q2.** In the PowerShell reverse shell one-liner, what .NET class is used to create the network connection to the attacker?
**Answer:** System.Net.Sockets.TCPClient

**Q3.** What bash pseudo-device path is used to create a TCP connection in the bash reverse shell?
**Answer:** /dev/tcp

### Exercise 2 — [msfvenom]

**Q1.** Which msfvenom payload would generate a 64-bit Linux stageless reverse TCP shell?
**Answer:** linux/x64/shell_reverse_tcp

**Q2.** What msfvenom flag specifies the number of encoding iterations?
**Answer:** -i

**Q3.** What type of msfvenom payload runs entirely in memory and provides built-in post-exploitation commands?
**Answer:** meterpreter

### Exercise 3 — [Metasploit multi/handler]

**Q1.** What Metasploit command loads the multi/handler module?
**Answer:** use multi/handler

**Q2.** What flag runs the handler as a background job so you can continue using the Metasploit console?
**Answer:** -j

**Q3.** Which command, followed by a session number, lets you interact with a specific active session?
**Answer:** sessions -i

### Exercise 4 — [Webshells]

**Q1.** What PHP function is used in the basic webshell to execute system commands?
**Answer:** shell_exec

**Q2.** What HTTP method helps avoid logging commands in web server access logs?
**Answer:** POST

**Q3.** What is the name of the well-known PHP reverse shell script included in Kali's webshell collection, written by PentestMonkey?
**Answer:** php-reverse-shell.php

### Exercise 5 — [Practical Exercises: Linux]

**Q1.** What msfvenom format flag generates a Linux ELF binary?
**Answer:** -f elf

**Q2.**What Metasploit output confirms the staged payload two-phase handshake is working?
**Answer:** Sending stage

### Exercise 6 — [Practical Exercises: Windows]

**Q1.** What Meterpreter command displays information about the compromised system, including OS and hostname?
**Answer:** sysinfo

## Key Takeaways

msfvenom handles binary generation for any platform and format. Multi/handler catches staged payloads and manages Meterpreter sessions. Webshells get code execution when the only path in is an HTTP upload. And once we have that first shell, credential hunting and account creation move us from an unstable foothold to something we can actually work with.

## Notes

Script-Based Shells - Many systems have scripting languages installed by default, and we can use them to create shells when traditional tools are missing. This is particularly useful when we have code executionthrough web applications, scheduled tasks, or other non-interactive methods. Python, Perl, Ruby and PHP all have networking capabilites that can open a socket and spawn a shell. The two most commonly useful options on linux targets are python and bash itself

**Payload Selection Strategy**

- Target operating system
- Available interpreters
- Network restrictions
- Execution context
- Detection concerns

**Msfvenom:**
Nanual payload creation works for many scenarios, but real engagements often need payloads that evade detection, taget different platforms, or plug into post-exploitation frameworks.Msfvenom, part of the Metasploit framework, automates all of this. It handles encoding, output formatting, and platform targeting that would take ages to do by hand.

Msfvenom is a payload generator and encoder. It creates executable code that establishes a shell connection, either connecting back to our attacking machine for reverse shells or opening a listening port for us to connect to for bind shells. Unlike the manual shell commands from previous tasks, msfvenom produces complete, standalone payloads we can deliver through email attachments, web uploads, or exploit frameworks.

**Basic msfvenom Syntax:**
attacker@tryhackme:~$ msfvenom -p <payload> LHOST=<ip> LPORT=<port> -f <format> -o <output>    

Output Formats and Use Cases

Msfvenom supports numerous output formats, each suited to different delivery methods and target environments. The right format depends on how we plan to execute the payload on the target.
- exe
- elf
- dll
- aspx
- jsp
- war
- python
- powershell

**Metasploit multi/handler**
Simple netcat listener work fine for basic shells, but they can't handle the staging protocol that staged payloads and Meterpreter sessions rely on. That's where Metasploit's multi/handler comes in. It knows how to receive stagers, send back the full payload, manage multiple sesions at once, and do things a plan netcat listener simply can't.

"A webshell is a script written in a server-side language (PHP,ASP,JSP,Python) that accepts commands through HTTP requests and runs them on the hosting server. We submit commands via URL parameters, POST data, or form fields, and the script executes them with the web server's privileges. The output comes back as HTML.

