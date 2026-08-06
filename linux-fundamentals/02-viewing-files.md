## `cat` — Concatenate (Print/Combine files)

**What it does:**
Prints a file's entire contents straight to the terminal. Originally meant to concatenate multiple files together, but its most common use by far is just "show me what's in this file."

**Syntax:**
    cat filename                # print the whole file
    cat file1 file2             # print both, one after another (concatenated)
    cat file1 file2 > combined  # merge them into a new file
    cat -n filename             # -n = show line numbers
    cat >> filename             # append text you type directly into the file (Ctrl+D to stop)

**Example:**
10:49:10|omkar@kaliuser ~/linux-practical $ cat backup

**Why it matters for pentesting:**
The single most-used recon command on any shell you land: cat /etc/passwd to enumerate users, cat /etc/shadow if you have permissions (huge privesc signal if you can read it as non-root), cat ~/.bash_history to see what commands the legit user has been running.
cat is also how you quickly check small config files for hardcoded credentials — cat config.php, cat .env, cat wp-config.php are classic web pentest moves.

**Notes / gotchas:**
Important limitation: cat dumps everything at once with no scrolling control. Fine for a 10-line file, useless (and messy) for a 10,000-line log file — that's exactly the gap less fills, which is next.

---

## `less` — View File Page-by-Page

**What it does:**
Opens a file for scrollable, searchable reading, one screen at a time — without dumping the whole thing into your terminal like cat does. It doesn't load the entire file into memory either, so it handles huge files (multi-GB logs) instantly, where cat would flood your screen and choke.

**Syntax:**
    less filename

**Example:**
10:52:26|omkar@kaliuser ~/linux-practical $ less output.txt 

**Why it matters for pentesting:**
less /var/log/auth.log on a Linux target is a go-to for finding failed SSH login attempts, sudo usage history, or evidence of who's been logging in — all things that matter both offensively (finding valid usernames from failed attempts) and defensively (in a report, showing evidence of weak auth monitoring).
less is genuinely the safer default habit vs cat for any file you haven't checked the size of yet — cat-ing a massive log file by accident spams your terminal and can make it briefly unresponsive; less never has that problem.
Search (/pattern) inside less is faster than piping to grep when you're just eyeballing one file interactively rather than scripting.

**Notes / gotchas:**
Space / f     → next page
b             → previous page
/searchterm   → search forward for a word
n             → jump to next search match
N             → jump to previous search match
g             → jump to top of file
G             → jump to bottom of file
q             → quit

---

## `head` and `tail` — View Start / End of a File

**What it does:**
head shows the first N lines of a file (default 10). tail shows the last N lines (default 10). Both are for when you want a quick peek without opening the whole file like cat or less would.

**Syntax:**
head filename           # first 10 lines
head -n 20 filename     # first 20 lines
head -5 filename        # shorthand for -n 5

tail filename            # last 10 lines
tail -n 20 filename      # last 20 lines
tail -f filename         # -f = "follow" — keeps watching the file live as new lines get added

**Example:**
11:05:44|omkar@kaliuser ~/linux-practical $ tail -n +11 server.log  # Displays everything except the first 10 lines.

**Why it matters for pentesting:**
tail -f /var/log/auth.log is what you'd run in a spare terminal while doing a Hydra brute-force against SSH — you watch failed/accepted login attempts appear live, confirming exactly when a password hit or the target started blocking you.
head is the fast way to sanity-check a file's format before processing it further — e.g. head wordlist.txt to confirm a downloaded wordlist actually looks like a wordlist and isn't corrupted, before you point Hydra or Gobuster at a huge file.
Combo move you'll use constantly: tail -f on a log file in one pane while you actively attack the service in another — real-time feedback loop instead of checking logs after the fact.

**Notes / gotchas:**
tail -f is one of the crucial commands used to watch new entries live.

---

## `nano` and `vim` — Text Editors

**What it does:**
What they do: Unlike cat/less/head/tail, which only view files, these let you actually edit file contents directly in the terminal — no GUI needed. You'll use these constantly once you're SSH'd into a target or a headless VM with no desktop environment.

**Syntax:**
nano filename

vim filename

**Example:**
11:05:44|omkar@kaliuser ~/linux-practical $ tail -n +11 server.log  # Displays everything except the first 10 lines.

**Why it matters for pentesting:**
Editing exploit scripts directly on a target or your Kali box — changing an IP, port, or payload inside a downloaded exploit's source code before running it. nano exploit.py is often faster than transferring the file back and forth.
vim matters specifically because minimal/embedded Linux targets often don't have nano installed, but almost always have vi/vim. If you only know nano, you can get stuck unable to edit a config file on a stripped-down box. This is a real, common scenario — not hypothetical.
Editing config files for privilege escalation practice — e.g. modifying a cron job script you have write access to, or editing /etc/hosts during testing.

**Notes / gotchas:**
For nano:
Ctrl+O  → save (Write Out)
Ctrl+X  → exit
Ctrl+K  → cut a line
Ctrl+U  → paste
Ctrl+W  → search

For vim:
i          → enter INSERT mode (now you can type)
Esc        → leave insert mode, back to COMMAND mode
:w         → save (write)
:q         → quit
:wq        → save and quit
:q!        → quit WITHOUT saving (force-discard changes)
dd         → delete current line (command mode)
/pattern   → search

*The #1 beginner trap: opening vim, typing immediately, and having letters trigger commands instead of appearing as text — because you're still in command mode, not insert mode. Always press i first*

---