# Linux Shell

## Overview

Learn about scripting and the different types of Linux shells.

## What I Learned

- Shell
- Variables
- Types
- Conditional Statements
- Loops
- Scripting

## Exercises

### Exercise 1 — [Introduction]

**Q1.** Who is the facilitator between the user and the OS?
**Answer:** Shell

### Exercise 2 — [How to interact with shell]

**Q1.** What is the default shell in most Linux distributions?
**Answer:** BASH

**Q2.** Which command utility is used to list down the contents of a directory?
**Answer:** ls

**Q3.** Which command utility can help you search for anything in a file?
**Answer:** grep

### Exercise 3 — [Types of shells]

**Q1.** Which shell comes with syntax highlighting as an out-of-the-box feature?
**Answer:** fish

**Q2.** Which shell does not have auto spell correction?
**Answer:**  bash

**Q3.** Which command displays all the previously executed commands of the current session?
**Answer:** history

### Exercise 4 — [Shell scripting and components]

**Q1.** What is the shebang used in a Bash script?
**Answer:** #!/bin/bash

**Q2.** Which command gives executable permissions to a script?
**Answer:**  chmod +x

**Q3.** Which scripting functionality helps us configure iterative tasks?
**Answer:** loops

### Exercise 5 — [Locker Script]

**Q1.** What would be the correct PIN to authenticate in the locker script?
**Answer:** 7385

### Exercise 6 — [Scripting]

**Q1.** Which file has the keyword?
**Answer:** authentication log

**Q2.** Where is the cat sleeping?
**Answer:** Under the Table


## Key Takeaways

In this room, we studied the importance of shells and flew to the world of linux shells, exploring their major types. We gained a good understanding of shell scripting and its role in automating tasks. In the end, we created some cool shell scripts and solved a practical lab pertaining to a script that finds mysterious things out of different directories.

## Notes

- BASH (Bourne Again Shell) is the default shell for most linux distos
- pwd: Prints Working Directory
- cd: Change Directory
- ls: Lists all the files and folders in current directory
- cat: Opens file in terminal
- grep: Find pattern in a file
- echo $SHELL: Prints the current shell name, you can also list down all the shells available in your OS: cat /etc/shells to switch between shell type the available shell in you terminal for e.g., zsh to make is permenant, chsh -s /usr/bin/zsh
- ./ - It is used to run script write this before the scriptname this tell the shell ts is a script . means ts is in current directory.