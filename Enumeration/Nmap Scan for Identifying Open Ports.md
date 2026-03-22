**Nmap** is a powerful network scanning tool used to identify open ports and services running on a target system.

```
┌──(kali㉿kali)-[~]
└─$ nmap -sS -p- -sV -T4 192.168.232.129
Starting Nmap 7.98 ( https://nmap.org ) at 2026-03-21 14:29 -0400
Nmap scan report for 192.168.232.129
Host is up (0.00083s latency).
Not shown: 65529 closed tcp ports (reset)
PORT      STATE SERVICE     VERSION
22/tcp    open  ssh         OpenSSH 2.9p2 (protocol 1.99)
80/tcp    open  http        Apache httpd 1.3.20 ((Unix)  (Red-Hat/Linux) mod_ssl/2.8.4 OpenSSL/0.9.6b)
111/tcp   open  rpcbind     2 (RPC #100000)
139/tcp   open  netbios-ssn Samba smbd (workgroup: MYGROUP)
443/tcp   open  ssl/https   Apache/1.3.20 (Unix)  (Red-Hat/Linux) mod_ssl/2.8.4 OpenSSL/0.9.6b
32768/tcp open  status      1 (RPC #100024)
MAC Address: 00:0C:29:5D:53:3F (VMware)

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 13.39 seconds
                                                             
```

## ⚙️ Option-by-Option Explanation

| Option            | Meaning                                                          |
| ----------------- | ---------------------------------------------------------------- |
| `-sS`             | 🔥 SYN (stealth) scan – half-open scan, fast and less detectable |
| `-p-`             | 🔓 Scan **all 65535 ports**                                      |
| `-sV`             | 🧪 Detect **service versions** running on open ports             |
| `-T4`             | ⚡ Faster scan timing (aggressive but stable)                     |
| `192.168.232.129` | 🎯 Target IP address                                             |
# 🧠 Priority Order (From the scan results )

1️⃣ **HTTP (80)** ← START HERE  
2️⃣ **HTTPS (443)**  
3️⃣ **SMB (139)**  
4️⃣ **SSH (22)**  
5️⃣ **RPC (111, 32768)**

**Nmap UDP scan on the first 1000 port**
```
┌──(kali㉿kali)-[~]
└─$ nmap -sU -p 0-1000 192.168.232.129  
Starting Nmap 7.98 ( https://nmap.org ) at 2026-03-21 14:40 -0400
Nmap scan report for 192.168.232.129
Host is up (0.00029s latency).
Not shown: 996 closed udp ports (port-unreach)
PORT    STATE         SERVICE
111/udp open          rpcbind
137/udp open          netbios-ns
138/udp open|filtered netbios-dgm
634/udp open|filtered ginad
771/udp open|filtered rtip
MAC Address: 00:0C:29:5D:53:3F (VMware)
```

