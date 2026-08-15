## `ip` — Network Interface & Routing Info

**What it does:**
Shows and manages network interfaces, IP addresses, and routing on the machine. It's the modern replacement for the older `ifconfig` — most current distros (including Kali) use `ip` now, so this is the one worth building muscle memory on.

**Syntax:**
```
ip a                    # show all interfaces and their IP addresses (shorthand for "ip addr")
ip addr show             # same as above, full form
ip route                 # show the routing table (what gateway traffic goes through)
ip link                  # show interfaces without IP details — link status only
ip link set eth0 up      # bring an interface up (requires sudo)
```

**Example:**
```
$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536
    inet 127.0.0.1/8 scope host lo
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500
    inet 192.168.1.105/24 brd 192.168.1.255 scope global eth0

$ ip route
default via 192.168.1.1 dev eth0
192.168.1.0/24 dev eth0 scope link
```
Reading this: your Kali box is `192.168.1.105`, on the `192.168.1.0/24` subnet, with `192.168.1.1` as the gateway.

**Why it matters for pentesting:**
Literally the first command you run before touching any target — `ip a` confirms which network you're actually on, which interface is active, and what your own IP is. This matters constantly: is your VM on the same subnet as the target lab machine? Are you connected to the VPN interface for a remote engagement (you'll often see a `tun0` interface appear once connected)? Misreading your own network position is a common beginner mistake that wastes hours scanning the wrong range.
`ip route` tells you the gateway — relevant for spotting whether you're behind NAT, and for understanding how traffic actually leaves your machine before you start troubleshooting a scan that isn't returning results.

**Notes / gotchas:**
Older tutorials and walkthroughs still show `ifconfig` — it still works if installed, but it's deprecated and `ip` is what you should default to. Worth recognizing `ifconfig` output if you see it in an older writeup, even though you'll practice with `ip`.

---

## `ss` — Socket Statistics

**What it does:**
Shows active network connections and listening ports on the machine — which services are actually reachable over the network right now. It's the modern replacement for the older `netstat`, similar story to `ip` replacing `ifconfig`.

**Syntax:**
```
ss -tuln         # the one you'll actually use — see below for what each letter does
ss -t              # TCP connections only
ss -u              # UDP connections only
ss -l              # listening sockets only
ss -n              # show numeric ports/addresses, don't resolve names (faster, clearer)
ss -p              # show the process using each socket (often needs sudo)
```
Breaking down `-tuln`: **t**cp + **u**dp + **l**istening + **n**umeric — the standard combo for "what's this machine actually serving right now."

**Example:**
```
$ ss -tuln
Netid  State    Local Address:Port    Peer Address:Port
tcp    LISTEN   0.0.0.0:22             0.0.0.0:*
tcp    LISTEN   127.0.0.1:3306         0.0.0.0:*
tcp    LISTEN   0.0.0.0:80             0.0.0.0:*
udp    UNCONN   0.0.0.0:68             0.0.0.0:*
```
Reading this: SSH (22) and HTTP (80) are listening on **all interfaces** (`0.0.0.0`) — reachable from the network. MySQL (3306) is bound only to `127.0.0.1` — only reachable from *this machine itself*, not externally. That distinction matters a lot.

**Why it matters for pentesting:**
This is the local-side mirror of what Nmap tells you from the outside — if you've landed a shell on a target, `ss -tuln` shows you services running that Nmap might've missed (things bound only to `127.0.0.1` are invisible to an external scan, but from inside the box you can see them, and sometimes reach them via port forwarding/SSH tunneling).
Comparing `0.0.0.0` vs `127.0.0.1` bindings is genuinely a reportable finding — a database or admin panel that *should* be localhost-only but is actually bound to `0.0.0.0` is an exposed-service misconfiguration you'd flag directly in a report.

**Notes / gotchas:**
Like `chown` needing root to change other users' files, `ss -p` (showing which process owns a socket) often needs `sudo` to see processes belonging to other users — without it, some entries just show blank instead of the process name. Also: `netstat` still appears in a lot of older guides and cheat sheets — recognize it, but default to `ss`.

No worries — let's just walk through your actual output line by line. This is a genuinely confusing wall of text at first, so let's slow down.

## What each tool is actually doing

- **Nmap** — sits on your Kali box, sends packets *across the network* to `192.168.122.201`, and reports back what answered. It's blind to anything on that box it can't reach network-wise.
- **`netstat -tulnp`** — ran *inside* Metasploitable2 itself, listing every socket the OS knows about, no network round-trip involved. It sees everything, period.

So the comparison is: "what did Nmap find from outside?" vs "what's actually there?"

## The interesting part — what showed up in netstat but NOT in your nmap scan

Look closely, this is the real finding:

```
tcp6   0   0   :::3632    :::*   LISTEN
```

**Port 3632 never appeared in your Nmap results at all.** That's `distccd` — and on Metasploitable2 specifically, that's one of the most famous vulnerabilities on the whole box (remote code execution, no auth needed). If you'd only trusted your Nmap scan, you'd have completely missed it.

**Why did Nmap miss it?** Two possible reasons, both worth understanding:
1. By default, Nmap only scans its **top 1000 most common ports** unless you tell it to scan everything. Port 3632 isn't in that default list.
2. It's listed under `tcp6` — bound to IPv6 (`:::3632`), and a plain `nmap -sV <IP>` only scans IPv4 by default.

**The fix — rescan properly:**
```bash
nmap -sV -p- 192.168.122.201
```
`-p-` means "scan all 65535 ports," not just the top 1000. Run that and see if 3632 shows up this time.

## The other real lesson — localhost-only services

Look at these two lines:
```
tcp    0   0   127.0.0.1:53    0.0.0.0:*   LISTEN
tcp6   0   0   ::1:953         :::*        LISTEN
```
`127.0.0.1` and `::1` both mean "localhost only." These are genuinely **invisible to Nmap no matter what**, because Nmap is coming from outside — there's no `-p-` flag or trick that reveals a service that's deliberately bound only to localhost. You can only see these by actually being on the box, exactly like you are right now over SSH.

**netstat revealed distccd on 3632 that the default Nmap scan missed — confirmed by rescanning with -p-.**

---

## `ping`

**What it does:**
Sends ICMP Echo Request packets to a target and waits for Echo Reply packets back. It's the most basic "is this thing alive and reachable" check in networking — before you scan anything, run any exploit, or troubleshoot anything, `ping` tells you whether there's even a live host to talk to.

**Syntax:**
```
ping target                # runs continuously until you Ctrl+C
ping -c 4 target             # -c = count, send only 4 packets then stop (best for scripts/quick checks)
ping -i 0.5 target            # -i = interval in seconds between packets
```

**Example:**
```
$ ping -c 4 192.168.122.201
PING 192.168.122.201 (192.168.122.201) 56(84) bytes of data.
64 bytes from 192.168.122.201: icmp_seq=1 ttl=64 time=0.234 ms
64 bytes from 192.168.122.201: icmp_seq=2 ttl=64 time=0.198 ms
64 bytes from 192.168.122.201: icmp_seq=3 ttl=64 time=0.211 ms
64 bytes from 192.168.122.201: icmp_seq=4 ttl=64 time=0.203 ms

--- 192.168.122.201 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3054ms
```
`ttl=64` is worth noticing — TTL (Time To Live) values often hint at the target's OS: Linux typically starts at 64, Windows typically starts at 128. Not definitive on its own, but a quick early clue.

**Why it matters for pentesting:**
Before running a full Nmap scan against a range, a quick `ping` sweep (or `nmap -sn`, the "ping scan" mode) tells you which hosts are even alive — no point scanning 254 addresses in a /24 if most are dead. It's also your first troubleshooting step when a scan returns nothing: is the target actually up, or is something wrong with your own network config (back to `ip a`)?

**Notes / gotchas:**
Many production networks and hardened targets **block ICMP** at the firewall level — a host can be very much alive and fully reachable on other ports, but simply not respond to `ping`. Don't conclude "host is down" just from a failed ping; a proper Nmap scan against specific ports will often prove otherwise. This trips up a lot of beginners who give up on a target too early.

---

## `traceroute`

**What it does:**
Shows the path — hop by hop — that packets take from your machine to a destination, listing every router/gateway along the way. It works by cleverly abusing TTL: it sends packets with TTL=1, then TTL=2, then TTL=3, and so on, so each hop along the route "expires" the packet and sends back an error, revealing itself in the process.

**Syntax:**
```
traceroute target             # standard usage
traceroute -n target           # -n = show IPs only, skip DNS lookups (faster, less noisy)
tracert target                  # Windows equivalent, different tool name, same idea
```

**Example:**
```
$ traceroute -n 8.8.8.8
traceroute to 8.8.8.8 (8.8.8.8), 30 hops max, 60 byte packets
 1  192.168.1.1     0.412 ms  0.398 ms  0.385 ms
 2  10.20.0.1       4.221 ms  4.198 ms  4.150 ms
 3  * * *
 4  142.250.65.1    12.882 ms  12.810 ms  12.795 ms
 5  8.8.8.8         13.104 ms  13.020 ms  12.998 ms
```
`* * *` means that hop didn't respond — usually a router configured to drop or ignore the probe, not necessarily a broken path (the trace still continues past it).

**Why it matters for pentesting:**
On a home lab against a single flat VM network, `traceroute` won't show much — you're usually one hop away. It becomes genuinely useful in larger, segmented environments (which matters more once you're doing internal network assessments, Level 6 on your roadmap) — mapping out network topology, spotting how many hops separate you from a target, and identifying if there's an unexpected router/firewall sitting in the path that might be filtering traffic.
It's also a basic sanity check when a scan or connection mysteriously fails partway — traceroute tells you whether the packets are even leaving your immediate network, versus dying somewhere further along the route.

**Notes / gotchas:**
Like `ping`, `traceroute` is commonly blocked or rate-limited by firewalls along the way — lots of `* * *` in real-world traces doesn't necessarily mean anything is broken, just that intermediate routers are configured not to respond. Don't over-read a trace full of asterisks as a failure.

---

## `curl`

**What it does:**
Transfers data to or from a URL directly from the command line — most commonly used to make HTTP requests and see exactly what a server sends back, without a browser rendering it and hiding the raw details from you.

**Syntax:**
```
curl url                        # GET request, prints the raw response body
curl -I url                      # -I = headers only, no body (quick check)
curl -v url                       # -v = verbose, shows the full request AND response, headers included
curl -X POST url -d "user=admin&pass=test"   # send a POST request with data
curl -o output.html url            # -o = save response to a file instead of printing
curl -H "Authorization: Bearer xyz" url  # -H = add a custom header
```

**Example:**
```
$ curl -I http://192.168.122.201
HTTP/1.1 200 OK
Date: Sun, 16 Aug 2026 02:30:11 GMT
Server: Apache/2.2.8 (Ubuntu) DAV/2
Last-Modified: Sat, 13 Aug 2026 14:02:33 GMT
Content-Type: text/html
```
That single command instantly confirms the exact Apache version — same info Nmap's `-sV` gave you, but straight from the source, and useful for double-checking or digging deeper than a version banner.

**Why it matters for pentesting:**
This is your go-to for **manually testing web behavior** without Burp's UI overhead — checking response headers for security misconfigurations (missing `X-Frame-Options`, no `Content-Security-Policy`, exposed `Server` version banners), testing whether an endpoint responds differently to GET vs POST, or quickly checking if a suspected vulnerable path exists (`curl http://target/admin/`) before firing up a full browser or Burp session.
It's also essential for scripting — when you start writing Python automation later, you'll often prototype the exact request in `curl` first (get it working, see the raw response) before translating it into Python's `requests` library.

**Notes / gotchas:**
By default `curl` follows the response as-is and does **not** follow redirects — if a server responds with a 301/302, you'll just see that redirect response, not the final page. Add `-L` (`curl -L url`) to make it follow redirects automatically. This trips people up when they curl a site and get a suspiciously short/empty response — check the status code first (`curl -I`) before assuming something's broken.

---


