## `ps` — Process Status

**What it does:**
Shows a snapshot of currently running processes. By default, `ps` alone only shows processes tied to your current terminal session — you almost always pair it with flags to see the whole system, which is what makes it actually useful.

**Syntax:**
```
ps                    # only processes in your current shell — rarely useful alone
ps aux                # THE one you'll actually use: all processes, all users, detailed
ps -ef                # alternative full-format listing, same idea, different style
ps aux | grep name     # filter for a specific process by name
```

**Example:**
```
$ ps aux | grep ssh
root       842  0.0  0.1  15200  3120 ?        Ss   09:01   0:00 /usr/sbin/sshd -D
omkar     2210  0.0  0.0   6400   700 pts/0    S+   12:41   0:00 grep --color=auto ssh
```
Reading `ps aux` columns: **USER** (who owns it), **PID** (process ID — you'll need this for `kill`), **%CPU / %MEM** (resource usage), **COMMAND** (what's actually running).

**Why it matters for pentesting:**
On a target, `ps aux` (or `ps -ef` if `aux` isn't available on a minimal system) is core enumeration — you're looking for processes running **as root** that you might be able to interact with or exploit, cron jobs actively executing, or security tooling (antivirus, EDR, monitoring agents) that tells you what you're up against and how careful you need to be.
It's also how you spot a process running a service with a **guessable or hardcoded credential in its command line** — some poorly-written services literally pass passwords as command-line arguments, and `ps aux` reveals the full command including those arguments to anyone who can run it.

**Notes / gotchas:**
On heavily locked-down or containerized targets, `ps aux` sometimes only shows *your own* processes even with the full flags, because of namespace isolation — don't assume the box is empty of other processes just because `ps` looks sparse; that itself is a signal worth noting (containerized environment).

---
