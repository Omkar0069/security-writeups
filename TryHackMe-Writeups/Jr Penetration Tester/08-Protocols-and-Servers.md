# Protocols and Servers

## Overview

Learn about common protocols such as HTTP, FTP, POP3, SMTP and IMAP, along with related insecurities.

## What I Learned

- This room covered several protocols, their usage, and how they work under the hood. Many other standard protocols are of interest to attackers. For instance, Server Message Block (SMB) provides shared access to files and printers between networks, and it can be an attractive target. However, this room intended only to provide a solid understanding of a few common protocols and how they operate at a low level.

## Exercises

### Exercise 1 — [Telnet]

**Q1.** To which port will the telnet command with the default parameters try to connect?
**Answer:** 23

### Exercise 2 — [FTP]

**Q1.** Using an FTP client, connect to the VM and try to recover the flag file. What is the flag?

    Username: frank
    Password: D2xc9CgD
**Answer:** THM{364db6ad0e3ddfe7bf0b1870fb06fbdf}

### Exercise 3 — [SMTP]

**Q1.** Using the AttackBox terminal, connect to the SMTP port of the target VM. What is the flag that you can get?
**Answer:** THM{5b31ddfc0c11d81eba776e983c35e9b5}

### Exercise 4 — [Post Office Protocol 3 (POP3)]

**Q1.** Connect to the VM (10.48.150.190) at the POP3 port. Authenticate using the username frank and password D2xc9CgD. What is the response you get to STAT?
**Answer:** +OK 0 0

**Q2.** How many email messages are available to download via POP3 on 10.48.150.190?
**Answer:** 0

### Exercise 5 — [IMAP]

**Q1.** What is the default port used by IMAP?
**Answer:** 143

## Key Takeaways

Every protocol covered in this room transmits data in cleartext by default, including authentication credentials. This is the central security lesson: if traffic is not encrypted, anyone with network access can capture usernames, passwords, email content, and file transfers.

The Telnet client, while not used as a server protocol on modern systems, remains a practical testing tool for manually interacting with any text-based protocol on any TCP port. This technique was used throughout the room to demonstrate HTTP, FTP, SMTP, POP3, and IMAP at the protocol level.

For every cleartext protocol, a secure alternative exists. Modern deployments should use encrypted variants (HTTPS, SFTP, IMAPS, SSH) to protect data in transit. 

## Notes

Reasons to learn this protocols:
1. This protocols still in use.
2. You will encounter cleartext protocol during penetration testing and security assessment.
3. Understanding this protocol help you understand the attacks better.

**Telnet** The Telnet protocol is an application-layer protocol used to connect to a virtual terminal of another computer. Using Telnet, a user can log into a remote machine and access its terminal (console) to run programs, start batch processes, and perform system administration tasks remotely.
**FTP** File Transfer Protocol (FTP) was developed to make the transfer of files between different computers with different systems efficient. It was one of the earliest protocols designed for the internet and remains in use today, though it has largely been replaced by secure alternatives for most purposes.
**SMTP** Simple Mail Transfer Protocol (SMTP) is used to communicate with an MTA server. The original SMTP uses cleartext, where all commands are sent without encryption.
**POP3** Post Office Protocol version 3 (POP3) is a protocol used to download email messages from a Mail Delivery Agent (MDA) server, as shown in the figure below. The mail client connects to the POP3 server, authenticates, downloads the new email messages, and then (optionally) deletes them from the server.
**IMAP** Internet Message Access Protocol (IMAP) is more sophisticated than POP3. IMAP makes it possible to keep email synchronised across multiple devices (and mail clients). If you mark an email message as read when checking your email on your smartphone, the change is saved on the IMAP server (MDA) and replicated on your laptop when you synchronise your inbox.