
# Public Key Cryptography Basics

## Overview

Discover how public key ciphers such as RSA work and explore their role in applications such as SSH.

## What I Learned

- Public Key Cryptrography
- RSA
- Diffie-Hellman
- SSH Key pairs
- Digital Signature and Certificates

## Exercises

### Exercise 1 — [Common use of Asymmetric Encryption]

**Q1.** In the analogy presented, what real object is analogous to the public key?
**Answer:** Lock

### Exercise 2 — [RSA]

**Q1.** Knowing that p = 4391 and q = 6659. What is n?
**Answer:** 29239669

**Q2.** Knowing that p = 4391 and q = 6659. What is ϕ(n)?
**Answer:** 29228620

### Exercise 3 — [Diffie-Hellman Key Exchange]

**Q1.** Consider p = 29, g = 5, a = 12. What is A?
**Answer:** 7

**Q2.** Consider p = 29, g = 5, b = 17. What is B?
**Answer:** 9

**Q3.** Knowing that p = 29, a = 12, and you have B from the second question, what is the key calculated by Bob? (key = Ba mod p)
**Answer:** 24

**Q4.** Knowing that p = 29, b = 17, and you have A from the first question, what is the key calculated by Alice? (key = Ab mod p)
**Answer:** 24

### Exercise 4 — [SSH]

**Q1.** Check the SSH Private Key in ~/Public-Crypto-Basics/Task-5. What algorithm does the key use?
**Answer:** RSA

### Exercise 4 — [Digital Signature & Certificates]

**Q1.** What does a remote web server use to prove itself to the client?
**Answer:** Certificate

**Q2.** What would you use to get a free TLS certificate for your website?
**Answer:** Let's Encrypt

### Exercise 5 — [PNG and GPG]

**Q1.** Use GPG to decrypt the message in ~/Public-Crypto-Basics/Task-7. What secret word does the message hold?
**Answer:** Pineapple

## Key Takeaways

We have defined cryptography as the science of securing communication in the presence of adversaries. Another important science that studies how to break or bypass cryptographic systems is cryptanalysis. As for trying every possible password combination, we call that a brute-force attack. However, when we know that the password is most likely a dictionary word, it will make more sense to try words from a dictionary instead of every possible password combination; this is called a dictionary attack.
    Cryptography is the science of securing communication and data using codes and ciphers.
    Cryptanalysis is the study of methods to break or bypass cryptographic security systems without knowing the key.
    Brute-Force Attack is an attack method that involves trying every possible key or password to decrypt a message.
    Dictionary Attack is an attack method where the attacker tries dictionary words or combinations of them.

## Notes

You can see and hear the other person. Consequently, it is easy to be sure of their identity. That’s authentication, i.e., you are confirming the identity of who you are talking with.
You can also confirm that what you are “hearing” is coming from your business partner. You can tell what words and sentences are coming from your business partner and what is coming from others. That’s authenticity, i.e., you verify that the message genuinely comes from a specific sender. Moreover, you know that what they are saying is reaching you, and there is no chance of anything changing the other party’s words across the table. That’s integrity, i.e., ensuring that the data has not been altered or tampered with.
Finally, you can pick a seat away from the other customers and keep your voice low so that only your business partner can hear you. That’s confidentiality, i.e., only the authorised parties can access the data.

Exchanging keys for symmetric encryption is a widespread use of asymmetric cryptography. Asymmetric encryption is relatively slow compared to symmetric encryption; therefore, we rely on asymmetric encryption to negotiate and agree on symmetric encryption ciphers and keys.

**The Math that makes RSA Secure**
RSA is based on the mathematically difficult problem of factoring a large number. Multiplying two large prime numbers is a straightforward operation; however, finding the factors of a huge number takes much more computing power.
It’s simple to multiply two prime numbers together even on paper, say 113 × 127 = 14351. Even for larger prime numbers, it would still be a feasible job, even by hand. Consider the following numeric example:
    Prime number 1: 982451653031
    Prime number 2: 169743212279
    Their product: 982451653031 × 169743212279 = 166764499494295486767649
On the other hand, it’s pretty tricky to determine what two prime numbers multiply together to make 14351 and even more challenging to find the factors of 166764499494295486767649.


**RSA Explaination:**
```
## 1. Bob chooses two prime numbers

Bob chooses:

* \(p = 157\)
* \(q = 199\)

Both are prime numbers.

Then he multiplies them:

n=p\times q

n=157\times199=31243

So:

\boxed{n=31243}

The number \(n\) is going to be part of **both the public and private key**.

genui{"learning_viz":{"type_id":"PRIMES","initial_values":{"number":31243},"locale_override":"en-US"}}

---

# 2. Calculate Euler's Totient \(\phi(n)\)

For RSA, when:

n=pq

we calculate:

\phi(n)=(p-1)(q-1)

Here:

\phi(n)=(157-1)(199-1)

=156\times198

=30888

So:

\boxed{\phi(n)=30888}

The text writes this another way:

n-p-q+1

which gives the same result:

31243-157-199+1=30888

---

# 3. Bob chooses \(e\)

Now Bob needs a number \(e\) that is **relatively prime** to \(\phi(n)\).

He chooses:

\boxed{e=163}

"Relatively prime" simply means:

\gcd(163,30888)=1

In other words, 163 and 30888 have no common factor other than 1.

This \(e\) becomes part of the **public key**.

---

# 4. Bob chooses \(d\)

Now Bob needs another number \(d\) satisfying:

e\times d\equiv1\pmod{\phi(n)}

He chooses:

\boxed{d=379}

Let's check:

163\times379=61777

Now divide 61777 by 30888:

61777=2(30888)+1

Therefore:

61777\bmod30888=1

So:

163\times379\bmod30888=1

That's exactly what we need.

---

# 5. Bob now has his keys

### Public key

\boxed{(n,e)=(31243,163)}

This can be shared with everyone.

### Private key

\boxed{(n,d)=(31243,379)}

This must be kept secret by Bob.

So remember:

| Key     | Contains | Purpose    |
| ------- | -------- | ---------- |
| Public  | \(n,e\)  | Encryption |
| Private | \(n,d\)  | Decryption |

---

# 6. Alice wants to send \(13\)

Alice wants to send:

\boxed{x=13}

She has Bob's **public key**:

(n,e)=(31243,163)

RSA encryption is:

y=x^e\bmod n

So:

y=13^{163}\bmod31243

After calculating that huge modular exponentiation:

\boxed{y=16341}

Alice sends **16341** to Bob.

Notice something important:

> Alice doesn't send 13 directly. She sends 16341.

---

# 7. Bob decrypts it

Bob receives:

y=16341

He has the private key:

(n,d)=(31243,379)

RSA decryption is:

x=y^d\bmod n

Therefore:

x=16341^{379}\bmod31243

And the result is:

\boxed{x=13}

Bob has recovered the original message.

---

# The whole process

Think of RSA like this:

text
                 BOB
        ┌───────────────────┐
        │ p = 157           │
        │ q = 199           │
        │                   │
        │ n = p × q = 31243 │
        │ φ(n) = 30888      │
        │ e = 163            │
        │ d = 379            │
        └───────────────────┘
                  │
          ┌───────┴───────┐
          ↓               ↓
     PUBLIC KEY       PRIVATE KEY
     (31243,163)      (31243,379)
          │               │
          │               │
          ↓               │
        ALICE              │
          │                │
     Message = 13         │
          │                │
     13^163 mod 31243     │
          │                │
          ↓                │
       16341 ──────────────┤
                           ↓
                  16341^379 mod 31243
                           │
                           ↓
                          13


## The 5 things you should remember

For understanding RSA, memorize this flow:

**1. Choose primes**

p,q

**2. Calculate \(n\)**

n=pq

**3. Calculate \(\phi(n)\)**

\phi(n)=(p-1)(q-1)

**4. Choose \(e\) and calculate \(d\)**

e\times d\equiv1\pmod{\phi(n)}

**5. Encrypt/decrypt**

Encryption:

\boxed{y=x^e\bmod n}

Decryption:

\boxed{x=y^d\bmod n}

### In this example:

157,199
\rightarrow31243
\rightarrow30888
\rightarrow e=163,d=379

Then:

\boxed{13\rightarrow16341\rightarrow13}

That's the entire RSA example.

The **important idea** is that anyone can know \(n\) and \(e\), but without the private \(d\), reversing the encryption is computationally difficult when \(p\) and \(q\) are enormous. The small numbers here are only for demonstration.

```

**Diffie-Hellman Key Exchange**
Key exchange aims to establish a shared secret between two parties. It is a method that allows two parties to establish a shared secret over an insecure communication channel without requiring a pre-existing shared secret and without an observer being able to get this key. Consequently, this shared key can be used for symmetric encryption in subsequent communications.
Alice and Bob generate secrets independently; let’s call these secrets A and B. They also have some public common material; let’s call this C.
We need to make some assumptions. Firstly, whenever we combine secrets, they’re practically impossible to separate. Secondly, the order in which they’re combined doesn’t matter. Alice and Bob will combine their secrets with the common material to form AC and BC. They will then send these to each other and combine the received part with their secret to create two identical keys, both ABC. Now, they can use this key to communicate.

**Various Algorithms:**
DSA (Digital Signature Algorithm) is a public-key cryptography algorithm specifically designed for digital signatures.
ECDSA (Elliptic Curve Digital Signature Algorithm) is a variant of DSA that uses elliptic curve cryptography to provide smaller key sizes for equivalent security.
ECDSA-SK (ECDSA with Security Key) is an extension of ECDSA. It incorporates hardware-based security keys for enhanced private key protection.
Ed25519 is a public-key signature system using EdDSA (Edwards-curve Digital Signature Algorithm) with Curve25519.
Ed25519-SK (Ed25519 with Security Key) is a variant of Ed25519. Similar to ECDSA-SK, it uses a hardware-based security key for improved private key protection.

**What’s a Digital Signature?**
Digital signatures provide a way to verify the authenticity and of a digital message or document. Proving the authenticity of files means we know who created or modified them. Using asymmetric cryptography, you produce a signature with your private key, which can be verified using your public key. Only you should have access to your private key, which proves you signed the file. In many modern countries, digital and physical signatures have the same legal value.