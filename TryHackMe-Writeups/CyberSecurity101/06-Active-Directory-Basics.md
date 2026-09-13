# Active Directory Basics

## Overview

This room will introduce the basic concepts and functionality provided by Active Directory.

## What I Learned

- Active Directory
- Windows Domain

## Exercises

### Exercise 1 — [Introduction]

**Q1.** In a Windows domain, credentials are stored in a centralised repository called...
**Answer:** Active Directory

**Q2.** In a Windows domain, credentials are stored in a centralised repository called...
**Answer:** Domain Controller

### Exercise 2 — [Active Directory]

**Q1.** How would you create the file named "newnote"?
**Answer:** touch newnote

**Q2.** On the deployable machine, what is the file type of "unknown1" in "tryhackme's" home directory?
**Answer:** ASCII Text

**Q3.** How would we move the file "myfile" to the directory "myfolder" 
**Answer:** mv myfile myfolder

**Q4.** What are the contents of this file?
**Answer:** THM{FILESYSTEM}

### Exercise 3 — [Permission 101]

**Q1.** Which group normally administrates all computers and resources in a domain?
**Answer:** Domain Admins

**Q2.** What would be the name of the machine account associated with a machine named TOM-PC?
**Answer:** TOM-PC$

**Q3.** Suppose our company creates a new department for Quality Assurance. What type of containers should we use to group all Quality Assurance users so that policies can be applied consistently to them?
**Answer:** Organizational Units

### Exercise 4 — [Common Directories]

**Q1.** The process of granting privileges to a user over some OU or other AD Object is called...
**Answer:** Delegation

### Exercise 5 — [Permission 101]

**Q1.** After organising the available computers, how many ended up in the Workstations OU?
**Answer:** 7

**Q2.** Is it recommendable to create separate OUs for Servers and Workstations? (yay/nay)
**Answer:** YAY

### Exercise 6 — [Permission 101]

**Q1.** Will a current version of Windows use NetNTLM as the preferred authentication protocol by default? (yay/nay)
**Answer:** nay

**Q2.** When referring to Kerberos, what type of ticket allows us to request further tickets known as TGS?
**Answer:** Ticket Granting Ticket

**Q3.** When using NetNTLM, is a user's password transmitted over the network at any point? (yay/nay)
**Answer:** nay

### Exercise 7 — [Permission 101]

**Q1.** What is a group of Windows domains that share the same namespace called?
**Answer:** tree

**Q2.** What should be configured between two domains for a user in Domain A to access a resource in Domain B?
**Answer:** A Trust Relationship

## Key Takeaways

In this room, we have shown the basic components and concepts related to Active Directories and Windows Domains. Keep in mind that this room should only serve as an introduction to the basic concepts, as there's quite a bit more to explore to implement a production-ready Active Directory environment.

## Notes

What is Windows Domain?
Windows Domain is a group of users and computers under the administration of a given business.

The main idea behind the domain is to centralise the administration of a common components of windows computer network in a single repository called Active Directory. The server that runs AD is called Domain Controller.

**Users:**
Users are one of the most common object types in Active Directory. Users are one of the objects known as security principals, meaning that they can be authenticated by the domain and can be assigned privileges over resources like files or printers. You could say that a security principal is an object that can act upon resources in the network.
     
**Machines:**
Machines are another type of object within Active Directory; for every computer that joins the Active Directory domain, a machine object will be created. Machines are also considered "security principals" and are assigned an account just as any regular user. This account has somewhat limited rights within the domain itself.

**Security Groups:**
If you are familiar with Windows, you probably know that you can define user groups to assign access rights to files or other resources to entire groups instead of single users. This allows for better manageability as you can add users to an existing group, and they will automatically inherit all of the group's privileges. Security groups are also considered security principals and, therefore, can have privileges over resources on the network.