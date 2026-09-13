# Windows Command Line

## Overview

Learn the essential Windows commands.

## What I Learned

Some essential Networking commands in Windows.

## Exercises

### Exercise 1 — [Introduction]

**Q1.** What is the default command line interpreter in the Windows environment?
**Answer:** cmd.exe

### Exercise 2 — [Basic Information]

**Q1.** What is the OS version of the Windows VM?
**Answer:** 10.0.20348.2655

**Q2.** What is the hostname of the Windows VM?
**Answer:** WINSRV2022-CORE

### Exercise 3 — [Network Troubleshooting]

**Q1.** Which command can we use to look up the server’s physical address (MAC address)?
**Answer:** ipconfig /all

**Q2.** What is the name of the service listening on port 135?
**Answer:** RpcSs

**Q3.** What is the name of the service listening on port 3389?
**Answer:** TermService

### Exercise 4 — [Task and Process Management]

**Q1.** What command would you use to find the running processes related to notepad.exe?
**Answer:** tasklist /FI "imagename eq notepad.txt"

**Q2.** What command can you use to kill the process with PID 1516?
**Answer:** taskill PID 1516

### Exercise 5 — [Conclusion]

**Q1.** The command shutdown /s can shut down a system. What is the command you can use to restart a system?
**Answer:** shutdown /r

**Q2.** What command can you use to abort a scheduled system shutdown?
**Answer:** shutdown /a


## Key Takeaways

/? is essential incase you don't know the use of the commmand.

## Notes

Benefits of using CLI: Lower Resource Usage, Automation, Remote Management
set: To check the path of command line
ver: To check the version of the operating system
systeminfo: To list detailed info about the system
del/erase: Used to delete file
tasklist: Like a taskmanager, list all the current tasks