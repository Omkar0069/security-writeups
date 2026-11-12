# Password Cracking

## Overview

Learn how passwords are hashed, identify hash types, and crack them with Hashcat and John the Ripper.

## What I Learned

- The gap between "I have a hash" and "I have a password" is shorter than it looks. Identify the algorithm, pick an attack that fits what we know about the target, and point the right tool at it. The bcrypt hash in Task 6 should have taken noticeably longer than the others. That is not a bug, it is the point of a slow hash function working exactly as intended.

## Exercises

### Exercise 1 — [How Passwords Are Stored]

**Q1.** What property of a hash function means you cannot reverse a hash to recover the original input?
**Answer:** one-way

**Q2.** What term describes the unique random string added to a password before hashing to prevent rainbow table attacks?
**Answer:** salt

**Q3.** Which hashing algorithm was designed specifically for passwords and is deliberately slow by design?
**Answer:** bcrypt

### Exercise 2 — [Identifying Hash Types]

**Q1.** What is the character length of an SHA-256 hash?
**Answer:** 64

**Q2.** What John the Ripper format would you use for an SHA-256 hash?
**Answer:** raw-sha256

### Exercise 3 — [Creating and Cleaning Wordlists]

**Q1.** What is the full path to the rockyou wordlist on the AttackBox?
**Answer:** /usr/share/wordlists/rockyou.txt

**Q2.** What type of attack applies transformations such as capitalisation and number suffixes to an existing wordlist?
**Answer:** rule-based

**Q3.** A password policy requires all passwords to start with a capital letter followed by six lowercase letters and two digits. What attack type is best suited to cracking a hash of such a password?
**Answer:** mask

### Exercise 4 — [Using Your Wordlist]

**Q1.** A penetration tester needs to crack a large set of SHA-256 hashes as quickly as possible. Which tool is the better choice: John the Ripper or Hashcat?
**Answer:** hashcat

**Q2.** What Hashcat attack mode number is used for a mask attack?
**Answer:** 3

**Q3.** Which John the Ripper flag displays previously cracked passwords from the potfile?
**Answer:** --show

## Key Takeaways

We moved from how passwords are stored and why algorithm choice matters, through hash identification with hashid and hashcat --identify, to running dictionary, rule-based, and mask attacks with both John the Ripper and Hashcat. The same knowledge works in reverse: choosing bcrypt or Argon2 with a high cost factor, enforcing salting, and avoiding fast hashes for password storage are the defensive side of everything we practised here.

## Notes

Password are the most common authentication mechanism on the internet and also one of the most reliable attack paths into a system. Whether we are dealing with a leaked database, a captured network handshake, or a hash extracted from a compromised machine, the ability to recover the plaintext from a hash is a fundamental red-team skill.

When a user logs in, the system hashes the submitted password and compares it to the stored hash. If they match, access is granted. The original password never needs to be stored anywhere.

Properties of hash: one-way, deterministic, fixed-length output, collision-resistant.

Salting is a unique random string generated for each user and combined with their password before hashing: stored_value = hash(password + salt)