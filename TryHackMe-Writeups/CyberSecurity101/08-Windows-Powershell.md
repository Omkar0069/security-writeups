# Windows Powershell

## Overview

Discover the "Power" in PowerShell and learn the basics.

## What I Learned

- Powershell Scripting

## Exercises

### Exercise 1 — [Introduction]

**Q1.** What do we call the advanced approach used to develop PowerShell?
**Answer:** Object-Oriented

### Exercise 2 — [Powershell Basics]

**Q1.** How would you retrieve a list of commands that start with the verb Remove? [for the sake of this question, avoid the use of quotes (" or ') in your answer]
**Answer:** Get-Command -Name Remove*

**Q2.** What cmdlet has its traditional counterpart echo as an alias?
**Answer:** Write-Output

**Q3.** What is the command to retrieve some example usage for the cmdlet New-LocalUser?
**Answer:** get-help New-LocalUser -examples

### Exercise 3 — [Navigation]

**Q1.** What cmdlet can you use instead of the traditional Windows command type?
**Answer:** Get-Content

**Q2.** What PowerShell command would you use to display the content of the "C:\Users" directory? [for the sake of this question, avoid the use of quotes (" or ') in your answer]
**Answer:**  Get-ChildItem -Path C:\Users

**Q3.** How many items are displayed by the command described in the previous question?
**Answer:** 4

### Exercise 4 — [Piping filtering and sorting the data]

**Q1.** How would you retrieve the items in the current directory with size greater than 100? [for the sake of this question, avoid the use of quotes (" or ') in your answer]
**Answer:** Get-ChildItem | Where-Object -Property Length -gt 100

### Exercise 5 — [System and network information]

**Q1.** Other than your current user and the default "Administrator" account, what other user is enabled on the lab machine?
**Answer:** p1r4t3

**Q2.** This lad has hidden his account among the others with no regard for our beloved captain! What is the motto he has so bluntly put as his account's description?
**Answer:** A merry life and a short one

### Exercise 6 — [Scripting]

**Q1.** What is the syntax to execute the command Get-Service on a remote computer named "RoyalFortune"? Assume you don't need to provide credentials to establish the connection. [for the sake of this question, avoid the use of quotes (" or ') in your answer]
**Answer:** Invoke-Command -ComputerName RoyalFortune -ScriptBlockd { Get-Service }


## Key Takeaways

Well done, mateys! You’ve successfully navigated the treacherous waters of , uncovering hidden treasures and elusive services aboard TheBlackPearl.

## Notes

What is Powershell?
Powershell is a powerful tool from microsoft designed for task automation and configuration management.

What is Framework?
Framework is a built in structure/toolkit that helps you build application without creating everything from scratch.

Powershell commands are known as cmdlets(Command-lets)