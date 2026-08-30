# Inside a Computer System

## Overview

This room explains the basics of Operating System.

## What I Learned

OS sits between user and hardware
USER -> APPLICATIONS -> **OPERATING SYSTEM** -> HARDWARE

OS RESPONSIBILITIES: Process Management, Memory Management, File System Management, User Management, Device Management

Two types of user interface: Graphical User Interface(GUI) and Command Line Interface(CLI)

Types of OS:
- Desktop: Personal computers, daily work, gaming, content creation
- Server: Web hosting, databases, cloud services, back-end
- Mobiles: Smartphones and tablets
- Embedded: Appliances, cars, IoT devices, smart TVs, routers
- Virtual/Cloud: Lab machines, containers, cloud instances

## Exercises

### Exercise 1 — [Invisible Manager]

**Q1.** Which OS space has unrestricted access to your computer's hardware?
**Answer:** Kernel Space

**Q2.** Which OS responsibility manages user accounts, authentication, and permissions?
**Answer:** User Management

**Q3.** After opening the About This Computer shortcut, you are greeted with an overview of the system's specifications.
What version of Ubuntu Mate is your computer running?
**Answer:** 1.26.2

**Q4.** Check out the Hardware section of the System tab.
How much memory is allocated to your machine?
**Answer:** 1.9 GiB

### Exercise 2 — [OS Interaction and Landscape]

**Q1.** Open the File Systems tab in System Monitor.What Type is listed for the /dev/root device?
**Answer:** ext4

**Q2.** After opening the Home directory on the Desktop, how many user directories exist?
**Answer:** 3

**Q3.** Navigate to Alex's home directory and explore the Documents folder.What is the flag value contained in note.txt?
**Answer:** THM{new_pc_for_free!}

**Q4.** How does UEFI know which device to boot from?
**Answer:** It follows a configured boot priority list

**Q5.** What does the bootloader do?
**Answer:** Loads the operating system into ram

## Key Takeaways

- A computer consists of multiple hardware components that work together.
- The CPU processes instructions while RAM provides temporary working memory.
- Storage keeps data even after the computer is powered off.

## Notes

**What is bootloader?**
Think of a bootloader as a stage manager at a theater:
It prepares the stage (initializes hardware).
Makes sure the actors are ready (checks the software).
Brings the actors onto the stage (loads the OS/application).
Then steps aside and lets the performance begin (hands control to the operating system or application).

**What is Firmware?**
Firmware is software that is stored on a piece of hardware and is responsible for controlling or initializing that hardware.