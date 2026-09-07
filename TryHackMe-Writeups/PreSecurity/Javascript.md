# Javascript: Simple Demo

## Overview

Explore what a basic JavaScript program looks like.

## What I Learned

JavaScript is used in most of the web pages that you visit on a day-to-day basis. Consequently, when we think of JavaScript engines, web browsers come to mind. In fact, JavaScript was initially developed to run on client machines, in particular, within a web browser. However, this has changed with the release of Node.js, which enables developers to build web applications with JavaScript. Consequently, as Node.js spread, JavaScript was no longer just a client-side programming language but also a server-side one.

**In this room, we will create a “Guess the Number” game. Our plan will be as follows:**

    The computer secretly picks a number between 1 and 20.
    The user keeps guessing until they get it right.
    The computer tells the user whether their guess is too low or too high.

## Exercises

### Exercise 1 — [Variables]

**Q1.** What word is used to declare a variable?
**Answer:** let

**Q2.** What word is used to declare a constant?
**Answer:** const

**Q3.** What is the method that we call to display text on the screen?
**Answer:** console.log()

### Exercise 2 — [Prompting the user for input]

**Q1.** What method is used to convert user input into a number?
**Answer:** parseInt()

### Exercise 3 — [Conditionals]

**Q1.** The secret is 10. What will our program display on the screen if the user makes a guess of 15?
**Answer:** Too high, try again.

**Q2.** The secret is 10. What will our program display on the screen if the user makes a guess of 35?
**Answer:** That number is out of range. Try again.

### Exercise 1 — [Variables]

**Q1.** What is the name of the loop that we used in this task?
**Answer:** while

**Q2.** What is the name of the variable that is incremented by one when the user makes a new wrong guess?
**Answer:** tries

**Q3.** How is “not equal” written in JavaScript?
**Answer:** !==

## Key Takeaways

In this room, we covered three key pillars in imperative programming languages:

    Variables
    Conditionals with if and else
    Loops with while

## Notes

**Secret number explained**

Step 1: Math.random()

Math.random() can produce any decimal from 0 up to (but not including) 1.

For example:

0.01
0.05
0.23
0.51
0.87
0.999
Step 2: Multiply by 20
Math.random() * 20

Now the range becomes:

0 → almost 20

For example:

0.01 × 20 = 0.2
0.05 × 20 = 1
0.23 × 20 = 4.6
0.51 × 20 = 10.2
0.87 × 20 = 17.4

Notice that the result can be between 0 and 20, including values less than 1.

Step 3: Math.floor()

Math.floor() simply removes everything after the decimal:

Math.floor(0.2)  → 0
Math.floor(1.0)  → 1
Math.floor(4.6)  → 4
Math.floor(10.2) → 10
Math.floor(17.4) → 17

So before the +1, the possible integers are:

0, 1, 2, 3, ... 19
Step 4: + 1

Finally:

Math.floor(Math.random() * 20) + 1

becomes:

0 + 1 = 1
1 + 1 = 2
2 + 1 = 3
...
19 + 1 = 20

So the final range is:

1 through 20.


**The await instruction pauses the system until the user responds. Obviously, Node.js’s default behavior is not to wait for a user to enter a value. Remember that Node.js is built as a runtime environment for web applications, not to run such a command-line JavaScript program. Consequently, we need to use libraries to override the default behavior and force Node.js to wait for the user.**