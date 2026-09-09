# HTTP in Detail

## Overview

Learn about how you request content from a web server using the HTTP protocol

## What I Learned

- HTTP(S)
- Request and Response
- HTTP Methods
- Headers 
- Cookies

## Exercises

### Exercise 1 — [Introduction]

**Q1.** What does HTTP stand for?
**Answer:** HyperText Transfer Protocol

**Q2.** What does the S in HTTPS stand for?
**Answer:** Secure

### Exercise 2 — [Request and Response]
**Q1.** What HTTP protocol is being used in the above example?
**Answer:** HTTP/1.1

**Q2.** What response header tells the browser how much data to expect?
**Answer:** Content-Length

### Exercise 3 — [HTTP Methods]

**Q1.** What method would be used to create a new user account?
**Answer:** POST

**Q2.** What method would be used to update your email address?
**Answer:** PUT

**Q3.** What method would be used to remove a picture you've uploaded to your account?
**Answer:** DELETE

**Q4.** What method would be used to view a news article?
**Answer:** GET

### Exercise 4 — [HTTP Methods]

**Q1.** What response code might you receive if you've created a new user or blog post article?
**Answer:** 201

**Q2.** What response code might you receive if you've tried to access a page that doesn't exist?
**Answer:** 404

**Q3.** What response code might you receive if the web server cannot access its database and the application crashes?
**Answer:** 503

**Q4.** What response code might you receive if you try to edit your profile without logging in first?
**Answer:** 401

### Exercise 5 — [Headers]

**Q1.** What header tells the web server what browser is being used?
**Answer:** User-Agent

**Q2.** What header tells the browser what type of data is being returned?
**Answer:** Content-Type

**Q3.** What header tells the web server which website is being requested?
**Answer:** Host

### Exercise 6 — [Cookies]

**Q1.** Which header is used to save cookies to your computer?
**Answer:** Set-Cookie

## Key Takeaways

## Key Takeaways

* HTTP is the protocol used for communication between clients and web servers.
* HTTPS is HTTP secured with encryption.
* HTTP requests contain methods, headers, and sometimes a body; servers respond with status codes, headers, and data.
* Common methods: **GET, POST, PUT, DELETE**.
* Status codes show the result: **2xx success, 3xx redirect, 4xx client error, 5xx server error**.
* Headers provide additional information about requests and responses.
* Cookies allow websites to maintain information about a user's session/state.
* URL fragments (`#...`) point to a specific location within a webpage.

## Notes

HTTP: HyperText Transfer Protocol is a set of rules used for communicating with the webservers for transmitting of webpage data.
HTTPS: Secure version of HTTP, where S stands for Secure. It encrypts the data
URL: Uniform Resource Locator is a predominantly an instruction on how to access the resources on the internet.
- Secheme: The protocol used for e.g, http, https, ftp
- User: Some services requires users to login, you can put username and password in the url
- Host: The domain name or the IP address of the server you wish to access
- Port: The port you are going to connect, 80 for http and 443 for https
- Path: The filename or the resource you are trying to access
- Query String: Extra bit of info that can be sent to the requested path
- Fragment: The reference to the location on the actual page requested
Header: Header contains extra information to give to the webserver you are trying to communicate with
HTTP Methods: HTTP Methods are the way for the client to show the intended action when making http request
- GET: Used for getting information from webserver
- POST: This is used for submitting information to the webserver
- PUT: This is used for submitting data to webserver to update information
- DELETE: Used to delete data from webserver
HTTP Status Codes: Informs the client the outcome of their requests
- 100 - 199 - Information Response
- 200 - 299 - Sucess
- 300 - 399 - Redirection
- 400 - 499 - Client Error
- 500 - 599 - Server Error
Common HTTP Status Codes:
- 200: OK
- 201: Created
- 301: Moved Permanantly
- 302: Found
- 400: Bad Request
- 401: Not Authorised
- 403: Forbidden
- 404: Page Not Found
- 405: Method Not Allowed
- 500: Internal Server Error
- 503: Service Unavailable
Visit this to Study Status Code in dept: https://http.cat/

**Common Request Headers**

Host: Some web servers host multiple websites so by providing the host headers you can tell it which one you require, otherwise you'll just receive the default website for the server.
User-Agent: This is your browser software and version number, telling the web server your browser software helps it format the website properly for your browser and also some elements of HTML, JavaScript and CSS are only available in certain browsers.
Content-Length: When sending data to a web server such as in a form, the content length tells the web server how much data to expect in the web request. This way the server can ensure it isn't missing any data.
Accept-Encoding: Tells the web server what types of compression methods the browser supports so the data can be made smaller for transmitting over the internet.
Cookie: Data sent to the server to help remember your information (see cookies task for more information).

**Common Response Headers**

Set-Cookie: Information to store which gets sent back to the web server on each request (see cookies task for more information).
Cache-Control: How long to store the content of the response in the browser's cache before it requests it again.
Content-Type: This tells the client what type of data is being returned, i.e., HTML, CSS, JavaScript, Images, PDF, Video, etc. Using the content-type header the browser then knows how to process the data.
Content-Encoding: What method has been used to compress the data to make it smaller when sending it over the internet.