# Javascript Essentials

## Overview

Learn how to use JavaScript to add interactivity to a website and understand associated vulnerabilities.

## What I Learned

- Essential Javascript

## Exercises

### Exercise 1 — [Essential concepts]

**Q1.** What term allows you to run a code block multiple times as long as it is a condition?
**Answer:** loop

### Exercise 2 — [Javascript Overview]

**Q1.** What is the code output if the value of x is changed to 10?
**Answer:** 20

**Q2.** Is JavaScript a compiled or interpreted language?
**Answer:** Interpreted

### Exercise 3 — [Integrating Javascript into HTML]

**Q1.** Which type of JavaScript integration places the code directly within the HTML document?
**Answer:** Internal

**Q2.** Which method is better for reusing JS across multiple web pages?
**Answer:** External

**Q3.** What is the name of the external JS file that is being called by external_test.html?
**Answer:** thm_external.js

**Q4.** What attribute links an external JS file in the <script> tag?
**Answer:** src

### Exercise 4 — [Abusing Dialogue Function]

**Q1.** In the file invoice.html, how many times does the code show the alert Hacked?
**Answer:** 5

**Q2.** Which of the JS interactive elements should be used to display a dialogue box that asks the user for input?
**Answer:** prompt

**Q3.** If the user enters Tesla, what value is stored in the carName= prompt("What is your car name?")? in the carName variable?
**Answer:** Tesla

### Exercise 5 — [Bypassing Control Flow Statement]

**Q1.** What is the message displayed if you enter the age less than 18?
**Answer:** You are a Minor

**Q2.** What is the password for the user admin?
**Answer:** ComplexPassword

### Exercise 6 — [Exploring Minified Files]

**Q1.** What is the alert message shown after running the file hello.html?
**Answer:** Welcome to THM

**Q2.**What is the value of the age variable in the following obfuscated code snippet?
age=0x1*0x247e+0x35*-0x2e+-0x1ae3;
**Answer:** 21

## Key Takeaways

We've covered important topics like the basics of JS, creating our first JS code and integrating JS in HTML. Moving forward, we discussed other interactive elements of JS, like prompts and how attackers can abuse them. Then, the room highlighted the usage of control flow statements and how they can be bypassed in JS.
We then explored how to use minify and obfuscate a JS file and learned the other way around. Lastly, we touched upon some best practices that you can follow to keep your web app safe from cyber threats. 

## Notes

JavaScript (JS) is a popular scripting language that allows web developers to add interactive features to websites containing HTML and CSS (styling).

Request-Response Cycle - In web development, the request-response cycle is when a user's browser (the client) sends a request to a web server, and the server responds with the requested information. This could be a webpage, data, or other resources.

Minification in JS is the process of compressing JS files by removing all unnecessary characters, such as spaces, line breaks, comments, and even shortening variable names. This helps reduce the file size and improves the loading time of web pages, especially in production environments. Minified files make the code more compact and harder to read for humans, but they still function exactly the same.