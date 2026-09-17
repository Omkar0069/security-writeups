
# Hashing Basics

## Overview

Learn about hashing functions and their uses in password verification and file integrity checking.

## What I Learned

- Hashing 
- Hashing for Passwords
- Hashing for Integrity

## Exercises

### Exercise 1 — [Hash Function]

**Q1.** If you have an 8-bit hash output, how many possible hash values are there?
**Answer:** 256

**Q2.** What is the output size in bytes of the MD5 hash function?
**Answer:** 16

**Q3.** What is the SHA256 hash of the passport.jpg file in ~/Hashing-Basics/Task-2?
**Answer:** 77148c6f605a8df855f2b764bcc3be749d7db814f5f79134d2aa539a64b61f02

### Exercise 2 — [Insecure Password Storage for Authentication]

**Q1.** What is the 20th password in rockyou.txt?
**Answer:** qwerty

### Exercise 3 — [Using Hashing for Secure Password Storage]

**Q1.** Manually check the hash “4c5923b6a6fac7b7355f53bfe2b8f8c1” using the rainbow table above.
**Answer:** inS3CyourP4$$

**Q2.** Crack the hash “5b31f93c09ad1d065c0491b764d04933” using an online tool.
**Answer:** tryhackme

**Q3.** Should you encrypt passwords in password-verification systems? Yea/Nay
**Answer:** Nay

### Exercise 4 — [Recognising Password Hashes]

**Q1.** What is the hash size in yescrypt?
**Answer:** 256

**Q2.** What’s the Hash-Mode listed for Cisco-ASA MD5?
**Answer:** 2410

**Q3.** What hashing algorithm is used in Cisco-IOS if it starts with $9$?
**Answer:** scrypt

### Exercise 4 — [Password Cracking]

**Q1.** Use hashcat to crack the hash, $2a$06$7yoU3Ng8dHTXphAg913cyO6Bjs3K5lBnwq5FJyA6d01pMSrddr1ZG, saved in ~/Hashing-Basics/Task-6/hash1.txt.
**Answer:** 85208520

**Q2.** Use hashcat to crack the SHA2-256 hash, 9eb7ee7f551d2f0ac684981bd1f1e2fa4a37590199636753efe614d4db30e8e1, saved in saved in ~/Hashing-Basics/Task-6/hash2.txt.
**Answer:** halloween

**Q3.** Use hashcat to crack the hash, $6$GQXVvW4EuM$ehD6jWiMsfNorxy5SINsgdlxmAEl3.yif0/c3NqzGLa0P.S7KRDYjycw5bnYkF5ZtB8wQy8KnskuWQS3Yr1wQ0, saved in ~/Hashing-Basics/Task-6/hash3.txt.
**Answer:** spaceman

**Q4.** Crack the hash, b6b0d451bbf6fed658659a9e7e5598fe, saved in ~/Hashing-Basics/Task-6/hash4.txt.
**Answer:** funforyou

### Exercise 4 — [Hashing for Integrity Checking]

**Q1.** What is SHA256 hash of libgcrypt-1.11.0.tar.bz2 found in ~/Hashing-Basics/Task-7?
**Answer:** 09120c9867ce7f2081d6aaa1775386b98c2f2f246135761aae47d81f58685b9c

**Q2.** What’s the hashcat mode number for HMAC-SHA512 (key = $pass)?
**Answer:** 1750

## Key Takeaways

This room covered hashing functions and their uses from various perspectives.

## Notes

What is Hash value? A hash value is a fixed-size string or characters that is computed by a hash function. A hash function takes an input of an arbitrary size and returns an output of fixed length, i.e., a hash value.

A hash function takes some input data of any size and creates a summary or digest of that data. The output has a fixed size. It’s hard to predict the output for any input and vice versa. Good hashing algorithms will be relatively fast to compute and prohibitively slow to reverse, i.e., go from the output and determine the input. Any slight change in the input data, even a single bit, should cause a significant change in the output.

