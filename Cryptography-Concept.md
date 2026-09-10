# Cryptography Concepts

## Overview

This room provides an understanding of cryptography in our everyday digital encounters.

## What I Learned

- Symmetric Encryption 
- Asymmetric Encryption

## Exercises

### Exercise 1 — [Understanding CIA Traid]

**Q1.** What's the flag you received after completing all levels of the Secret Message Rescue game?
**Answer:** THM{CAESAR_CIPHER_MASTER_2026}

**Q2.** Using the Caesar cipher with a key of 5, what does CYBER become when encoded? (Uppercase, no spaces.)
**Answer:** HDGJW

**Q3.** Using the Caesar cipher, find the correct key and decode the following secret message: FVZCYR PNRFNE PVCURE.
**Answer:** SIMPLE CAESAR CIPHER

### Exercise 2 — [The Security Mindset]

**Q1.** In asymmetric encryption, which key stays secret?
**Answer:** Private Key

**Q2.** With asymmetric encryption, Alice can encrypt a message using Bob's public key, and only Bob's private key can decrypt it. Yay or Nay?
**Answer:** Yay

**Q3.** What problem does asymmetric solve that symmetric cannot?
**Answer:** Key Distribution

**Q4.** After initial asymmetric exchange in HTTPS, what encryption type handles bulk data?
**Answer:** Symmetric

## Key Takeaways

Plaintext is what you can read. Ciphertext is scrambled gibberish.
A key is the secret that controls scrambling and unscrambling.
An algorithm is the public method for using the key.
Symmetric encryption uses a single key for both encryption and decryption. It's fast and efficient, but you need a secure way to share that key. We used the Caesar cipher to see how this works.
Asymmetric encryption uses two linked keys: a public key that anyone can use and a private key that only one person keeps. This solves the key distribution problem and powers the initial handshake for HTTPS connections.

## Notes

How do we actually protect secrets and detect tampering in the real world. That's where cryptography comes in.

Symmetric Encryption: The same key encrypts and decrypts the message. Sender and receiver needs copy of that key. The key has to stay secret from everyone else. E.g., Caesar Cipher
Asymmetric Encryption: There are two keys one public and one private public key is accessible to everyone and used for encryption whereas private key is only available to one person and it is used for decryption.
Hybrid approach: Asymmetric is used to solve the key distribution problem and Symmetric encryption is used for faster data transfer
A certificate is a digital document that:
    Contains someone's public key.
    States who that key belongs to (like example.com).
    A trusted authority digitally signs it, called a Certificate Authority (CA).
