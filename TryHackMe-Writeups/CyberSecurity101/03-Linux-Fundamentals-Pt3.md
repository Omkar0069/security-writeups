# Linux Fundamentals Part-3

## Overview

Power-up your Linux skills and get hands-on with some common utilities that you are likely to use day-to-day!

## What I Learned

Processes, cron, and stuff (Pretty hectic)

## Exercises

### Exercise 1 — [Flags]

**Q1.** What directional arrow key would we use to navigate down the manual page?
**Answer:** Down

**Q2.** What flag would we use to display the output in a "human-readable" way?
**Answer:** -h

### Exercise 2 — [File System]

**Q1.** How would you create the file named "newnote"?
**Answer:** touch newnote

**Q2.** On the deployable machine, what is the file type of "unknown1" in "tryhackme's" home directory?
**Answer:** ASCII Text

**Q3.** How would we move the file "myfile" to the directory "myfolder" 
**Answer:** mv myfile myfolder

**Q4.** What are the contents of this file?
**Answer:** THM{FILESYSTEM}

### Exercise 3 — [Permission 101]

**Q1.** What would the command be to switch to the user "user2"?
**Answer:** su user2

### Exercise 4 — [Common Directories]

**Q1.** What command would we use to bring a previously backgrounded process back to the foreground?
**Answer:** fg

**Q2.** If we were to launch a process where the previous ID was "300", what would the ID of this new process be?
**Answer:** 301

**Q3.** If we wanted to cleanly kill a process, what signal would we send it?
**Answer:** SIGTERM

**Q4.** What command would we use to stop the service "myservice"?
**Answer:** systemctl stop myservice

**Q5.** What command would we use to start the same service on the boot-up of the system?
**Answer:** systemctl enable myservice

**Q5.** What command would we use to bring a previously backgrounded process back to the foreground?
**Answer:** fg

## Key Takeaways

To recap, this room introduced you to the following topics:

    Using terminal text editors
    General utilities such as downloading and serving contents using a python webserver
    A look into processes
    Maintaining & automating your system by the use of crontabs, package management, and reviewing logs

## Notes

To copy file from remote system to local system: scp ubuntu@192.168.1.30:/home/ubuntu/documents.txt notes.txt 
To copy file from current system to remote system: scp important.txt ubuntu@192.168.1.30:/home/ubuntu/transferred.txt

To start a python server on your local machine enter: python3 -m http.server
To download content from that server, on another tab: wget http://10.49.143.104:8000/.flag.txt
To end the connection: Ctrl+C
