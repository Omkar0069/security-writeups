## `useradd`

**What it does:**
Creates a new user account on a Linux system. Requires root/sudo privileges. On its own it creates the account but usually doesn't set a password or a home directory the way you'd want — you typically pair it with flags (or with `passwd` right after, which is next).

**Syntax:**
```
sudo useradd username                  # bare minimum, often incomplete setup
sudo useradd -m username               # -m = create a home directory (/home/username)
sudo useradd -m -s /bin/bash username  # -s = set the login shell explicitly
sudo useradd -m -G sudo username       # -G = add to a supplementary group (here, sudo group)
sudo userdel -r username               # the removal counterpart, -r deletes home dir too
```

**Example:**
```
$ sudo useradd -m -s /bin/bash testuser
$ ls /home
omkar  testuser

$ id testuser
uid=1001(testuser) gid=1001(testuser) groups=1001(testuser)
```
Notice `testuser` has no password yet — the account exists but can't log in normally until you run `passwd testuser`, which is next.

**Why it matters for pentesting:**
On the offensive side, you'll rarely create users on a *target* (that's a very loud, easily-logged action you wouldn't do without explicit authorization in scope) — but you'll use it constantly in your **home lab** to simulate realistic scenarios: setting up low-privilege users to practice privesc against, or setting up a user without `-m` to demonstrate a misconfiguration in a report.
On the defensive/audit side, this is exactly the kind of command you're looking *for* in logs — an unexpected `useradd` in `/var/log/auth.log` or shell history is a strong sign of a compromise or a backdoor account being planted, since legitimate admin account creation is usually rare and well-documented.

**Notes / gotchas:**
Forgetting `-m` is the classic beginner trap — the user technically exists but has no home directory, which breaks a lot of expected behavior (no `.bashrc`, no default file locations). On some distros (Debian-based, including Kali), `useradd` is the low-level tool and `adduser` is a friendlier interactive wrapper around it — worth knowing both names exist, since walkthroughs use them interchangeably.

---

## `passwd`

**What it does:**
Sets or changes a user's password. Run without a username, it changes *your own* password. Run with `sudo` and a username, it sets/changes another user's password — which is exactly how you'd finish setting up the `testuser` account from the last command.

**Syntax:**
```
passwd                    # change your own password (prompts for current, then new)
sudo passwd username      # set/change another user's password (root doesn't need current pw)
sudo passwd -l username   # -l = lock the account (disable login)
sudo passwd -u username   # -u = unlock it
sudo passwd -e username   # -e = expire it now, forces password change on next login
```

**Example:**
```
$ sudo passwd testuser
New password: 
Retype new password: 
passwd: password updated successfully

$ id testuser
uid=1001(testuser) gid=1001(testuser) groups=1001(testuser)
```
`testuser` can now log in — the missing piece from the `useradd` step.

**Why it matters for pentesting:**
This is where `/etc/shadow` becomes relevant — `passwd` is what writes the hashed password into that file (which is why the `passwd` binary itself needs SUID, tying straight back to what you learned earlier). If you ever manage to read `/etc/shadow` on a target (root access or a misconfiguration), the hashes you extract get cracked with `John the Ripper` or `hashcat` — both later on your tools list.
In your home lab, `sudo passwd -l testuser` is a realistic way to simulate a disabled/locked account for practicing enumeration — you'll sometimes find locked accounts during a real engagement and need to correctly identify and report that they can't currently be used for login, versus one that can.

**Notes / gotchas:**
Weak/default passwords set via `passwd` during quick lab setups (like `testuser:password123`) are intentional practice fodder, but it's worth remembering *why* they're vulnerable in your reports later — this is the exact class of finding ("weak password policy") you'll be writing up against real clients.

---

## `groups`

**What it does:**
Shows which groups a user belongs to. Every user has one *primary* group and can belong to any number of *supplementary* groups. Group membership is what a lot of permission checks actually come down to — not just individual `chmod` rules, but whether you're *in the group* that has access to something.

**Syntax:**
```
groups                # show YOUR OWN group memberships
groups username        # show another user's group memberships
id username             # more detailed — shows UID, GID, and all groups with numeric IDs
```

**Example:**
```
$ groups testuser
testuser : testuser

$ sudo usermod -aG sudo testuser
$ groups testuser
testuser : testuser sudo

$ id testuser
uid=1001(testuser) gid=1001(testuser) groups=1001(testuser),27(sudo)
```
Adding `testuser` to the `sudo` group (via `usermod -aG`, a related command worth knowing even though it's not on your list) is literally how you grant a user admin rights on Debian-based systems like Kali — instead of editing config files directly.

**Why it matters for pentesting:**
This is a real enumeration step after landing any shell — `groups` or `id` tells you immediately what you can potentially access without needing to test permissions file-by-file. Being in the `docker` group, for instance, is a well-known privesc path (Docker access effectively means root, since you can mount the host filesystem into a container) — GTFOBins covers this too. Being in `sudo` or `wheel` obviously matters. Being in a custom app-specific group might grant you access to sensitive log files or configs.
`id` is usually the more useful command in practice — one line gives you UID, all group memberships with their numeric IDs, which you then cross-reference against `/etc/group` or `/etc/sudoers` if you can read it.

**Notes / gotchas:**
`groups` with no argument shows *your current effective* groups — but note that group membership changes don't take effect in an already-open shell session; you'd need to log out/in or start a new shell for a newly-added group to actually apply. This trips people up in labs when they add a user to a group and then wonder why `sudo` still doesn't work in the same terminal.

---

