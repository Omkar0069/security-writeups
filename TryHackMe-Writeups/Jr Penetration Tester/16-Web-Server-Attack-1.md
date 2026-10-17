# Web Server Attack 1

## Overview

Enumerate and identify misconfigurations across Apache, Nginx, Node.js, and Python HTTP Server.

## What I Learned



## Exercises

### Exercise 1 — [Identifying Web Servers]

**Q1.** What value does the Server header return for the Python HTTP Server running on port 8000? (Answer Format: SimpleHTTP/X.X Python/X.X.X)
**Answer:** SimpleHTTP/0.6 Python/3.12.3

**Q2.** Which HTTP header reveals the application framework running on port 3000?
**Answer:** X-Powered-By

**Q3.** What web server software is running on port 8080?
**Answer:** nginx

### Exercise 2 — [Python HTTP Server]

**Q1.** What database password is stored in the .env file served by the Python HTTP Server?
**Answer:** S3cur3DBPass!

**Q2.** What is the flag found inside the backup archive served by the Python HTTP Server?
**Answer:** THM{py_server_exposed}

### Exercise 3 — [Apache2]

**Q1.** What Apache module exposes real-time server statistics at /server-status?
**Answer:** mod_status

**Q2.** What is the flag found in the /files/ directory on Apache?
**Answer:** THM{apache_dir_listing}

### Exercise 4 — [Node.js]

**Q1.** What value does the NODE_ENV variable have in the debug endpoint response?
**Answer:** development

**Q2.** What is the flag found in the static files served by the Node.js application?
**Answer:** THM{node_debug_exposed}

### Exercise 5 — [Nginx]

**Q1.** What Nginx directive enables directory listing in a location block?
**Answer:** autoindex on

**Q2.** What URL path exposes Nginx connection statistics?
**Answer:** /nginx_status

**Q3.** What is the flag found in the directory listing on port 8080?
**Answer:** THM{nginx_autoindex}

### Exercise 6 — [Common Misconfigurations Across Servers]

**Q1.** Which security header, when missing, allows a page to be embedded in an iframe on another domain?
**Answer:** X-Frame-Options

**Q2.** What finding text does Nikto report when it detects directory indexing on the /files/ path?
**Answer:** Directory Indexing found

## Key Takeaways


Response headers are the fastest fingerprinting surface. The Server and X-Powered-By headers reveal software type and sometimes version before you have made a single request to an actual application path.
Python's built-in HTTP server has no access controls of any kind. When it appears in an engagement, assume the entire working directory is readable, including dotfiles such as .env.
Apache's mod_status and directory listing are enabled by default on Ubuntu installs and require active configuration to restrict them. Their presence is common and worth checking on every Apache engagement.
Node.js Express applications in development mode leak stack traces, route lists, and environment variables. Each of those is a finding in its own right, and together they give a complete picture of the application's internals.
Nginx autoindex and stub_status mirror Apache's directory listing and mod_status patterns. The directives differ, but the investigation approach is the same.
Security headers are absent by default on all four server types. An audit with curl -sI and a grep for the header names is a fast, reliable check that belongs in every web server engagement.



## Notes

Python's HTTP server serves the entire working directory, including every file in it, including dotfiles like .env. There is no .htaccess equivalent, no blocklist, no configuration file. If the file exists in the directory, anyone who can reach port 8000 can download it.

This is different from Apache or Nginx, where directory listing is disabled by default, and administrators can restrict individual paths. Python's HTTP server has one mode: serve everything.

**Apache** is the most widely deployed web server in the world, which means it appears in nearly every engagement that touches web infrastructure. Its default Ubuntu configuration leaves several things enabled that testers regularly find and report. The three most common are directory listing on specific paths, the server-status module, and backup files sitting in the document root.