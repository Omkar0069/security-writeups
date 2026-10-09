# Protocols and Servers 2

## Overview

Learn about attacks against passwords and cleartext traffic; explore options for mitigation via SSH and SSL/TLS.

## What I Learned

- This room examined three common attacks against network protocols:
    Sniffing Attack
    MITM Attack
    Password Attack

## Exercises

### Exercise 1 — [Sniffing Attacks]

**Q1.** What do you need to add to the command sudo tcpdump to capture only Telnet traffic?
**Answer:** port 23

**Q2.** What is the simplest display filter you can use with Wireshark to show only IMAP traffic?
**Answer:** imap

### Exercise 2 — [MITM]

**Q1.** How many different interfaces does Ettercap offer?
**Answer:** 3

**Q2.** In how many ways can you invoke Bettercap?
**Answer:** 3

### Exercise 3 — [TLS]

**Q1.** DNS can also be secured using TLS. What is the three-letter acronym of the DNS protocol that uses TLS?
**Answer:** DoT

### Exercise 4 — [SSH]

**Q1.** Use SSH to connect to 10.48.186.132 as mark with the password XBtc49AB. Using uname -r, find the Kernel release?
**Answer:** 5.15.0-119-generic

**Q2.** Use SSH to download the file book.txt from the remote system. How many KBs did scp display as download size?
**Answer:** 415

### Exercise 5 — [Password Attack]

**Q1.** We learned that one of the email accounts is lazie. What is the password used to access the IMAP service on 10.48.186.132?
**Answer:** butterfly

## Key Takeaways

The central theme of this room is that cleartext protocols are inherently insecure. Any protocol that transmits data without encryption is vulnerable to sniffing and MITM attacks. The solution is to use encrypted alternatives:

    Use HTTPS instead of HTTP.
    Use SSH instead of Telnet.
    Use SFTP or FTPS instead of FTP.
    Use IMAPS/POP3S/SMTPS instead of their cleartext counterparts.

Even with encryption, password-based authentication remains a weak point. Strong passwords, account lockout policies, rate limiting, and multi-factor authentication are essential defences. Where possible, passwordless authentication using passkeys or certificate-based authentication provides stronger security.

## Notes

**An attack aims to cause Disclosure, Alteration, and Destruction (DAD).**

**Sniffing Attack:** A sniffing attack refers to using a network packet capture tool to collect information about the target. When a protocol communicates in cleartext, the data exchanged can be captured by a third party to analyse. A simple network packet capture can reveal information such as the content of private messages and login credentials if the data is not encrypted in transit.

**MITM Attack:** A Man-in-the-Middle (MITM) attack occurs when a victim (A) believes they are communicating with a legitimate destination (B) but is unknowingly communicating with an attacker (E). In the figure below, A requests the transfer of $20 to M. However, E alters this message and replaces the original value with a new one. B receives the modified message and acts on it.

**TLS:** SSL (Secure Sockets Layer) originated when the World Wide Web began to see new applications, such as online shopping and sending payment information. Netscape introduced SSL in 1994, with SSL 3.0 being released in 1996. Eventually, more security was needed, and the TLS (Transport Layer Security) protocol was introduced in 1999 with TLS 1.0.

**SSH:** Secure Shell (SSH) was created to provide a secure way for remote system administration. It allows you to securely connect to another system over the network and execute commands on the remote system. The "S" in SSH stands for secure.


**Authentication, or proving your identity, can be achieved through one of the following, or a combination of two or more:**

    Something you know, such as a password or PIN code.
    Something you have, such as a phone, security key, or smart card.
    Something you are, such as a fingerprint or facial recognition.
