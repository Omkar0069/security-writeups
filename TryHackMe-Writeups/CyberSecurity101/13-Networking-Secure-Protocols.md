# Networking Secure Protocols

## Overview

Learn how TLS, SSH, and VPN can secure your network traffic.

## What I Learned

- TLS
- SSH
- Some Security Protocols

## Exercises

### Exercise 1 — [TLS]

**Q1.** What is the protocol name that TLS upgraded and built upon?
**Answer:** SSL

**Q2.** Which type of certificates should not be used to confirm the authenticity of a server?
**Answer:** Self-Signed Certificate

### Exercise 2 — [HTTPS]

**Q1.** How many packets did the TLS negotiation and establishment take in the Wireshark HTTPS screenshots above?
**Answer:** 8

**Q2.** What is the number of the packet that contain the GET /login when accessing the website over HTTPS?
**Answer:** 10

### Exercise 3 — [SMTPS, POP3S and IMAPS]

**Q1.** If you capture network traffic, in which of the following protocols can you extract login credentials: SMTPS, POP3S, or IMAP?
**Answer:** IMAP

### Exercise 4 — [SSH]

**Q1.** What is the name of the open-source implementation of the SSH protocol?
**Answer:** OpenSSH

### Exercise 5 — [SMTPS,POP3S and IMAPS]

**Q1.** What would you use to connect the various company sites so that users at a remote office can access resources located within the main branch?
**Answer:** VPN

## Key Takeaways

The first approach is to use TLS, which provides a convenient way to secure many protocols, such as HTTP,SMTP, and POP3. Protocols secured with TLS usually get an S, for Secure, added to their names, such as HTTPS, SMTPS, and POP3S.

The second approach to secure network traffic is to use SSH. Although SSH is mainly used for remote access, it can also transfer files securely and establish secure tunnels. Creating an SSH tunnel is a solid choice if you want to pass the traffic of a plaintext protocol, such as VNC.

The last approach we covered to secure network traffic is using VPN connections. A VPN connection is usually the perfect option for connecting two company branches.

## Notes

In Networking core protocols we learned that the protocol used to browse the web and access email, among others however it does not transfer the data into encrypted format or protect the confidentiality, Intergrity or authenticity anyone could intercept and steal or manipulate the data if not protected securely.

Transport Layer Protocol (TLS) to existing protocols to protect confindentiality, integrity and authenticity. Consequently SMTP, HTTP, POP3 and IMAP becomes SMTPS, HTTPS, POP3S and IMAPS, S stands for Secure.

All the packets are sent in a plaintext and anyone on the network could capture those packets and find the credientials. Netscape communication recognised the need for secure communication on the WWW. They eventually developed SSL(Secure Socket Layer) and released SSL 2.O in 1995 as the first public version. In 1999 the Internet Engineering Task Force (IETF) developed TLS (Transport Layer Security) operating at OSI model transport layer

Certificate: The first step for every server (or client) that needs to identify itself is to get a signed TLS certificate. Generally, the server administrator creates a Certificate Signing Request (CSR) and submits it to a Certificate Authority (); the CA verifies the CSR and issues a digital certificate. Once the (signed) certificate is received, it can be used to identify the server (or the client) to others, who can confirm the validity of the signature. 

The insecure version of default TCP port number shown below
HTTP 80
SMTP 25
POP3 110
IMAP 143

The secure version i.e., TLS, use the following ports
HTTPS 443
SMTPS 465 or 587
POP3S 995
IMAPS 993

Tatu Ylönen developed the secure shell (SSH) protocol and released SSH-1 in 1995 as free ware. The more secure version SSH-2 was released in 1996.
**OpenSSH offers several benefits. We will list a few key points:**
    Secure authentication: Besides password-based authentication, SSH supports public key and two-factor authentication.
    Confidentiality: OpenSSH provides end-to-end encryption, protecting against eavesdropping. Furthermore, it notifies you of new server keys to protect against man-in-the-middle attacks.
    Integrity: In addition to protecting the confidentiality of the exchanged data, cryptography also protects the integrity of the traffic.
    Tunneling: SSH can create a secure “tunnel” to route other protocols through SSH. This setup leads to a VPN-like connection.
    X11 Forwarding: If you connect to a Unix-like system with a graphical user interface, SSH allows you to use the graphical application over the network.
You would use command: **ssh username@hostname** to connect to ssh server. If the username is same as logged in username, you only need s**sh hostname**. Then you will asked for password, however if public key authentiation is used you will logged in immediately.

SFTP stands for SSH File Transfer Protocol and allows secure file transfer. It is part of the SSH protocol suite and shares the same port number, 22. If enabled in the OpenSSH server configuration, you can connect using a command such as sftp username@hostname.