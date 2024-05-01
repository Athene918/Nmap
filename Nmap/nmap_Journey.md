![Nmap](https://miro.medium.com/v2/resize:fit:720/format:webp/1*Gp5Er4NK9P4Lq3Q0imjdqg.jpeg)
## Pour voir la dernière version de nmap:
 nmap -V
 
 ================================================
 ## nmap -v :

````bash
 
 ┌──(root㉿kali)-[~/nmap/zenmap]
└─# nmap -v 10.0.2.6
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 04:34 EDT
Initiating ARP Ping Scan at 04:34
Scanning 10.0.2.6 [1 port]
Completed ARP Ping Scan at 04:34, 0.07s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 04:34
ipToPtr: 10.0.2.6 => 6.2.0.10.in-addr.arpa
Completed Parallel DNS resolution of 1 host. at 04:34, 0.50s elapsed
Initiating SYN Stealth Scan at 04:34
Scanning 10.0.2.6 [1000 ports]
Completed SYN Stealth Scan at 04:34, 21.83s elapsed (1000 total ports)
Nmap scan report for 10.0.2.6
Host is up (0.0017s latency).
All 1000 scanned ports on 10.0.2.6 are in ignored states.
Not shown: 1000 filtered tcp ports (no-response)
MAC Address: 08:00:27:67:BA:E7 (PCS Systemtechnik/Oracle VirtualBox virtual NIC)

Read data files from: /usr/local/bin/../share/nmap
Nmap done: 1 IP address (1 host up) scanned in 22.50 seconds
           Raw packets sent: 2001 (88.028KB) | Rcvd: 1 (28B)
============================================================
````

nmap 10.0.2.6 : permet d'afficher tous les ports dispo

````bash

┌──(root㉿kali)-[~/nmap/zenmap]
└─# nmap 10.0.2.6    
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 04:38 EDT
ipToPtr: 10.0.2.6 => 6.2.0.10.in-addr.arpa
Nmap scan report for 10.0.2.6
Host is up (0.0014s latency).
All 1000 scanned ports on 10.0.2.6 are in ignored states.
Not shown: 1000 filtered tcp ports (no-response)
MAC Address: 08:00:27:67:BA:E7 (PCS Systemtechnik/Oracle VirtualBox virtual NIC)

Nmap done: 1 IP address (1 host up) scanned in 22.45 seconds
````

=============================================================

nmap 10.0.2.6 10.188.7.141 : Permet de scanner plusieurs ip

````bash
┌──(root㉿kali)-[~/nmap/zenmap]
└─# nmap 10.0.2.6 10.188.7.141
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 04:42 EDT
ipToPtr: 10.0.2.6 => 6.2.0.10.in-addr.arpa
ipToPtr: 10.188.7.141 => 141.7.188.10.in-addr.arpa
Nmap scan report for 10.0.2.6
Host is up (0.00076s latency).
All 1000 scanned ports on 10.0.2.6 are in ignored states.
Not shown: 1000 filtered tcp ports (no-response)
MAC Address: 08:00:27:67:BA:E7 (PCS Systemtechnik/Oracle VirtualBox virtual NIC)

Nmap scan report for 10.188.7.141
Host is up (0.0014s latency).
Not shown: 996 filtered tcp ports (no-response)
PORT    STATE SERVICE
80/tcp  open  http
135/tcp open  msrpc
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds

Nmap done: 2 IP addresses (2 hosts up) scanned in 27.44 seconds

======================================================
````
nmap 10.188.7.141/8: permet de scanner un subnet

````bash
┌──(root㉿kali)-[~/nmap/zenmap]
└─# nmap 10.188.7.141/8
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 04:44 EDT
ipToPtr: 10.0.0.0 => 0.0.0.10.in-addr.arpa
ipToPtr: 10.0.0.1 => 1.0.0.10.in-addr.arpa
ipToPtr: 10.0.0.2 => 2.0.0.10.in-addr.arpa
ipToPtr: 10.0.0.3 => 3.0.0.10.in-addr.arpa
ipToPtr: 10.0.0.4 => 4.0.0.10.in-addr.arpa
ipToPtr: 10.0.0.5 => 5.0.0.10.in-addr.arpa
ipToPtr: 10.0.0.6 => 6.0.0.10.in-addr.arpa
ipToPtr: 10.0.0.7 => 7.0.0.10.in-addr.arpa
ipToPtr: 10.0.0.8 => 8.0.0.10.in-addr.arpa

========================================================
````

nmap 10.188.7.141-252: pour scanner une ranger d'Ip

`````bash
──(root㉿kali)-[~/nmap/zenmap]
└─# nmap 10.188.7.141-252
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 04:47 EDT
ipToPtr: 10.188.7.141 => 141.7.188.10.in-addr.arpa
ipToPtr: 10.188.7.142 => 142.7.188.10.in-addr.arpa
ipToPtr: 10.188.7.143 => 143.7.188.10.in-addr.arpa
ipToPtr: 10.188.7.144 => 144.7.188.10.in-addr.arpa
ipToPtr: 10.188.7.145 => 145.7.188.10.in-addr.arpa
ipToPtr: 10.188.7.146 => 146.7.188.10.in-addr.arpa
ipToPtr: 10.188.7.147 => 147.7.188.10.in-addr.arpa

===========================================
````

Pour scanner un fichier contenant une list d'ip

````bash
┌──(root㉿kali)-[~/nmap/zenmap]
└─# touch ip.txt 

┌──(root㉿kali)-[~/nmap/zenmap]
└─# cat ip.txt     
192.168.56.1
45.33.32.156
192.168.47.1
192.168.134.1
10.0.2.6

──(root㉿kali)-[~/nmap/zenmap]
└─# nmap -iL ip.txt      
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 04:52 EDT
ipToPtr: 192.168.56.1 => 1.56.168.192.in-addr.arpa
ipToPtr: 45.33.32.156 => 156.32.33.45.in-addr.arpa
ipToPtr: 192.168.47.1 => 1.47.168.192.in-addr.arpa
ipToPtr: 192.168.134.1 => 1.134.168.192.in-addr.arpa
ipToPtr: 10.0.2.6 => 6.2.0.10.in-addr.arpa
Nmap scan report for 192.168.56.1
Host is up (0.0021s latency).
Not shown: 994 filtered tcp ports (no-response)
PORT     STATE SERVICE
80/tcp   open  http
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
2103/tcp open  zephyr-clt
2107/tcp open  msmq-mgmt
6881/tcp open  bittorrent-tracker

Nmap scan report for scanme.nmap.org (45.33.32.156)
Host is up (0.00048s latency).
Not shown: 987 filtered tcp ports (no-response)
PORT      STATE  SERVICE
1/tcp     closed tcpmux
1174/tcp  closed fnet-remote-ui
1972/tcp  closed intersys-cache
2046/tcp  closed sdfunc
2967/tcp  closed symantec-av
3995/tcp  closed iss-mgmt-ssl
5061/tcp  closed sip-tls
5822/tcp  closed unknown
7000/tcp  closed afs3-fileserver
10215/tcp closed unknown
15660/tcp closed bex-xr
16012/tcp closed unknown
27355/tcp closed unknown

Nmap scan report for 192.168.47.1
Host is up (0.00064s latency).
All 1000 scanned ports on 192.168.47.1 are in ignored states.
Not shown: 1000 filtered tcp ports (no-response)

Nmap scan report for 192.168.134.1
Host is up (0.00055s latency).
Not shown: 999 filtered tcp ports (no-response)
PORT   STATE SERVICE
53/tcp open  domain
=======================================================
````

Pour exclure une address Ip

````bash
──(root㉿kali)-[~/nmap/zenmap]
└─# nmap 10.0.2.6 --exclude 10.188.7.141 
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 04:57 EDT
ipToPtr: 10.0.2.6 => 6.2.0.10.in-addr.arpa
Nmap scan report for 10.0.2.6
Host is up (0.0022s latency).
All 1000 scanned ports on 10.0.2.6 are in ignored states.
Not shown: 1000 filtered tcp ports (no-response)
MAC Address: 08:00:27:67:BA:E7 (PCS Systemtechnik/Oracle VirtualBox virtual NIC)

Nmap done: 1 IP address (1 host up) scanned in 22.15 seconds

==========================================================
````

Pour exclure une IP dans un ensemble ip

````bash

┌──(root㉿kali)-[~/nmap/zenmap]
└─# nmap -F 10.0.2.6/8 --excludefile ip.txt
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 05:00 EDT
ipToPtr: 10.0.0.0 => 0.0.0.10.in-addr.arpa
ipToPtr: 10.0.0.1 => 1.0.0.10.in-addr.arpa
ipToPtr: 10.0.0.2 => 2.0.0.10.in-addr.arpa
ipToPtr: 10.0.0.3 => 3.0.0.10.in-addr.arpa
ipToPtr: 10.0.0.4 => 4.0.0.10.in-addr.arpa
ipToPtr: 10.0.0.5 => 5.0.0.10.in-addr.arpa

=========================================
````

pour scanner une interface dans un réseau:

````bash
┌──(root㉿kali)-[~]
└─# nmap -e lo 10.0.2.15   
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 05:08 EDT
ipToPtr: 10.0.2.15 => 15.2.0.10.in-addr.arpa
ipToPtr: 10.0.2.15 => 15.2.0.10.in-addr.arpa
ipToPtr: 10.0.2.15 => 15.2.0.10.in-addr.arpa
ipToPtr: 10.0.2.15 => 15.2.0.10.in-addr.arpa
Nmap scan report for 10.0.2.15
Host is up.
All 1000 scanned ports on 10.0.2.15 are in ignored states.
Not shown: 1000 filtered tcp ports (no-response)

Nmap done: 1 IP address (1 host up) scanned in 214.49 seconds
=========================================
````

Pour scanner un ip6:

````bash
──(root㉿kali)-[~/nmap/zenmap]
└─# nmap -6 fe80::a00:27ff:fefe:dda8       
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 05:09 EDT
Nmap scan report for fe80::a00:27ff:fefe:dda8
Host is up (0.000043s latency).
All 1000 scanned ports on fe80::a00:27ff:fefe:dda8 are in ignored states.
Not shown: 1000 closed tcp ports (reset)

Nmap done: 1 IP address (1 host up) scanned in 0.66 seconds
============================================
````

Pour selectionner des ip aléatoirement:

````bash
┌──(root㉿kali)-[~/nmap/zenmap]
└─# nmap -iR 3                      
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 05:11 EDT
ipToPtr: 153.23.143.108 => 108.143.23.153.in-addr.arpa
ipToPtr: 51.194.77.196 => 196.77.194.51.in-addr.arpa
ipToPtr: 47.218.97.171 => 171.97.218.47.in-addr.arpa
Nmap scan report for 153.23.143.108
Host is up (0.00041s latency).
All 1000 scanned ports on 153.23.143.108 are in ignored states.
Not shown: 1000 filtered tcp ports (no-response)

Nmap scan report for 33C24Dc4.skybroadband.com (51.194.77.196)
Host is up (0.00055s latency).
All 1000 scanned ports on 33C24Dc4.skybroadband.com (51.194.77.196) are in ignored states.
Not shown: 1000 filtered tcp ports (no-response)

Nmap scan report for 47.218.97.171
Host is up (0.00048s latency).
All 1000 scanned ports on 47.218.97.171 are ignored states.
Not shown: 1000 filtered tcp ports (no-response)

Nmap done: 3 IP addresses (3 hosts up) scanned in 9.55 seconds
                                                                
=====================================================================
````

Pour afficher la raison pour laquel les ports sont filtrés, ouvert etc.

````bash
──(root㉿kali)-[~/nmap/zenmap]
└─# nmap --reason 47.218.97.171
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 05:15 EDT
ipToPtr: 47.218.97.171 => 171.97.218.47.in-addr.arpa
Nmap scan report for 47.218.97.171
Host is up, received reset ttl 255 (0.00056s latency).
All 1000 scanned ports on 47.218.97.171 are in ignored states.
Not shown: 1000 filtered tcp ports (no-response)

Nmap done: 1 IP address (1 host up) scanned in 4.77 seconds
=======================================================================
````

Pour afficher uniquement les port ouvert:

````bash
┌──(root㉿kali)-[~/nmap/zenmap]
└─# nmap --open 47.218.97.171
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 05:16 EDT
ipToPtr: 47.218.97.171 => 171.97.218.47.in-addr.arpa
Nmap done: 1 IP address (1 host up) scanned in 5.01 seconds

==================================================================
````

Pour tracket les packets

````bash
┌──(root㉿kali)-[~/nmap/zenmap]
└─# nmap --packet-trace 10.0.2.6
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 05:18 EDT
SENT (0.0387s) ARP who-has 10.0.2.6 tell 10.0.2.15
RCVD (0.0402s) ARP reply 10.0.2.6 is-at 08:00:27:67:BA:E7
NSOCK INFO [0.0940s] nsock_iod_new2(): nsock_iod_new (IOD #1)
NSOCK INFO [0.0940s] nsock_connect_udp(): UDP connection requested to 8.8.8.8:53 (IOD #1) EID 8
NSOCK INFO [0.0940s] nsock_read(): Read request from IOD #1 [8.8.8.8:53] (timeout: -1ms) EID 18
NSOCK INFO [0.0940s] nsock_iod_new2(): nsock_iod_new (IOD #2)
NSOCK INFO [0.0940s] nsock_connect_udp(): UDP connection requested to 1.1.1.1:53 (IOD #2) EID 24
NSOCK INFO [0.0940s] nsock_read(): Read request from IOD #2 [1.1.1.1:53] (timeout: -1ms) EID 34
ipToPtr: 10.0.2.6 => 6.2.0.10.in-addr.arpa

============================================================
````

Pour scanner un port:

````bash
┌──(root㉿kali)-[~/nmap/zenmap]
└─# nmap -F 10.0.2.6                       
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 05:21 EDT
ipToPtr: 10.0.2.6 => 6.2.0.10.in-addr.arpa
Nmap scan report for 10.0.2.6
Host is up (0.0012s latency).
All 100 scanned ports on 10.0.2.6 are in ignored states.
Not shown: 100 filtered tcp ports (no-response)
MAC Address: 08:00:27:67:BA:E7 (PCS Systemtechnik/Oracle VirtualBox virtual NIC)

Nmap done: 1 IP address (1 host up) scanned in 3.72 seconds

===========================================================
````

Pour scanner un port specifique

````bash
┌──(root㉿kali)-[~/nmap/zenmap]
└─# nmap -p 80 192.168.56.1
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 05:24 EDT
ipToPtr: 192.168.56.1 => 1.56.168.192.in-addr.arpa
Nmap scan report for 192.168.56.1
Host is up (0.00035s latency).

PORT   STATE SERVICE
80/tcp open  http

Nmap done: 1 IP address (1 host up) scanned in 0.60 seconds

========================================
````

Pour scanncer des multiples ports

````bash
┌──(root㉿kali)-[~/nmap/zenmap]
└─# nmap -p 80,139,50-1000 192.168.56.1
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 05:25 EDT
WARNING: Duplicate port number(s) specified.  Are you alert enough to be using Nmap?  Have some coffee or Jolt(tm).
ipToPtr: 192.168.56.1 => 1.56.168.192.in-addr.arpa
Nmap scan report for 192.168.56.1
Host is up (0.0024s latency).
Not shown: 947 filtered tcp ports (no-response)
PORT    STATE SERVICE
80/tcp  open  http
135/tcp open  msrpc
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds

Nmap done: 1 IP address (1 host up) scanned in 15.60 seconds

Par type de service : 
┌──(root㉿kali)-[~/nmap/zenmap]
└─# nmap -p msrpc,http,netbios-ssn 192.168.56.1

┌──(root㉿kali)-[~/nmap/zenmap]
└─# nmap -p msrpc,http,netbios-ssn 192.168.56.1
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 05:27 EDT
ipToPtr: 192.168.56.1 => 1.56.168.192.in-addr.arpa
Nmap scan report for 192.168.56.1
Host is up (0.00050s latency).

PORT     STATE    SERVICE
80/tcp   open     http
135/tcp  open     msrpc
139/tcp  open     netbios-ssn
8008/tcp filtered http
=========================================================
````

Pour scanner le port TPC et UPD:

````bash
┌──(root㉿kali)-[~]
└─# nmap -sU -sT -p U:53, T:25 192.168.56.1
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 05:32 EDT
WARNING: a TCP scan type was requested, but no tcp ports were specified.  Skipping this scan type.
Failed to resolve "T:25".
ipToPtr: 192.168.56.1 => 1.56.168.192.in-addr.arpa
Nmap scan report for 192.168.56.1
Host is up (0.00050s latency).

PORT   STATE         SERVICE
53/udp open|filtered domain

Nmap done: 1 IP address (1 host up) scanned in 1.01 seconds
===========================================
````

Pour spécifier la plage des ports à scanner:

````bash
┌──(root㉿kali)-[~]
└─# nmap -r 192.168.56.1                   
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 05:36 EDT
ipToPtr: 192.168.56.1 => 1.56.168.192.in-addr.arpa
Nmap scan report for 192.168.56.1
Host is up (0.00099s latency).
Not shown: 935 filtered tcp ports (no-response), 57 closed tcp ports (reset)
PORT     STATE SERVICE
80/tcp   open  http
135/tcp  open  msrpc
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
902/tcp  open  iss-realsecure
1801/tcp open  msmq
2179/tcp open  vmrdp
8443/tcp open  https-alt

Nmap done: 1 IP address (1 host up) scanned in 20.39 seconds

===================================
````

Pour scanner une plage de ports aléatoires sur une IP spécifié:

````bash
┌──(root㉿kali)-[~]
└─# nmap -v -r 192.168.56.1
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 05:41 EDT
Initiating Ping Scan at 05:41
Scanning 192.168.56.1 [4 ports]
Completed Ping Scan at 05:41, 0.01s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 05:41
ipToPtr: 192.168.56.1 => 1.56.168.192.in-addr.arpa
Completed Parallel DNS resolution of 1 host. at 05:41, 0.50s elapsed
Initiating SYN Stealth Scan at 05:41
Scanning 192.168.56.1 [1000 ports]
Discovered open port 80/tcp on 192.168.56.1
Discovered open port 135/tcp on 192.168.56.1
Discovered open port 139/tcp on 192.168.56.1
Discovered open port 445/tcp on 192.168.56.1
Completed SYN Stealth Scan at 05:41, 7.46s elapsed (1000 total ports)
Nmap scan report for 192.168.56.1
Host is up (0.0014s latency).
Not shown: 996 filtered tcp ports (no-response)
PORT    STATE SERVICE
80/tcp  open  http
135/tcp open  msrpc
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds

Read data files from: /usr/local/bin/../share/nmap
Nmap done: 1 IP address (1 host up) scanned in 8.04 seconds
           Raw packets sent: 2004 (88.152KB) | Rcvd: 278 (11.132KB)
=================================================================
````






