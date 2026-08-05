## `cat` — Create Empty File / Update Timestamp

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