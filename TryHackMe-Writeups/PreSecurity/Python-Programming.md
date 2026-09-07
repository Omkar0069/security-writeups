# Python: Simple Demo

## Overview

Explore what a basic Python program looks like.

## What I Learned

In this room, we will create a “Guess the Number” game. Our plan will be as follows:

    The computer secretly picks a number between 1 and 20.
    The user keeps guessing until they get it right.
    The computer tells the user whether their guess is too low or too high.

## Exercises

### Exercise 1 — [Variables]

**Q1.** What is the name of the function we used to display text on the screen?
**Answer:** print()

**Q2.** What is the name of the function that we used to convert user input to an integer?
**Answer:** int()

### Exercise 2 — [Conditionals]

**Q1.** How does Python write “else if”?
**Answer:** elif

**Q2.** What will the program display if the user’s input is 50?
**Answer:** That number is out of range. Try again.

### Exercise 3 — [Iterations]

**Q1.** What type of loop does this program use?
**Answer:** while

**Q2.** What will the program display if the user makes the correct guess in 3 tries?
**Answer:** You got it in 3 tries!

## Key Takeaways

In this room, we covered three key pillars in imperative programming languages:

    Variables
    Conditionals with if and else
    Loops with while

## Notes

You need to import the library first to be able to use it like 
import random  # gives us tools for picking random numbers
secret = random.randint(1,20) # generates random number from 1 to 20