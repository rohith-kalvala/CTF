Gobuster results on kioptrix using common.txt wordlist
```
┌──(kali㉿kali)-[~]
└─$ sudo gobuster dir -u http://192.168.232.129 -w /usr/share/dirb/wordlists/common.txt

===============================================================
Gobuster v3.8.2
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     http://192.168.232.129
[+] Method:                  GET
[+] Threads:                 10
[+] Wordlist:                /usr/share/dirb/wordlists/common.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.8.2
[+] Timeout:                 10s
===============================================================
Starting gobuster in directory enumeration mode
===============================================================
.hta                 (Status: 403) [Size: 268]
.htaccess            (Status: 403) [Size: 273]
.htpasswd            (Status: 403) [Size: 273]
~root                (Status: 403) [Size: 269]
~operator            (Status: 403) [Size: 273]
cgi-bin/             (Status: 403) [Size: 272]
index.html           (Status: 200) [Size: 2890]
manual               (Status: 301) [Size: 294] [--> http://127.0.0.1/manual/]
mrtg                 (Status: 301) [Size: 292] [--> http://127.0.0.1/mrtg/]
usage                (Status: 301) [Size: 293] [--> http://127.0.0.1/usage/]
Progress: 4613 / 4613 (100.00%)
===============================================================
Finished
===============================================================

```

Dirb directory bruteforcing using dirb tool with common.txt word list
```
┌──(kali㉿kali)-[~]
└─$ sudo dirb http://192.168.232.129 
[sudo] password for kali: 

-----------------
DIRB v2.22    
By The Dark Raver
-----------------

START_TIME: Sat Mar 21 23:46:49 2026
URL_BASE: http://192.168.232.129/
WORDLIST_FILES: /usr/share/dirb/wordlists/common.txt

-----------------

GENERATED WORDS: 4612                                                          

---- Scanning URL: http://192.168.232.129/ ----
+ http://192.168.232.129/~operator (CODE:403|SIZE:273)                                                          
+ http://192.168.232.129/~root (CODE:403|SIZE:269)                                                              
+ http://192.168.232.129/cgi-bin/ (CODE:403|SIZE:272)                                                           
+ http://192.168.232.129/index.html (CODE:200|SIZE:2890)                                                        
==> DIRECTORY: http://192.168.232.129/manual/                                                                   
==> DIRECTORY: http://192.168.232.129/mrtg/                                                                     
==> DIRECTORY: http://192.168.232.129/usage/                                                                    
                                                                                                                
---- Entering directory: http://192.168.232.129/manual/ ----
(!) WARNING: Directory IS LISTABLE. No need to scan it.                        
    (Use mode '-w' if you want to scan it anyway)
                                                                                                                
---- Entering directory: http://192.168.232.129/mrtg/ ----
+ http://192.168.232.129/mrtg/index.html (CODE:200|SIZE:17318)                                                  
                                                                                                                
---- Entering directory: http://192.168.232.129/usage/ ----
+ http://192.168.232.129/usage/index.html (CODE:200|SIZE:4278)                                                  
                                                                                                                
-----------------
END_TIME: Sat Mar 21 23:47:16 2026
DOWNLOADED: 13836 - FOUND: 6
