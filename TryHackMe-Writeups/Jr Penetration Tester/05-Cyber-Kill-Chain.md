# Cyber Kill Chain

## Overview

Explore the Cyber Kill Chain by Lockheed Martin.

## What I Learned

- Importance of Cyber Kill Chain

## Exercises

### Exercise 1 — [Introduction]

**Q1.** How many phases comprise the Cyber Kill Chain?
**Answer:** 7

### Exercise 2 — [Reconaissance]

**Q1.** What is the term for using search engines to reveal sensitive information and confidential files?
**Answer:** Google Dorking

**Q2.** What type of reconnaissance is it where the attacker checks the social media pages?
**Answer:** Passive Reconnaissance

### Exercise 3 — [Weaponisation]

**Q1.** What technique is mentioned to evade detection by making it challenging to analyse the malicious code? issue that you reported. What stage of the risk management cycle does this activity fall under?
**Answer:** Obfuscation

**Q2.** What built-in feature makes creating a malicious MS Office document possible?
**Answer:** Macro

### Exercise 4 — [Delivery]

**Q1.** What method involves showing advertisements on legitimate websites to redirect users to malicious pages?
**Answer:** Malvertising

**Q2.** What phishing attack sends text messages with malicious links or instructions to download malware?
**Answer:** Smishing

### Exercise 5 — [Exploitation]

**Q1.** What type of exploit is used before the vendor becomes aware of a vulnerability?
**Answer:** Zero-day Exploit

**Q2.** What technology is mentioned to prevent an attacker from gaining access even with valid login credentials?
**Answer:** MFA

### Exercise 6 — [Installation]

**Q1.** What tactic allows attackers to execute operating system commands on a target via a web browser interface?
**Answer:** Web Shell

**Q2.** What technique is mentioned to prevent the execution of unauthorised or malicious software by only allowing approved applications to run?
**Answer:** Allowlisiting

### Exercise 7 — [C2]

**Q1.** What is the name of the tactic where data is hidden within DNS queries?
**Answer:** DNS Tunnelling

**Q3.** What protocol would the attacker use to smuggle his data as encrypted web traffic?
**Answer:** HTTPS

### Exercise 7 — [Actions and Objectives]

**Q1.** What is the term for stealing sensitive files from a target network?
**Answer:** Data Exfilteration

**Q2.** What principle limits who can access sensitive systems and data to minimise damage caused by an attacker?
**Answer:** Principle of least privilege

**Q3.** What type of attack involves encrypting files and demanding payment in exchange for the decryption key?
**Answer:** Ransomware

## Key Takeaways

In this room, we covered the Cyber Kill Chain and its seven phases. The most damage occurs in the last phase; however, companies can protect themselves against such damage if they interrupt the chain in any of its earlier stages. Consequently, the focus of the defensive security team, such as the blue team, would be to detect the attacker’s actions related to each phase and to block them.

## Notes

The Cyber Kill Chain 
**Reconnaissance:** In the first stage, the attacker gathers information about the target
**Weaponisation:** Once proper reconnaissance is conducted, the attacker creates a deliverable payload or modifies an existing one based on the target system’s vulnerabilities
**Delivery:** Once ready, the attacker sends the weaponised payload to the target
**Exploitation:** Once executed, the payload exploits a vulnerability in the target’s system
**Installation:** The exploitation enables the attacker to install a backdoor or malware to maintain persistence in the target’s environment
**Command & Control (C2):** Using the installed backdoor, the attacker can control the compromised system
**Actions on Objectives:** Reaching this far, the attacker can now carry out further actions such as data exfiltration or other systems’ exploitation

Reconnaissance can be divided into two types: passive and active. When carrying out passive reconnaissance, the attacker performs their activities without making any “noise,” for example, using open-source intelligence (OSINT). However, in the case of active reconnaissance, the attacker cannot remain completely quiet and invisible; it requires some form of interaction with the target organisation, such as using social engineering against the target’s personnel or scanning a target system for vulnerabilities.

 Sometimes, an exploit is made available before the vendor becomes aware that a vulnerability exists in their product; in this case, it is called a zero-day exploit.