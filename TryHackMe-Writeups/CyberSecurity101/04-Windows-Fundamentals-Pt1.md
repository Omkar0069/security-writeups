# Windows Fundamentals Part-1

## Overview

In part 1 of the Windows Fundamentals module, we'll start our journey learning about the Windows desktop, the NTFS file system, UAC, the Control Panel, and more..

## What I Learned

- Windows Overview

## Key Takeaways

Again, this was a generic overview of the Windows OS. 

There are intermediate and advanced topics for each topic (task) that was covered in this room. 

Hence, Task 9 ended with a detailed blog post explaining the Task Manager in great detail. 

In future modules, we'll cover topics like the Windows folder, the management console, security tools (Windows Defender, Windows , Firewall etc.), to name a few. 

## Notes

Environment variables store information about the operating system environment. This information includes details such as the operating system path, the number of processors used by the operating system, and the location of temporary folders

Windows Vista was a sucessed of WindowsXP - But it was quickly phased out as it was not received well by the users.

Windows 11 comes in two flavours home and pro. The major difference is Bitlocker Driver Encryption which means if your device is lost or stolen bitlocker put everything on lockdown, so no one could access your data. It comes with pro version and is not available on home version.

Components of Windows OS:
1. Desktop
2. Start Menu
3. Search Box
4. Task View
5. Taskbar
6. Toolbars
7. Notification Areas

The 3 types of file systems are: FAT, NTFS and HPFS

Per Microsoft (opens in new tab), " Environment variables store information about the operating system environment. This information includes details such as the operating system path, the number of processors used by the operating system, and the location of temporary folders ". 

WindowsOS is stored in C:\Windows it can be stored anywhere but the standard location in this
System32 contains all the internal files of WindowsOS one should handle this file very carefully and run antivirus scan regularly as most malware are hidden here C:\Windows\System32

Each user has its own profile stored in C:\Users\Max (Here user Max is stored in Users folder)

UAC(User Account Control): When a user with account type of adminitrator logs into a system, the current session doesn't run with elevated permissions. When an operation with high previliges need to execute it will prompt the user to confirm that they permit the operation to run.