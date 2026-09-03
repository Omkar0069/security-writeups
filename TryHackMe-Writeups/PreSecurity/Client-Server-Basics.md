# Client-Server Basics

## Overview

This room explains the basics of Client-Server model.

## What I Learned

**Service, Client, Server:** The browser is the client that requests the webpage, and the server is the system that serves it.
**Request and Response:** In computer systems, we can say that Alice used a browser (the client) to request a webpage from a server, which then sent the webpage to the client.
**Protocol:**  A protocol defines how a client can communicate with a server. 
**Port:** A port is used to identify a specific service running on a system. When a client wants to access a service on a server, it must connect using the correct port.
**DNS:** Domain Name System (DNS) is the protocol responsible for resolving hostnames, such as tryhackme.com, to their respective IP addresses.

HTTP Commands

In the main specifications that define HTTP (also called Request for Comments, or documents), there are 9 core commands. In HTTP lingo, we use the term method instead of command. Below you can see an overview of these methods:
    GET
    POST
    PUT
    DELETE
    PATCH
    HEAD
    OPTIONS
    CONNECT
    TRACE

## Exercises

### Exercise 1 — [Basic Terminologies]

**Q1.** What would be the host in the following URL? https://www.iamlearning.thm/contac
**Answer:** Port

**Q2.** What do we call the address of a server?
**Answer:** Internet Protocol Address

### Exercise 2 — [Web Communication]

**Q1.** What would be the host in the following URL? https://www.iamlearning.thm/contact
**Answer:** www.iamlearning.thm

**Q2.** What would be the scheme in the following URL? https://www.iamlearning.thm/contact
**Answer:** https

## Key Takeaways

In this room, we have explored how devices on the internet can offer services to each other. We focused on the client-server model, which is similar to ordering a pizza. The client initiates the communication and the server replies.

Then, we continued with an example of the protocol which is used for websites. We saw a practical example of how a client request and server response actually looks like behind the scenes.

## Notes

**Stateless:** The server does not automatically remember what happened in previous requests.
**Stateful:** It means the system remembers information about previous interactions and uses that information in later requests.