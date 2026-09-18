
# John the Ripper: Basics

## Overview

Learn how to use John the Ripper, a powerful and adaptable hash-cracking tool.

## What I Learned

- John the Ripper with it's various conversion tools

## Exercises

### Exercise 1 — [Basic Term]

**Q1.** What is the most popular extended version of John the Ripper?
**Answer:** Jumbo John

### Exercise 2 — [Insecure Password Storage for Authentication]

**Q1.** Which website’s breach was the rockyou.txt wordlist created from?
**Answer:** rockyou.com

### Exercise 3 — [Cracking Basic Hashes]

**Q1.** What do we need to set the --format flag to in order to crack this hash?
**Answer:** md5

**Q2.** What is the cracked value of hash1.txt?
**Answer:** biscuit

**Q3.** What type of hash is hash2.txt?
**Answer:** SHA1

**Q4.** What is the cracked value of hash2.txt?
**Answer:** kangeroo

**Q5.** What type of hash is hash3.txt?
**Answer:** SHA256

**Q6.** What is the cracked value of hash3.txt?
**Answer:** microphone

**Q5.** What type of hash is hash4.txt?
**Answer:** whirlpool

**Q6.** What is the cracked value of hash4.txt?
**Answer:** colossal

### Exercise 4 — [Cracking Windows Authentication Hashes]
e
**Q1.** What do we need to set the --format flag to in order to crack this hash?
**Answer:** nt

**Q2.** What is the cracked value of this password?
**Answer:** mushroom

### Exercise 5 — [Cracking /etc/shadow Hashes]

**Q1.** What is the root password?
**Answer:** 1234

### Exercise 6 — [Single Crack Mode]

**Q1.** What is Joker’s password?
**Answer:** Jok3r

### Exercise 7 — [Custom Rules]

**Q1.** What do custom rules allow us to exploit?
**Answer:** Password complexity predictability

**Q2.** What rule would we use to add all capital letters to the end of the word?
**Answer:** Az"[A-Z]"

**Q3.** What flag would we use to call a custom rule called THMRules?
**Answer:** --rules=THMRules

### Exercise 8 — [Cracking Password Protected Zip Files]

**Q1.** What is the password for the secure.zip file?
**Answer:** pass123

**Q2.** What is the contents of the flag inside the zip file?
**Answer:** THM{w3ll_d0n3_h4sh_r0y4l}

### Exercise 9 — [Cracking Password Protected Rar Files]

**Q1.** What is the password for the secure.rar file?
**Answer:** password

**Q2.** What are the contents of the flag inside the rar file?
**Answer:** THM{r4r_4rch1ve5_th15_t1m3}

### Exercise 10 — [Cracking SSH Keys with John]

**Q1.** What is the SSH private key password?
**Answer:** mango

## Key Takeaways

You understand the basic principles and pattern of using John with even the most obscure supported hashes by now.

## Notes

What makes hashing secure? While this is a fascinating mathematical concept that proves fundamental to computing and cryptography, it is entirely outside the scope of this room. But abstractly, the algorithm to hash the value will be “P” and can, therefore, be calculated reasonably. However, an “un-hashing” algorithm would be “NP” and intractable to solve, meaning that it cannot be computed in a reasonable time using standard computers.

John the Ripper converts the passwords from the wordlist into hashes then match it with the victim hash.

The basic syntax of John is: john [option] [filepath]

**Automatic Cracking**
John has built-in features to detect what type of hash it’s being given and to select appropriate rules and formats to crack it for you; this isn’t always the best idea as it can be unreliable, but if you can’t identify what hash type you’re working with and want to try cracking it, it can be a good option! To do this, we use the following syntax:

john --wordlist=[path to wordlist] [path to file]

--wordlist=: Specifies using wordlist mode, reading from the file that you supply in the provided path
[path to wordlist]: The path to the wordlist you’re using, as described in the previous task

**Format-Specific Cracking**
Once you have identified the hash that you’re dealing with, you can tell John to use it while cracking the provided hash using the following syntax:

john --format=[format] --wordlist=[path to wordlist] [path to file]

    --format=: This is the flag to tell John that you’re giving it a hash of a specific format and to use the following format to crack it
    [format]: The format that the hash is in

Example Usage:

john --format=raw-md5 --wordlist=/usr/share/wordlists/rockyou.txt hash_to_crack.txt

NTLM is the format in which windows store hashes.

**Word Mangling**
The best way to explain Single Crack mode and word mangling is to go through an example:
Consider the username “Markus”.

Some possible passwords could be:
    Markus1, Markus2, Markus3 (etc.)
    MArkus, MARkus, MARKus (etc.)
    Markus!, Markus$, Markus* (etc.)
This technique is called word mangling. 

**How to create Custom Rules**
Custom rules are defined in the john.conf file. This file can be found in /opt/john/john.conf on the TryHackMe Attackbox. It is usually located in /etc/john/john.conf if you have installed John using a package manager or built from source with make.
Let’s go over the syntax of these custom rules, using the example above as our target pattern. Note that you can define a massive level of granular control in these rules. I suggest looking at the wiki here (opens in new tab) to get a full view of the modifiers you can use and more examples of rule implementation.

**The first line:**
[List.Rules:THMRules] is used to define the name of your rule; this is what you will use to call your custom rule a John argument.

We then use a regex style pattern match to define where the word will be modified; again, we will only cover the primary and most common modifiers here:

    Az: Takes the word and appends it with the characters you define
    A0: Takes the word and prepends it with the characters you define
    c: Capitalises the character positionally

These can be used in combination to define where and what in the word you want to modify.

Lastly, we must define what characters should be appended, prepended or otherwise included. We do this by adding character sets in square brackets [ ] where they should be used. These follow the modifier patterns inside double quotes " ". Here are some common examples:

    [0-9]: Will include numbers 0-9
    [0]: Will include only the number 0
    [A-z]: Will include both upper and lowercase
    [A-Z]: Will include only uppercase letters
    [a-z]: Will include only lowercase letters

Please note that:

    [a]: Will include only a
    [!£$%@]: Will include the symbols !, £, $, %, and @

Putting this all together, to generate a wordlist from the rules that would match the example password Polopassword1! (assuming the word polopassword was in our wordlist), we would create a rule entry that looks like this:

[List.Rules:PoloPassword]

cAz"[0-9] [!£$%@]"

Utilises the following:

    c: Capitalises the first letter
    Az: Appends to the end of the word
    [0-9]: A number in the range 0-9
    [!£$%@]: The password is followed by one of these symbols

**Using Custom Rules**
We could then call this custom rule a John argument using the  --rule=PoloPassword flag.
As a full command: john --wordlist=[path to wordlist] --rule=PoloPassword [path to file]

**Zip2John**
Similarly to the unshadow tool we used previously, we will use the zip2john tool to convert the Zip file into a hash format that John can understand and hopefully crack. The primary usage is like this:
zip2john [options] [zip file] > [output file]

**Rar2John**
Almost identical to the zip2john tool, we will use the rar2john tool to convert the RAR file into a hash format that John can understand. The basic syntax is as follows:
rar2john [rar file] > [output file]
    rar2john: Invokes the rar2john tool
    [rar file]: The path to the RAR file you wish to get the hash of
    >: This redirects the output of this command to another file
    [output file]: This is the file that will store the output from the command

**Cracking Key Passwords**

Okay, okay, I hear you. There are no more file archives! Fine! Let’s explore one more use of John that comes up semi-frequently in CTF challenges—using John to crack the SSH private key password of id_rsa files. Unless configured otherwise, you authenticate your SSH login using a password. However, you can configure key-based authentication, which lets you use your private key, id_rsa, as an authentication key to log in to a remote machine over SSH. However, doing so will often require a password to access the private key; here, we will be using John to crack this password to allow authentication over SSH using the key.
SSH2John

Who could have guessed it, another conversion tool? Well, that’s what working with John is all about. As the name suggests, ssh2john converts the id_rsa private key, which is used to log in to the SSH session, into a hash format that John can work with. Jokes aside, it’s another beautiful example of John’s versatility. The syntax is about what you’d expect. Note that if you don’t have ssh2john installed, you can use ssh2john.py, located in the /opt/john/ssh2john.py. If you’re doing this on the AttackBox, replace the ssh2john command with python3 /opt/john/ssh2john.py or on Kali, python /usr/share/john/ssh2john.py.

ssh2john [id_rsa private key file] > [output file]

    ssh2john: Invokes the ssh2john tool
    [id_rsa private key file]: The path to the id_rsa file you wish to get the hash of
    >: This is the output director. We’re using it to redirect the output from this command to another file.
    [output file]: This is the file that will store the output from

