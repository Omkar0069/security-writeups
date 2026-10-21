# Burpsuite: Intruder

## Overview

Learn how to use Intruder to automate requests in Burp Suite.

## What I Learned

- Intruder is funn.

## Exercises

### Exercise 1 — [What is Intruder]

**Q1.** In which Intruder tab can we define the "Attack type" for our planned attack?
**Answer:** Positions

### Exercise 2 — [Positions]

**Q1.** What symbol defines the start and the end of a payload position?
**Answer:** §

### Exercise 3 — [Payloads]

**Q1.** Which Payload processing rule could we use to add characters at the end of each payload in the set?
**Answer:** Add Suffix  

### Exercise 4 — [Introduction to Attack Types]

**Q1.** What attack type cycles through the payloads inserting one payload at a time into each position defined in the request?
**Answer:** Sniper

### Exercise 5 — [Sniper]

**Q1.** If you were using Sniper to fuzz three parameters in a request with a wordlist containing 100 words, how many requests would Burp Suite need to send to complete the attack?
**Answer:** 300

**Q2.** How many sets of payloads will Sniper accept for conducting an attack?
**Answer:** 1

### Exercise 6 — [Battering Ram]

**Q1.** As a hypothetical question: You need to perform a Battering ram Intruder attack on the example request above.
If you have a wordlist with two words in it (admin and Guest) and the positions in the request template look like this:
username=§pentester§&password=§Expl01ted§
What would the body parameters of the first request that Burp Suite sends be?
**Answer:** username=admin&password=admin

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

By now, you should have a solid understanding of how to effectively utilize Intruder to automate requests and perform various types of attacks.

## Notes

Intruder is Burp Suite's built-in fuzzing tool that allows for automated request modification and repetitive testing with variations in input values. By using a captured request (often from the Proxy module), Intruder can send multiple requests with slightly altered values based on user-defined configurations. It serves various purposes, such as brute-forcing login forms by substituting username and password fields with values from a wordlist or performing fuzzing attacks using wordlists to test subdirectories, endpoints, or virtual hosts. Intruder's functionality is comparable to command-line tools like Wfuzz or ffuf.

The Positions tab of Burp Suite Intruder has a dropdown menu for selecting the attack type. Intruder offers four attack types, each serving a specific purpose. Let's explore each of them:

    Sniper: The Sniper attack type is the default and most commonly used option. It cycles through the payloads, inserting one payload at a time into each position defined in the request. Sniper attacks iterate through all the payloads in a linear fashion, allowing for precise and focused testing.

    Battering ram: The Battering ram attack type differs from Sniper in that it sends all payloads simultaneously, each payload inserted into its respective position. This attack type is useful when testing for race conditions or when payloads need to be sent concurrently.

    Pitchfork: The Pitchfork attack type enables the simultaneous testing of multiple positions with different payloads. It allows the tester to define multiple payload sets, each associated with a specific position in the request. Pitchfork attacks are effective when there are distinct parameters that need separate testing.

    Cluster bomb: The Cluster bomb attack type combines the Sniper and Pitchfork approaches. It performs a Sniper-like attack on each position but simultaneously tests all payloads from each set. This attack type is useful when multiple positions have different payloads, and we want to test them all together.

As shown in the table, Pitchfork takes the first item from each list and substitutes them into the request, one per position. It then repeats this process for the next request by taking the second item from each list and substituting it into the template. Intruder continues this iteration until one or all of the lists run out of items. It's important to note that Intruder stops testing as soon as one of the lists is complete. Therefore, in Pitchfork attacks, it is ideal for the payload sets to have the same length. If the lengths of the payload sets differ, Intruder will only make requests until the shorter list is exhausted, and the remaining items in the longer list will not be tested.