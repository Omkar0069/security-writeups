# Windows Fundamentals Part-2

## Overview

In part 2 of the Windows Fundamentals module, discover more about System Configuration, UAC Settings, Resource Monitoring, the Windows Registry and more..

## What I Learned

Various tools in windows system. Didnt got much like part 1 but still something is better than nothing.

## Exercises

### Exercise 1 — [System Configuration and Advanced System Settings]

**Q1.** What is the name of the service that lists Systems Internals as the manufacturer?
**Answer:** PsShutDown

**Q2.** Whom is the Windows license registered to?
**Answer:** Windows User

**Q3.** What is the command for Windows Troubleshooting?
**Answer:** C:\Windows\System32\control.exe /name Microsoft.Troubleshooting

**Q4.** What command will open the Control Panel? (The answer is  the name of .exe, not the full path)
**Answer:** Control.exe

### Exercise 2 — [Change UAC Settings]

**Q1.** What is the command to open User Account Control Settings? (The answer is the name of the .exe file, not the full path)
**Answer:** UserAccountControlSettings.exe

### Exercise 3 — [Computer Management]

**Q1.** What is the command to open Computer Management?
**Answer:** compmgmt.msc

**Q2.** When is the npcapwatchdog scheduled task set to run at?
**Answer:** At System Startup

**Q3.** What is the name of the hidden folder that is shared?
**Answer:** sh4r3dF0Ld3r

### Exercise 4 — [System Information]

**Q1.** What is the command to open System Information? (The answer is the name of the .exe file, not the full path)
**Answer:** msinfo32.exe

**Q2.** What is listed under System Name?
**Answer:** THM-WINFUN2

**Q3.** Under Environment Variables, what is the value for ComSpec?
**Answer:** %SystemRoot%\system32\cmd.exe

### Exercise 5 — [Resource Monitor]

**Q1.** What is the command to open Resource Monitor? (The answer is the name of the .exe file, not the full path)
**Answer:** resmon.exe

### Exercise 6 — [Command Prompt]

**Q1.** In System Configuration, what is the full command for Internet Protocol Configuration?
**Answer:** C:\Windows\System32\cmd.exe /k %windir%\system32\ipconfig.exe

**Q2.** For the ipconfig command, how do you show detailed information?
**Answer:** ipconfig/all

## Key Takeaways

 Throughout the room, commands and shortcuts were shared for the utilities. This means you don't have to launch MSConfig to run these utilities. 

## Notes

The system configuration utility (MSConfig) is advanced troubleshooting, its main purpose is to help diagnose the startup. More more info visit [here](https://learn.microsoft.com/en-us/troubleshoot/windows-client/performance/system-configuration-utility-troubleshoot-configuration-errors)
Five utilities in MSConfig: General, Boot, Services, Startup, Tools