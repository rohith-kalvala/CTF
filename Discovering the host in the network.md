## 🖥️ Identifying the IP Address of the Kali Linux Virtual Machine

To perform network-based activities such as scanning or enumeration, it is essential to first identify the IP address assigned to the Kali Linux virtual machine.
#### Using `ifconfig` Command

```
ifconfig
```

- Shows network interface details
    
- IP address is listed as `inet`

> ⚠️ Note: If `ifconfig` is not available, install it using:

```
sudo apt install net-tools
```

```
 ┌──(kali㉿kali)-[~]
└─$ ifconfig
                            
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.232.128  netmask 255.255.255.0  broadcast 192.168.232.255
        inet6 fe80::34c8:ce01:dda:68d2  prefixlen 64  scopeid 0x20<link>
        ether 00:0c:29:fc:ae:a6  txqueuelen 1000  (Ethernet)
        RX packets 3943  bytes 4287753 (4.0 MiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2724  bytes 271087 (264.7 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 130  bytes 41410 (40.4 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 130  bytes 41410 (40.4 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

## 🌐 Netdiscover Tool Usage

**Netdiscover** is a network reconnaissance tool used to identify live hosts within a local network by sending ARP requests. It is especially useful during the initial phase of penetration testing for discovering active devices.
```
sudo netdiscover -r 192.168.232.0/24

 Currently scanning: Finished!   |   Screen View: Unique Hosts               
                                                                             
 32 Captured ARP Req/Rep packets, from 4 hosts.   Total size: 1920           
 _____________________________________________________________________________
   IP            At MAC Address     Count     Len  MAC Vendor / Hostname      
 -----------------------------------------------------------------------------
 192.168.232.1   00:50:56:c0:00:08     27    1620  VMware, Inc.              
 192.168.232.2   00:50:56:ec:cc:0a      3     180  VMware, Inc.              
 192.168.232.129 00:0c:29:5d:53:3f      1      60  VMware, Inc.              
 192.168.232.254 00:50:56:ee:56:59      1      60  VMware, Inc. 
```
 
## 🌐 arp-scan Tool Usage

**arp-scan** is a fast and efficient network discovery tool used to identify live hosts on a local network by sending ARP (Address Resolution Protocol) requests.
```
┌──(kali㉿kali)-[~]
└─$ sudo arp-scan 192.168.232.0/24                         
Interface: eth0, type: EN10MB, MAC: 00:0c:29:fc:ae:a6, IPv4: 192.168.232.128
WARNING: Cannot open MAC/Vendor file ieee-oui.txt: Permission denied
WARNING: Cannot open MAC/Vendor file mac-vendor.txt: Permission denied
Starting arp-scan 1.10.0 with 256 hosts (https://github.com/royhills/arp-scan)
192.168.232.1   00:50:56:c0:00:08       (Unknown)
192.168.232.2   00:50:56:ec:cc:0a       (Unknown)
192.168.232.129 00:0c:29:5d:53:3f       (Unknown)
192.168.232.254 00:50:56:ee:56:59       (Unknown)

4 packets received by filter, 0 packets dropped by kernel


Ending arp-scan 1.10.0: 256 hosts scanned in 1.846 seconds (138.68 hosts/sec). 4 responded

```
## 🖥️ Device-by-Device Explanation

|IP Address|Role / Device|Activity (Count)|Description|
|---|---|---|---|
|**192.168.232.1**|Default Gateway / Virtual Router|High (27)|Connects the VM network to the outside (NAT/Host). Managed by VMware.|
|**192.168.232.2**|VMware DHCP / NAT Service|Low (3)|Assists in assigning IP addresses to virtual machines.|
|**192.168.232.129**|Kali Linux VM (Attacker Machine)|Very Low (1)|Your machine; low activity is normal when idle.|
|**192.168.232.254**|VMware Virtual Interface|Very Low (1)|Used for internal network management or broadcast functions.|

**Target Host: 192.168.232.129**
