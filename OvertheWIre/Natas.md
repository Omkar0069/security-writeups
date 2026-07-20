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