# Natas Level 0 → 1

## Objective
Find the password for Natas Level 1.

## Enumeration
- Logged into the application using the provided credentials.
- Inspected the webpage.
- Viewed the page source.

## Finding
The HTML source contained a comment revealing the password for the next level.

## Steps
1. Right-click the webpage.
2. Select **View Page Source**.
3. Search through the HTML comments.
4. Locate the password for the next level.

## Why It Worked
HTML comments are sent to the client's browser even though they are not displayed on the webpage. Anyone can inspect the page source and read them.

## Security Concept
**Information Disclosure** – Sensitive information should never be stored in client-side HTML comments because users can easily view the source code.

## Real-World Impact
An attacker could discover:
- Credentials
- API keys
- Internal URLs
- Developer notes
- Hidden functionality

## Mitigation
Never place sensitive information in HTML comments or any other client-side code. Store secrets securely on the server.

## Key Takeaways
- Always inspect the page source during reconnaissance.
- HTML comments can accidentally leak sensitive information.

# Natas Level 1 -> 2

## Objective
Find the password for Natas Level 2.

## Enumeration
- Logged into the application using the provided credentials.
- Since the right click is blocked, we need to find another way to see the view source.

## Finding
The HTML source contained a comment revealing the password for the next level.

## Steps
1. Since right click is blocked.
2. Add **view-source:** before the URL to view page source.
3. Search through the HTML comments.
4. Locate the password for the next level.

## Why It Worked
HTML comments are sent to the client's browser even though they are not displayed on the webpage. Anyone can inspect the page source and read them.

## Security Concept
**Information Disclosure** – Sensitive information should never be stored in client-side HTML comments because users can easily view the source code.

## Real-World Impact
An attacker could discover:
- Credentials
- API keys
- Internal URLs
- Developer notes
- Hidden functionality

## Mitigation
Never place sensitive information in HTML comments or any other client-side code. Store secrets securely on the server.

## Key Takeaways
- Always inspect the page source during reconnaissance.
- HTML comments can accidentally leak sensitive information.

# Natas Level 2 -> 3

## Objective
Find the password for Natas Level 3.

## Enumeration
- Logged into the application using the provided credentials.
- View source page provided crucial info.

## Finding
The hidden directories.

## Steps
1. Since there was nothing on the page I still view the page source.
2. And there was a crucial info related to /files/pixel.png.
3. I visited that directory there was nothing special.
4. Then I went to /files directory and saw useful information there.
5. There was a parent directory that also include users.txt besides pixel.png
6. I visited users.txt and got the password for natas3.

## Why It Worked
Page contains different directories and any views can visit them if not properly secure there pixel.png was just a scapegoat; the orignal content was inside /files directory.

## Security Concept
**Information Disclosure** – Sensitive information should never be stored in client-side HTML comments because users can easily access to different directories using tools like gobuster and dirb.

## Real-World Impact
An attacker could discover:
- Credentials
- API keys
- Internal URLs
- Developer notes
- Hidden functionality

## Mitigation
Never place sensitive information in HTML comments or any other client-side code. Store secrets securely on the server.

## Key Takeaways
- Always inspect the page source during reconnaissance.
- HTML comments can accidentally leak sensitive information.
- HTML directories can also leak sensitive data if not secured properly.

# Natas Level 3 -> 4

## Objective
Find the password for Natas Level 4.

## Enumeration
- Logged into the application using the provided credentials.
- Knowing what is robots.txt is crucial.

## Finding
robots.txt.

## Steps
1. Since there was nothing on the page I still view the page source.
2. There was nothing crucial.
3. I visited the robots.txt directory and dang!
4. There I found the a secret directory.
5. I visited that directory and there was a subdirectory.
6. I visited users.txt and got the password for natas4.

## Why It Worked
robots.txt is a publicly accessible file that tells search engine crawlers which parts of a website they should or shouldn't index. It is not a security mechanism, so anyone can access it directly. Developers sometimes accidentally expose sensitive directories or files by listing them there.

## Security Concept
**Information Disclosure** – Sensitive information should never be stored in client-side HTML comments because users can easily access to different directories using tools like gobuster and dirb.

## Real-World Impact
An attacker could discover:
- robots.txt
- Credentials
- API keys
- Internal URLs
- Developer notes
- Hidden functionality

## Mitigation
Never place sensitive information in HTML comments or any other client-side code. Store secrets securely on the server.

## Key Takeaways
- Sensitive data should never be placed in robots.txt because the file is publicly accessible. Anyone can read it directly, making it unsuitable for hiding directories, files, or confidential information.

# Natas Level 4 -> 5

## Objective
Find the password for Natas Level 5.

## Enumeration
- Logged into the application using the provided credentials.
- Knowing about referer head is must.

## Finding
Referer head manipulation.

## Steps
1. Since there was nothing on the page I still view the page source.
2. There was nothing crucial.
3. I used burpesuite to intercept traffic.
4. I send the GET request to the repeater.
5. Then I changed the **referer head** from **natas4 to natas5**.
6. When I checked the response I got the password for natas5.

## Why It Worked
The Referer header is an HTTP request header that tells the server which webpage the client came from before making the current request.
Changing the referer head cause the system to think that the request came from natas5.

## Security Concept
**Client-Side Trust** – Trusting user-controlled HTTP headers for security decisions can allow attackers to bypass access restrictions.

## Real-World Impact
An attacker can spoof the **Referer header** to gain unauthorized access to protected resources if the server relies on it for authorization.

## Mitigation
Perform authentication and authorization on the server using sessions or access tokens. Never rely on the Referer header for security checks.

## Key Takeaways
- Sensitive data should never be placed in robots.txt because the file is publicly accessible. Anyone can read it directly, making it unsuitable for hiding directories, files, or confidential information.

# Natas Level 5 -> 6

## Objective
Find the password for Natas Level 6.

## Enumeration
- Logged into the application using the provided credentials.
- Portswigger.

## Finding
Sending request head to repeater.

## Steps
1. I intercepted the traffic through burpsuite.
2. Then I saw the request head where isLogin was set to 0.
3. I send that query to repeater and changed it to 1.
4. Then I got the password in response.

## Why It Worked
Changing the login query to 1 lead to get the password.

## Security Concept
Never solely rely on 1 argument which can intercepted easily.

## Real-World Impact
An attacker can spoof the argument and gain sensitive information.

## Key Takeaways
Never rely on single authentication which can easily be bypassed.

# Natas Level 6 -> 7

## Objective
Find the password for Natas Level 7.

## Enumeration
- Logged into the application using the provided credentials.
- Directories.

## Finding
Secret directories.

## Steps
1. I viewed the source code with the given link.
2. I found includes/secret.inc directory.
3. I visited that directory.
4. I went to the source page where I found the secret.
5. I copied that secret and pasted in the input field on the home page.
6. Got the pass for natas7.

## Why It Worked
I knew it.

## Security Concept
Never put sensitive info in client side model even if it is a secret directory it can be intercepted or break.

## Real-World Impact
An attacker can use that sensitive data for bad use.

## Key Takeaways
Sensitive data should be kept in severside encrypted.

# Natas Level 7 -> 8

## Objective
Find the password for Natas Level 8.

## Enumeration
- Logged into the application using the provided credentials.
- URL Path.

## Finding
URL Path.

## Steps
1. I viewed the source code.
2. I found the path for the password.
3. I visited that home directory.
4. I manipulated the URL in the bar removed home and pasted the path I found in the source code.
5. Got the pass for natas8.

## Why It Worked
Changing the URL provided the password.

## Security Concept
Never put sensitive info in client side model even if it is a secret directory it can be intercepted or break.

## Real-World Impact
An attacker can use that sensitive data for bad use.

## Key Takeaways
Sensitive data should be kept in severside encrypted.

# Natas Level 8 -> 9

## Goal
Find the password for the next level.

---

## Vulnerability
Encoded secret was on source code.

---

## Solution
1. I visited the source code via view source code option.
2. I got an encoded secret.
3. Then I use decoder tool from burpsuite and encoded the secret in ascii hex -> reversed string -> base64
4. I got the Input secret and Entered it in the input field.
5. I got the password for the next level.

---

## Tool
Decoder
---

## Key Takeaway
- We can decrypt the data through decoder tool.
- Sensitive data should not be put on client side module.

# Natas Level 9 -> 10

## Goal
Find the password for the next level.

---

## Vulnerability
OS Command Injection

---

## Solution
1. I visited the source code via view source code option.
2. Then I enter the command in search bar: ; cat /etc/natas_webpass/natas10
3. I got the password for the next level.

---

## Tool
PHP and command knowlege.
---

## Key Takeaway
The shell recognizes:
command1 ; command2
as two separate commands.
Because the application didn't sanitize or escape your input, your input became part of the shell syntax instead of remaining plain text.

This is the essence of command injection.

# Natas Level 10 → 11

## Goal

Find the password for the next level.

---

## Vulnerability

The application stored a client-side encoded secret inside a cookie. Since the cookie was only encoded and not securely protected, it could be decoded, modified, and re-encoded to change its value.

---

## Solution

1. Inspected the page source and application behavior.
2. Identified the encoded data stored in the cookie.
3. Used Burp Suite Decoder to decode the value and analyzed its structure.
4. Modified the decoded data to change the relevant parameter.
5. Re-encoded the modified value and replaced the original cookie.
6. Refreshed the page and obtained the password for the next level.

---

## Tool

* Burp Suite Decoder

---

## Key Takeaways

* Client-side data should never be trusted for security decisions.
* Encoding is **not** a security mechanism; anyone can decode and modify encoded data.
* Sensitive information and authorization logic should always be validated on the server.
* Cookies should be protected with integrity mechanisms (e.g., signatures) if their contents affect application behavior.
