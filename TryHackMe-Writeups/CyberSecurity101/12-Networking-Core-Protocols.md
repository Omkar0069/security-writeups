# Networking Core Protocols

## Overview

Learn about the core TCP/IP protocols.

## What I Learned

- DNS
- WHOIS
- HTTP(S)
- FTP
- SMTP
- POP3
- IMAP

## Exercises

### Exercise 1 — [DNS]

**Q1.** Which DNS record type refers to IPv6?
**Answer:** AAAA

**Q2.** Which DNS record type refers to the email server?
**Answer:** MX

### Exercise 2 — [WHOIS]

**Q1.** When was the x.com record created? Provide the answer in YYYY-MM-DD format.
**Answer:** 1993-04-02

**Q2.** When was the twitter.com record created? Provide the answer in YYYY-MM-DD format.
**Answer:** 2000-01-21

### Exercise 3 — [ICMP]

**Q1.** Using the FTP client ftp on the AttackBox, access the FTP server at 10.49.160.17 and retrieve flag.txt. What is the flag found?
**Answer:** THM{FAST-FTP}

### Exercise 4 — [SMTP]

**Q1.** Which SMTP command indicates that the client will start the contents of the email message?
**Answer:** DATA

**Q2.** What does the email client send to indicate that the email message has been fully entered?
**Answer:** .

### Exercise 5 — [POP3]

**Q1.** Looking at the traffic exchange, what is the name of the POP3 server running on the remote server?
**Answer:** Dovecot

**Q2.** Use telnet to connect to 10.49.160.17’s POP3 server. What is the flag contained in the fourth message?
**Answer:** THM{TELNET_RETR_EMAIL}

### Exercise 6 — [IMAP]

**Q1.** What IMAP command retrieves the fourth email message?
**Answer:** FETCH 4 BODY[]

## Key Takeaways

With the protocols covered, we now have a better understanding of how domain names are resolved, how web pages are served, and how email is sent and received. Another primary purpose of this room is to give you a good understanding of how a protocol functions behind the graphical interfaces.

## Notes

DNS operates at the Application Layer, i.e., Layer 7 of the ISO OSI model. DNS traffic uses UDP port 53 by default and TCP port 53 as a default fallback. 

FTP: File Transfer Protocol is used to transfer files between network. Some important commands are:
**USER** is used to input the username
**PASS** is used to enter the password
**RETR** (retrieve) is used to download a file from the FTP server to the client.
**STOR** (store) is used to upload a file from the client to the FTP server.

SMTP: Simple Mail Transfer Protocol (SMTP) defines how a mail client talks with a mail server and how a mail server talks with another.
HELO or EHLO initiates an SMTP session
MAIL FROM specifies the sender’s email address
RCPT TO specifies the recipient’s email address
DATA indicates that the client will begin sending the content of the email message
. is sent on a line by itself to indicate the end of the email message

The SMTP server listens on port 25 by default

POP3: You’ve received an email and want to download it to your local mail client. The Post Office Protocol version 3 (POP3) is designed to allow the client to communicate with a mail server and retrieve email messages.
Some common POP3 commands are:

    USER <username> identifies the user
    PASS <password> provides the user’s password
    STAT requests the number of messages and total size
    LIST lists all messages and their sizes
    RETR <message_number> retrieves the specified message
    DELE <message_number> marks a message for deletion
    QUIT ends the POP3 session applying changes, such as deletions
By default POP3 server listens on port 110

IMAP: IMAP allows synchronizing read, moved, and deleted messages. IMAP is quite convenient when you check your email via multiple clients.
Commands:
LOGIN <username> <password> authenticates the user
SELECT <mailbox> selects the mailbox folder to work with
FETCH <mail_number> <data_item_name> Example fetch 3 body[] to fetch message number 3, header and body.
MOVE <sequence_set> <mailbox> moves the specified messages to another mailbox
COPY <sequence_set> <data_item_name> copies the specified messages to another mailbox
LOGOUT logs out
By Default IMAP server listens on port 143
