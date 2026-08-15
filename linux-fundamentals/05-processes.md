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

## `top` — Live Process Monitor

**What it does:**
Like `ps aux`, but live and continuously updating instead of a one-time snapshot — you get a real-time, refreshing view of running processes, CPU usage, and memory usage, sorted by resource consumption by default.

**Syntax:**
```
top                # launch the live monitor
```
Once inside, useful keys:
```
q          → quit
P          → sort by CPU usage (default)
M          → sort by memory usage
k          → kill a process (prompts for PID)
1          → toggle per-core CPU breakdown
```

**Example:**
```
$ top
top - 12:45:01 up 2:15,  1 user,  load average: 0.15, 0.10, 0.05
Tasks:  98 total,   1 running,  97 sleeping
%Cpu(s):  2.3 us,  1.1 sy,  0.0 ni, 96.4 id
MiB Mem :   3900 total,   1200 free,   900 used,  1800 buff/cache

  PID USER      PR  NI    VIRT    RES  %CPU  %MEM  COMMAND
  842 root      20   0   15200   3120   0.3   0.1  sshd
 1120 omkar     20   0  305000  85000   2.1   2.2  burpsuite
 1550 root      20   0   45000  12000   1.8   0.3  nmap
```
That live view lets you watch, for example, a scan you just launched actually consuming CPU in real time, or spot a process that suddenly spikes.

**Why it matters for pentesting:**
Less of a direct exploitation tool and more a diagnostic one — during a heavy scan (Nmap, Gobuster, Hydra) that's taking forever, `top` tells you whether your own machine is the bottleneck (maxed CPU/RAM) versus the network or target being slow. Useful for not wasting hours assuming a tool is hung when it's actually just resource-starved.
On a target, if you land a shell and run `top`, you can sometimes spot **defensive tooling actively running** (antivirus scans, log monitoring agents consuming CPU) or catch a legitimate admin's session actively doing something in real time — both relevant to how carefully you need to move.

**Notes / gotchas:**
`top`'s interface varies slightly by distro, and many people upgrade to `htop` (not on your list but worth knowing exists) for a cleaner, color-coded, scrollable version of the same thing — same core purpose, nicer UX. Worth trying both once you're comfortable with `top`'s basics.

---

## `kill`

**What it does:**
Sends a signal to a process, most commonly to terminate it. "Kill" is a bit of a misnomer — it actually sends a *signal*, and termination is just the most common signal used; processes can also be paused, resumed, or asked to gracefully shut down via different signals.

**Syntax:**
```
kill PID              # sends SIGTERM (15) — polite request to terminate
kill -9 PID            # sends SIGKILL (9) — force kill, no cleanup, cannot be ignored
kill -l                 # list all available signals
killall processname     # kill by process NAME instead of PID (kills all matching)
pkill processname        # similar to killall, pattern-based matching
```

**Example — chaining with `ps` from earlier:**
```
$ ps aux | grep burpsuite
omkar     1120  2.1  2.2  305000  85000 pts/1 Sl+ 12:30 0:45 burpsuite

$ kill 1120
$ ps aux | grep burpsuite
                              # gone — no output

$ kill -9 1120                # if it had been unresponsive, force kill instead
```

**Why it matters for pentesting:**
Directly useful when a tool hangs — Hydra stuck mid-brute-force, a reverse shell listener that won't die, Burp eating all your RAM. `ps aux | grep` to find the PID, then `kill` (or `kill -9` if it's truly frozen) is the standard fix, faster than closing and reopening a terminal.
On a target, if you're simulating a red-team scenario, `kill` can be used to stop a monitoring or logging process you've identified via `ps aux` — though in a real authorized engagement this is something you'd only do within explicit scope, since killing defensive tooling is a significant, loggable action with real consequences if it's outside what the client agreed to.

**Notes / gotchas:**
`kill -9` should be your *last resort*, not your default — it doesn't let the process clean up (close files, release locks, save state), which can occasionally leave things in a messier state than a normal `kill`. Try plain `kill` first, and only escalate to `-9` if the process genuinely won't respond.

---

## `jobs`, `bg`, `fg` — Job Control

**What it does:**
These three manage processes you started **from your own terminal**, letting you pause, background, or bring them back to the foreground without killing them — different from `kill`, which ends a process entirely. Useful for running something long without tying up your terminal.

**Syntax:**
```
Ctrl+Z              # suspend the currently running foreground process
jobs                # list all background/suspended jobs in this terminal session
bg                  # resume the most recently suspended job, IN THE BACKGROUND
bg %2                # resume job number 2 specifically, in the background
fg                  # bring the most recent background job back to the FOREGROUND
fg %2                # bring job number 2 specifically to the foreground
command &            # start a command directly in the background from the start
```

**Example:**
```
$ nmap -p- 192.168.1.50 -oN fullscan.txt
^Z
[1]+  Stopped                 nmap -p- 192.168.1.50 -oN fullscan.txt

$ jobs
[1]+  Stopped                 nmap -p- 192.168.1.50 -oN fullscan.txt

$ bg %1
[1]+ nmap -p- 192.168.1.50 -oN fullscan.txt &

$ ls -la          # terminal is free again, scan runs in background
...

$ fg %1            # bring it back to check progress or when it's near done
```

**Why it matters for pentesting:**
This is exactly the pattern for long-running scans — a full-port Nmap scan (`-p-`) can take 20+ minutes. Instead of opening a whole new terminal tab, `Ctrl+Z` then `bg` frees up your current terminal to keep working while the scan runs, and `jobs` lets you check on it without losing your place.
Starting something directly in the background from the outset (`nmap -p- target &`) is even more common in practice than suspend-then-background — you'll use `&` constantly once scans become routine, especially when you're running multiple tools against the same target in parallel.

**Notes / gotchas:**
Jobs are tied to your **specific terminal session** — closing that terminal kills background jobs unless you've used something like `nohup` or `screen`/`tmux` to detach them properly (not on your list yet, but worth knowing they exist for genuinely long unattended scans). Don't confuse this with `tmux`, which is the actual professional solution for surviving disconnects — job control is more for quick, same-session multitasking.

---

