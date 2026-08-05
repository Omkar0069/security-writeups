## `pwd` — Print Working Directory

**What it does:**
Prints the absolute path of the current directory.

**Syntax:**
    pwd

**Example:**
    $ pwd
    /home/omkar

**Why it matters for pentesting:**
First command to run after landing a shell — tells you where you are
on the filesystem before you do anything else.

**Notes / gotchas:**
- `pwd -P` for resolving symlinks

---

## `ls` — List

**What it does:**
Lists the contents (files and folders) of a directory. By default, it shows what's in your current directory — the one pwd just told you about.

**Syntax:**
    ls

**Example:**
    $ ls
    backup  saved


**Why it matters for pentesting:**
ls -la after landing a shell on a target is your second move (right after pwd) — the -a flag matters a lot here, because attackers hide things in dotfiles, and defenders' leftover credentials often sit in hidden config files (.bash_history, .ssh/, .env) that plain ls won't show you.

**Notes / gotchas:**
- ls              # basic list
- ls -l           # long format: permissions, owner, size, date
- ls -a           # show hidden files too (anything starting with .)
- ls -la          # combine both — this is the one you'll use constantly
- ls -lh          # -l but with human-readable sizes (KB/MB instead of bytes)

---

## `cd` — Change Directory

**What it does:**
Moves you into a different directory — changes what pwd will report and what ls will show..

**Syntax:**
    cd foldername

**Example:**
00:42:03|omkar@kaliuser ~ $ pwd
/home/omkar

00:42:05|omkar@kaliuser ~ $ cd linux-practical/

00:42:08|omkar@kaliuser ~/linux-practical $ pwd
/home/omkar/linux-practical

**Why it matters for pentesting:**
cd /var/www/html is almost muscle memory on any compromised web server — that's where the webroot usually lives, and it's often writable.
cd - is genuinely useful when you're bouncing between a web directory and a temp/loot folder repeatedly during an engagement — saves retyping full paths.

**Notes / gotchas:**
- cd foldername     # go into a subfolder of where you are
- cd ..              # go up one level (to the parent directory)
- cd ../..           # go up two levels
- cd                 # no argument = jump straight to your home directory
- cd ~               # same thing — ~ always means home
- cd -               # jump back to the PREVIOUS directory you were in
- cd /               # go to root of the filesystem

---

## `cp` — Copy

**What it does:**
Copies a file (or folder) from one location to another, leaving the original in place. Different from mv, which we'll hit next — cp duplicates, it doesn't relocate.

**Syntax:**
    cp source destination          # copy a single file
    cp -r source_folder dest_folder  # -r = recursive, REQUIRED for copying folders
    cp file1 file2 dest_folder/    # copy multiple files into a folder
    cp -v source destination       # -v = verbose, shows what's happening (good while learning)

**Example:**
00:46:46|omkar@kaliuser ~/linux-practical $ cp backup ..
(copies to one directory up)

**Why it matters for pentesting:**
Before modifying any exploit script or config, cp file.py file.py.bak is a cheap safety net — you don't want to break a working exploit mid-engagement with no way back.
On an engagement, you'll cp evidence (log files, config files, hashes you found) into a dedicated loot/ folder as you go, so your report-writing later has everything in one place instead of scattered across the filesystem.
Forgetting -r on a folder is the single most common beginner mistake here — cp will just error out ("omitting directory") if you try to copy a folder without it.

---

## `mv` — Move (or rename)

**What it does:**
Moves a file/folder to a new location — or renames it if the "new location" is just a new name in the same directory. Unlike cp, the original is gone from its old spot; nothing is duplicated.

**Syntax:**
    mv source destination             # move a file into a folder
    mv oldname newname                # rename (same folder = rename, not move)
    mv -v source destination          # verbose, shows what happened
    mv file1 file2 file3 dest_folder/ # move multiple files at once

**Example:**
00:47:11|omkar@kaliuser ~ $ mv backup linux-practical/

**Why it matters for pentesting:**
After downloading a tool or exploit onto a target (or into your Kali box), files often land in ~/Downloads or /tmp — mv is how you organize them into your working directory without leaving a duplicate cluttering the source.
No -r flag needed for folders like cp requires — mv handles folders natively, which trips people up when they instinctively add -r out of habit.

**Notes / gotchas:**
Careful with mv onto an existing filename — it overwrites silently by default (no warning). This is a classic way to accidentally destroy loot or a working exploit. mv -i (interactive) prompts before overwriting — worth building as a habit early.

---

## `rm` — Remove

**What it does:**
Deletes files or directories. Unlike a GUI trash bin, there's no undo — rm deletes for real, immediately.

**Syntax:**
    rm filename           # delete a file
    rm -r foldername      # -r = recursive, required to delete a folder and its contents
    rm -f filename        # -f = force, no confirmation prompt even on protected files
    rm -rf foldername     # the infamous combo — recursive + force, deletes without asking
    rm -i filename         # -i = interactive, asks "are you sure?" before each delete

**Example:**
00:57:07|omkar@kaliuser ~/linux-practical $ rm backup

**Why it matters for pentesting:**
Cleaning up after yourself matters more than you'd think — in a real engagement, leaving tools, uploaded webshells, or temp files on a client's system is bad practice (and sometimes explicitly required to be cleaned up per the rules of engagement). rm is how you tidy up before closing out a target.
No -r needed for a single file, same rule as cp: rm file.txt alone; rm -r folder/ for directories.

**Notes / gotchas:**
rm -rf is genuinely dangerous — it's the command behind almost every "I deleted my entire home directory" horror story, especially if a space goes in the wrong place (rm -rf / home instead of rm -rf /home is a legendary example — the space turns it into "delete root, and also try to delete a folder called home"). Get in the habit of running pwd and ls right before any rm -r, not after.

---

## `mkdir` — Make Directory

**What it does:**
Creates a new, empty directory (folder).

**Syntax:**
    mkdir foldername              # create one folder
    mkdir folder1 folder2 folder3 # create multiple at once
    mkdir -p parent/child/grandchild  # -p = create nested folders in one shot, even if parent doesn't exist yet

**Example:**
01:01:15|omkar@kaliuser ~/linux-practical $ mkdir temp

**Why it matters for pentesting:**
mkdir -p is exactly how you set up a clean engagement structure fast — e.g. mkdir -p target1/{recon,exploits,loot,screenshots} (that curly-brace trick creates all four subfolders in one line — we'll cover that expansion syntax properly when we hit bash).
Keeping scans, loot, and screenshots in separate dated folders from the start saves you real pain later when you're writing the report and need to reference exactly which scan produced which finding.

**Notes / gotchas:**
Without -p, that second command would've failed with "No such file or directory" — mkdir normally refuses to create a folder if its parent doesn't exist yet.

---

## `touch` — Create Empty File / Update Timestamp

**What it does:**
Creates a new, empty file if it doesn't exist. If the file already exists, touch doesn't erase it — it just updates the file's "last modified" timestamp.

**Syntax:**
    touch filename                 # create an empty file
    touch file1 file2 file3        # create multiple empty files at once
    touch -t 202608061200 file.txt # manually set a specific timestamp (rare, but useful)

**Example:**
01:01:24|omkar@kaliuser ~/linux-practical $ touch kids

**Why it matters for pentesting:**
Quickly scaffolding a folder structure before you start work — touch notes.txt findings.txt gives you empty files ready to fill in as you go, rather than creating them mid-task and breaking flow.
The timestamp-editing use (-t) shows up in a slightly different context: understanding that attackers can use touch to backdate files and cover tracks (e.g., matching a malicious file's timestamp to legitimate system files so it doesn't stand out in a directory listing sorted by date). Worth knowing defensively — it's why forensic investigators don't fully trust mtime alone.

**Notes / gotchas:**
Also commonly used just to test if you have write permissions in a directory: touch testfile && rm testfile — if it works, you can write there.

---