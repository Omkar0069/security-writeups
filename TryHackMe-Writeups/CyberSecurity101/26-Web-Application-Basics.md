# Web Application Basics

## Overview

Learn the basics of web applications: HTTP, URLs, request methods, response codes, and headers.

## What I Learned

- Basics of Web applications

## Exercises

### Exercise 1 — [Overview]

**Q1.** Which component on a computer is responsible for hosting and delivering content for web applications?
**Answer:** Web Server

**Q2.** Which tool is used to access and interact with web applications?
**Answer:** Web Browser

**Q3.** Which component acts as a protective layer, filtering incoming traffic to block malicious attacks, and ensuring the security of the the web application?
**Answer:** Web Application Firewall

### Exercise 2 — [URL]

**Q1.** Which protocol provides encrypted communication to ensure secure data transmission between a web browser and a web server?
**Answer:** HTTPS

**Q2.** What term describes the practice of registering domain names that are misspelt variations of popular websites to exploit user errors and potentially engage in fraudulent activities?
**Answer:** Typosquatting

**Q3.** What part of a URL is used to pass additional information, such as search terms or form inputs, to the web server?
**Answer:** Query String

### Exercise 3 — [HTTP Messages]

**Q1.** Which HTTP message is returned by the web server after processing a client's request?
**Answer:** HTTP response

**Q2.** What follows the headers in an HTTP message?
**Answer:** Empty line

### Exercise 4 — [HTTP Request line and method]

**Q1.** Which HTTP protocol version became widely adopted and remains the most commonly used version for web communication, known for introducing features like persistent connections and chunked transfer encoding?
**Answer:** HTTP/1.1

**Q2.** Which HTTP request method describes the communication options for the target resource, allowing clients to determine which HTTP methods are supported by the web server?
**Answer:** OPTIONS

**Q3.** In an HTTP request, which component specifies the specific resource or endpoint on the web server that the client is requesting, typically appearing after the domain name in the URL?
**Answer:** URL Path

### Exercise 5 — [Headers and Body]

**Q1.** Which HTTP request header specifies the domain name of the web server to which the request is being sent?
**Answer:** HOST

**Q2.** What is the default content type for form submissions in an HTTP request where the data is encoded as key=value pairs in a query string format?
**Answer:** application/x-www-form-urlencoded

**Q3.** Which part of an HTTP request contains additional information like host, user agent, and content type, guiding how the web server should process the request?
**Answer:** Request Headers

### Exercise 6 — [HTTP Response]

**Q1.** What part of an HTTP response provides the HTTP version, status code, and a brief explanation of the response's outcome?
**Answer:** Status Line

**Q2.** Which category of HTTP response codes indicates that the web server encountered an internal issue or is unable to fulfil the client's request?
**Answer:** Server Error Responses

**Q3.** Which HTTP status code indicates that the requested resource could not be found on the web server?
**Answer:** 404

### Exercise 7 — [HTTP Response]

**Q1.** Which HTTP response header can reveal information about the web server's software and version, potentially exposing it to security risks if not removed?
**Answer:** Server

**Q2.** Which flag should be added to cookies in the Set-Cookie HTTP response header to ensure they are only transmitted over HTTPS, protecting them from being exposed during unencrypted transmissions?
**Answer:** Secure

**Q3.** Which flag should be added to cookies in the Set-Cookie HTTP response header to prevent them from being accessed via JavaScript, thereby enhancing security against XSS attacks?
**Answer:** HttpOnly

### Exercise 8 — [Security Headers]

**Q1.** In a Content Security Policy (CSP) configuration, which property can be set to define where scripts can be loaded from?
**Answer:** Script-Src

**Q2.** When configuring the Strict-Transport-Security (HSTS) header to ensure that all subdomains of a site also use HTTPS, which directive should be included to apply the security policy to both the main domain and its subdomains?
**Answer:** IncludeSubDomains

**Q3.** Which HTTP header directive is used to prevent browsers from interpreting files as a different MIME type than what is specified by the server, thereby mitigating content type sniffing attacks?
**Answer:** nosniff

## Key Takeaways

What components are involved in web applications
The structure of the Uniform Resource Locator (URL)
What are HTTP messages, requests, headers and responses
The importance of Security headers

## Notes

**FrontEnd(Client Side)**
- HTML: Hypertext Markup Language, defines structure of the page.
- CSS: Cascading Style Sheet, used to design the page.
- Javascript: Brings interactivity to the page.

**BackEnd (Server Side)**
- Database: Stores or retrive the information of the user about the preferences what to show and what to not.
- Infrastructure Components: Web server, application server, storage etc
- WAF: Web Application Firewall is an optional component for web applications, it filter out dangerous requests away from the web server and provide an element of protection.

A URL (Uniform Resource Locator) is a web address that let you access to all kind of online content.

Anatomy of a URL: http://user:password@tryhackme.com:80/view-room?id=101#task3
where,
http - Schema
user:password - User
tryhackme.com - Host/Domain
80 - Port
view-room - Path
?id=101 - Query String
task3 - Fragment

Note that not everything is used everytime some components might not be used for some cases.

Schema - The protocol used to access the website. Most common being http and https(recommended)
User - Some URLs may include users login details for site that requires authentication
Host/Domain - The host and domain is the most important part of the url as it tell which website are you accessing.
Port - The port helps direct url to the right service on the web server.
Path - The path points specifies the specific page or file on the web server you are trying to access.
Query String - The query string is the part of the URL that starts with a question mark (?). It’s often used for things like search terms or form inputs.
Fragment - The exact location within the web server.

There are two types of HTTP messages:
    HTTP Requests: Sent by the user to trigger actions on the web application.
    HTTP Responses: Sent by the server in response to the user’s request.

HTTP message:
- Start Line - The start line is like the introduction to the message it tell what kind of message is it, request or response
- Header - Headers are made up of key-value pairs that provide extra information about the HTTP message. They give instructions to both the client and the server handling the request or response. These headers cover all sorts of things, like security, content types, and more, making sure everything goes smoothly in the communication.
- Empty Line - The empty line is a little divider that separates the header from the body. It’s essential because it shows where the headers stop and where the actual content of the message begins. Without this empty line, the message might get messed up, and the client or server could misinterpret it, causing errors.
- Body - Stores the actual data

HTTP Methods

The HTTP method tells the server what action the user wants to perform on the resource identified by the URL path. Here are some of the most common methods and their possible security issue:

- **GET** Used to fetch data from the server without making any changes. Reminder! Make sure you’re only exposing data the user is allowed to see. Avoid putting sensitive info like tokens or passwords in GET requests since they can show up as plaintext.
- **POST** Sends data to the server, usually to create or update something. Reminder! Always validate and clean the input to avoid attacks like SQL injection or XSS.
- **PUT** Replaces or updates something on the server. Reminder! Make sure the user is authorised to make changes before accepting the request.
- **DELETE** Removes something from the server. Reminder! Just like with PUT, make sure only authorised users can delete resources.

Besides these common methods, there are a few others used in specific cases:

- **PATCH** Updates part of a resource. It’s useful for making small changes without replacing the whole thing, but always validate the data to avoid inconsistencies.
- **HEAD** Works like GET but only retrieves headers, not the full content. It’s handy for checking metadata without downloading the full response.
- **OPTIONS** Tells you what methods are available for a specific resource, helping clients understand what they can do with the server.
- **TRACE** Similar to OPTIONS, it shows which methods are allowed, often for debugging. Many servers disable it for security reasons.
- **CONNECT** Used to create a secure connection, like for HTTPS. It’s not as common but is critical for encrypted communication.

**HTTP Versions**

HTTP/0.9 (1991)
The first version, only supported GET requests.
HTTP/1.0 (1996)
Added headers and better support for different types of content, improving caching.
HTTP/1.1 (1997)
Brought persistent connections, chunked transfer encoding, and better caching. It’s still widely used today.
HTTP/2 (2015)
Introduced features like multiplexing, header compression, and prioritisation for faster performance.
HTTP/3 (2022)
Built on HTTP/2, but uses a new protocol (QUIC) for quicker and more secure connections.



URL Encoded (application/x-www-form-urlencoded)
A format where data is structured in pairs of key and value where (key=value). Multiple pairs are separated by an (&) symbol, such as key1=value1&key2=value2. Special characters are percent-encoded.

Form Data (multipart/form-data)
Allows multiple data blocks to be sent where each block is separated by a boundary string. The boundary string is the defined header of the request itself. This type of formatting can be used to send binary data, such as when uploading files or images to a web server. 

JSON (application/json)
In this format, the data can be sent using the JSON (JavaScript Object Notation) structure. Data is formatted in pairs of name : value. Multiple pairs are separated by commas, all contained within curly braces { }.

XML (application/xml)
In XML formatting, data is structured inside labels called tags, which have an opening and closing. These labels can be nested within each other. You can see in the example below the opening and closing of the tags to send details about a user called Aleksandra.
