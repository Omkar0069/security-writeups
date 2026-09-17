
# Cryptography Basics

## Overview

Learn how to use Tcpdump to save, filter, and display packets.

## What I Learned

- What is Cryptography?
- Introduction to Symmetric and Asymmetric Encrytion
- Basic math - XOR and Modulo

## Exercises

### Exercise 1 — [Importance of Cryptography]

**Q1.** What is the standard required for handling credit card information?
**Answer:** PCI DSS

### Exercise 2 — [Plaintext to Ciphertext]

**Q1.** What do you call the encrypted plaintext?
**Answer:** Ciphertext

**Q2.** What do you call the process that returns the plaintext?
**Answer:** Decryption

### Exercise 3 — [Historical Cipher]

**Q1.** Knowing that XRPCTCRGNEI was encrypted using Caesar Cipher, what is the original plaintext?
**Answer:** ICANENCRYPT

### Exercise 4 — [Types of Encryption]

**Q1.** Should you trust DES? (Yea/Nay)
**Answer:** Nay

**Q2.** When was AES adopted as an encryption standard?
**Answer:** 2001

### Exercise 4 — [Basic Math]

**Q1.** What’s 1001 ⊕ 1010?
**Answer:** 0011

**Q2.** What’s 118613842%9091?
**Answer:** 3565

**Q3.** What’s 60%12?
**Answer:** 0

## Key Takeaways

In this room, we learned about the importance of cryptography and some of the problems that it solves. We also introduced symmetric and asymmetric encryption ciphers. Finally, we explained the and the modulo operations.

## Notes

Have you ever wondered how to prevent third parties from reading your messages? How can your app or web browser build a secure channel with a remote server? By secure, we mean that no one can read or alter the exchanged data; furthermore, we can be confident that we are connecting with the real server. Thanks to cryptography, these requirements are satisfied.

Cryptography lays the foundation for our digital world. While networking protocols have made it possible for devices spread across the globe to communicate, cryptography has made it possible to trust this communication.

- When you log in to TryHackMe, your credentials are encrypted and sent to the server so that no one can retrieve them by snooping on your connection.
- When you connect over SSH, your SSH client and the server establish an encrypted tunnel so no one can eavesdrop on your session.
- When you conduct online banking, your browser checks the remote server’s certificate to confirm that you are communicating with your bank’s server and not an attacker’s.
- When you download a file, how do you check if it was downloaded correctly? Cryptography provides a solution through hash functions to confirm that your file is identical to the original one.

Key Terms:
**Plaintext** is the original, readable message or data before it’s encrypted. It can be a document, an image, a multimedia file, or any other binary data.
**Ciphertext** is the scrambled, unreadable version of the message after encryption. Ideally, we cannot get any information about the original plaintext except its approximate size.
**Cipher** is an algorithm or method to convert plaintext into ciphertext and back again. A cipher is usually developed by a mathematician.
**Key** is a string of bits the cipher uses to encrypt or decrypt data. In general, the used cipher is public knowledge; however, the key must remain secret unless it is the public key in asymmetric encryption. We will visit asymmetric encryption in a later task.
**Encryption** is the process of converting plaintext into ciphertext using a cipher and a key. Unlike the key, the choice of the cipher is disclosed.
**Decryption** is the reverse process of encryption, converting ciphertext back into plaintext using a cipher and a key. Although the cipher would be public knowledge, recovering the plaintext without knowledge of the key should be impossible (infeasible).

**Symmetric Encryption:** Symmetric encryption, also known as symmetric cryptography, uses the same key to encrypt and decrypt the data.
Examples of symmetric encryption are DES (Data Encryption Standard), 3DES (Triple DES) and AES (Advanced Encryption Standard).
    DES was adopted as a standard in 1977 and uses a 56-bit key. With the advancement in computing power, in 1999, a DES key was successfully broken in less than 24 hours, motivating the shift to 3DES.
    3DES is DES applied three times; consequently, the key size is 168 bits, though the effective security is 112 bits. 3DES was more of an -hoc solution when DES was no longer considered secure. 3DES was deprecated in 2019 and should be replaced by AES; however, it may still be found in some legacy systems.
    AES was adopted as a standard in 2001. Its key size can be 128, 192, or 256 bits.

**Asymmetric Encryption:** Unlike symmetric encryption, which uses the same key for encryption and decryption, asymmetric encryption uses a pair of keys, one to encrypt and the other to decrypt

**XOR Operation**
XOR, short for “exclusive OR”, is a logical operation in binary arithmetic that plays a crucial role in various computing and cryptographic applications. In binary, XOR compares two bits and returns 1 if the bits are different and 0 if they are the same, as shown in the truth table below. This operation is often represented by the symbol ⊕ or ^.
XOR has several interesting properties that make it useful in cryptography and error detection. One key property is that applying XOR to a value with itself results in 0, and applying XOR to any value with 0 leaves it unchanged. This means A ⊕ A = 0, and A ⊕ 0 = A for any binary value A. Additionally, XOR is commutative, i.e., A ⊕ B = B ⊕ A. And it is associative, i.e., (A ⊕ B) ⊕ C = A ⊕ (B ⊕ C).

**Modulo Operation**
Another mathematical operation we often encounter in cryptography is the modulo operator, commonly written as % or as mod. The modulo operator, X%Y, is the remainder when X is divided by Y. In our daily life calculations, we focus more on the result of division than on the remainder. The remainder plays a significant role in cryptography.