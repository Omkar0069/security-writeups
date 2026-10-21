# Burpsuite: Other Modules

## Overview

Take a dive into some of Burp Suite's lesser-known modules.

## What I Learned

- Some other less important modules of burpsuite.

## Exercises

### Exercise 1 — [Decoder Overview]

**Q1.** Which feature attempts auto-decode of the input?
**Answer:** Smart Decode

### Exercise 2 — [Decoder: Encoding/Decoding]

**Q1.** Base64 encode the phrase: Let's Start Simple.
What is the base64 encoded version of this text?
**Answer:** TGV0J3MgU3RhcnQgU2ltcGxl

**Q2.** URL Decode this data: %4e%65%78%74%3a%20%44%65%63%6f%64%69%6e%67.
What is the plaintext returned?
**Answer:** Next: Decoding

**Q3.** Use Smart decode to decode this data: &#x25;&#x33;&#x34;&#x25;&#x33;&#x37;.
What is the decoded text?
**Answer:** 47

**Q4.** Encode this phrase: Encoding Challenge.
Start with base64 encoding. Take the output of this and convert it into ASCII Hex. Finally, encode the hex string into octal.
What is the final string?
**Answer:** 24034214a720270024142d541357471232250253552c1162d1206c

### Exercise 3 — [Decoder: Hashing]

**Q1.** Using Decoder, what is the SHA-256 hashsum of the phrase: Let's get Hashing!?
Convert this into an ASCII Hex string for the answer to this question.
**Answer:** 6b72350e719a8ef5af560830164b13596cb582757437e21d1879502072238abe

**Q2.** Generate an MD4 hashsum of the phrase: Insecure Algorithms.
Encode this as base64 (not ASCII Hex) before submitting.
**Answer:** TcV4QGZZN7y7lwYFRMMoeA==

**Q3.** Let's look at an in-context example:

First, download the file attached to this task.

Note: This file can also be downloaded from the deployed VM with wget http://10.48.157.0:9999/AlteredKeys.zip — you may find this helpful if you are using the AttackBox.

Now read the problem specification below:

"Some joker has messed with my SSH key! There are four keys in the directory, and I have no idea which is the real one. The MD5 hashsum for my key is 3166226048d6ad776370dc105d40d9f8 — could you find it for me?"

What is the correct key name?
**Answer:** key3

### Exercise 4 — [Sequencer: Overview]

**Q1.** What does Sequencer allow us to evaluate?
**Answer:** entropy 

### Exercise 5 — [Sequencer: Live Capture]

**Q1.** What is the overall quality of randomness estimated to be?
**Answer:** Excellent

### Exercise 6 — [Organizer: Overview]

**Q1.** Are saved requests read-only? (yea/nay)
**Answer:** yea

### Exercise 7 — [Pitchfork]

**Q1.** What is the maximum number of payload sets we can load into Intruder in Pitchfork mode?
**Answer:** 20

### Exercise 8 — [Cluster Bomb]

**Q1.** We have three payload sets. The first set contains 100 lines, the second contains 2 lines, and the third contains 30 lines.

How many requests will Intruder make using these payload sets in a Cluster bomb attack?
**Answer:** 6000

### Exercise 9 — [Practical Example]

**Q1.** What username and password combination indicates a successful login attempt? The answer format is "username:password".
**Answer:** m.rivera:letmein1


## Key Takeaways

To summarize, Decoder allows you to encode and decode data, making it easier to read and understand the information being transferred. Comparer enables you to spot differences between two datasets, which can be pivotal in identifying vulnerabilities or anomalies. Sequencer helps in performing entropy analysis on tokens, providing insights into the randomness of their generation and, consequently, their security level. Organizer enables you to store and annotate copies of HTTP requests that you may want to revisit later.

## Notes

**Decoder:** The Decoder module of Burp Suite gives user data manipulation capabilities. As implied by its name, it not only decodes data intercepted during an attack but also provides the function to encode our own data, prepping it for transmission to the target. Decoder also allows us to create hashsums of data, as well as providing a Smart Decode feature, which attempts to decode provided data recursively until it is back to being plaintext (like the "Magic" function of Cyberchef).
- Plain: This refers to the raw text before any transformations are applied.
- URL: URL encoding is utilized to ensure the safe transfer of data in the URL of a web request. It involves substituting characters for their ASCII character code in hexadecimal format, preceded by a percentage symbol (%). This method is vital for any type of web application testing.   
- HTML: HTML Entities encoding replaces special characters with an ampersand (&), followed by either a hexadecimal number or a reference to the character being escaped, and ending with a semicolon (;). This method ensures the safe rendering of special characters in HTML and helps prevent attacks such as XSS. The HTML option in Decoder allows any character to be encoded into its HTML escaped format or decode captured HTML entities. For instance, to decode a previously discussed quotation mark, input the encoded version and choose Decode as -> HTML
- Base64: Base64, a commonly used encoding method, converts any data into an ASCII-compatible format. The under-the-hood functioning isn't crucial at this stage.
- ASCII Hex: This option transitions data between ASCII and hexadecimal representations. For instance, the word "ASCII" can be converted into the hexadecimal number "4153434949". Each character is converted from its numeric ASCII representation into hexadecimal.
- Hex, Octal, and Binary: These encoding methods apply solely to numeric inputs, converting between decimal, hexadecimal, octal (base eight), and binary representations.
- Gzip: Gzip compresses data, reducing file and page sizes before browser transmission. Faster load times are highly desirable for developers looking to enhance their SEO score and avoid user inconvenience. Decoder facilitates the manual encoding and decoding of gzip data, although it often isn't valid ASCII/Unicode.


**Decoder: Hashing**
Hashing is a one-way process that transforms data into a unique signature. For a function to qualify as a hashing algorithm, the output it generates must be irreversible. A proficient hashing algorithm ensures that every data input will generate a completely unique hash. For instance, using the MD5 algorithm to produce a hashsum for the text "MD5sum" returns 4ae1a02de5bd02a5515f583f4fca5e8c. Using the same algorithm for "MD5SUM" yields an entirely different hash despite the close resemblance of the input: 13b436b09172400c9eb2f69fbd20adad. Therefore, hashes are commonly used to verify the integrity of files and documents, as even a tiny alteration to the file significantly changes the hashsum.

**Comparer: Overview**
Comparer, as the name implies, lets us compare two pieces of data, either by ASCII words or by bytes.
There are many situations where being able to quickly compare two (potentially very large) pieces of data can come in handy.
For example, when performing a login bruteforce or credential stuffing attack with Intruder, you may wish to compare two responses with different lengths to see where the differences lie and whether the differences indicate a successful login.

**Sequencer: Overview**
Sequencer allows us to evaluate the entropy, or randomness, of "tokens". Tokens are strings used to identify something and should ideally be generated in a cryptographically secure manner. These tokens could be session cookies or Cross-Site Request Forgery (CSRF) tokens used to protect form submissions. If these tokens aren't generated securely, then, in theory, we could predict upcoming token values. The implications could be substantial, for instance, if the token in question is used for password resets.

**Organizer: Overview**
The Organizer module of Burp Suite is designed to help you store and annotate copies of HTTP requests that you may want to revisit later. This tool can be particularly useful for organizing your penetration testing workflow. Here are some of its key features:
You can store requests that you want to investigate later, save requests that you've already identified as interesting, or save requests that you want to add to a report later.
You can send HTTP requests to Burp Organizer from other Burp Modules such as Proxy or Repeater. You can do this by right-clicking the request and selecting Send to Organizer or using the default hotkey Ctrl + O. Each HTTP request that you send to Organizer is a read-only copy of the original request saved at the point you sent it to Organizer.