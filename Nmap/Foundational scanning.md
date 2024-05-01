![Nmap](https://miro.medium.com/v2/resize:fit:720/format:webp/1*M0jQ_MfkUkHB309bj24OzA.jpeg)
## No Ping Scan:
### 1. Description: 

- This command instructs Nmap not to perform host discovery and to scan the specified IP address even if it appears to be unresponsive to ping.

````bash
┌──(root㉿kali)-[~]
└─# nmap -PN 192.168.56.1 
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 05:50 EDT
ipToPtr: 192.168.56.1 => 1.56.168.192.in-addr.arpa
Nmap scan report for 192.168.56.1
Host is up (0.0013s latency).
Not shown: 992 filtered tcp ports (no-response)
PORT     STATE SERVICE
80/tcp   open  http
135/tcp  open  msrpc
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
902/tcp  open  iss-realsecure
1801/tcp open  msmq
2107/tcp open  msmq-mgmt
2179/tcp open  vmrdp

Nmap done: 1 IP address (1 host up) scanned in 13.41 seconds
````


## Ping Only Scan:
### 1. Description: 

- This command performs a scan by sending only ping probes to the specified IP address to determine if the host is up.

````bash
┌──(root㉿kali)-[~]
└─# nmap -sP 192.168.56.1
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 05:52 EDT
ipToPtr: 192.168.56.1 => 1.56.168.192.in-addr.arpa
Nmap scan report for 192.168.56.1
Host is up (0.0015s latency).
Nmap done: 1 IP address (1 host up) scanned in 0.54 seconds
````

## TCP SYN Ping:
### 1. Description: 

- This command specifies Nmap to conduct a SYN scan with an initial packet.

````bash
┌──(root㉿kali)-[~]
└─# nmap -PS 192.168.56.1  
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 05:55 EDT
ipToPtr: 192.168.56.1 => 1.56.168.192.in-addr.arpa
Nmap scan report for 192.168.56.1
Host is up (0.0014s latency).
Not shown: 991 filtered tcp ports (no-response)
PORT     STATE SERVICE
80/tcp   open  http
135/tcp  open  msrpc
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
912/tcp  open  apex-mesh
1801/tcp open  msmq
2103/tcp open  zephyr-clt
2105/tcp open  eklogin
2179/tcp open  vmrdp

Nmap done: 1 IP address (1 host up) scanned in 29.60 seconds
````

## TCP SYN Ping:
### Description:

- This command specifies Nmap to conduct a SYN scan with an initial packet.

````bash
┌──(root㉿kali)-[~]
└─# nmap -PA 192.168.56.1
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 05:59 EDT
ipToPtr: 192.168.56.1 => 1.56.168.192.in-addr.arpa
Nmap scan report for 192.168.56.1
Host is up (0.00098s latency).
Not shown: 995 filtered tcp ports (no-response)
PORT     STATE SERVICE
80/tcp   open  http
135/tcp  open  msrpc
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
6881/tcp open  bittorrent-tracker

Nmap done: 1 IP address (1 host up) scanned in 5.47 seconds

------------

┌──(root㉿kali)-[~]
└─# nmap -PA 443 192.168.56.1
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 06:01 EDT
ipToPtr: 192.168.56.1 => 1.56.168.192.in-addr.arpa
Nmap scan report for 192.168.56.1
Host is up (0.00085s latency).
Not shown: 995 filtered tcp ports (no-response)
PORT     STATE SERVICE
80/tcp   open  http
135/tcp  open  msrpc
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
2103/tcp open  zephyr-clt

Nmap done: 2 IP addresses (1 host up) scanned in 18.27 seconds
````

## UDP Ping:
### 1. Description:

- This command sends UDP packets to the specified IP address to determine if the host is up.

````bash
┌──(root㉿kali)-[~]
└─# nmap -PU 192.168.56.1 
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 06:03 EDT
Note: Host seems down. If it is really up, but blocking our ping probes, try -Pn
Nmap done: 1 IP address (0 hosts up) scanned in 15.23 seconds

┌──(root㉿kali)-[~]
└─# nmap -PU 80 192.168.56.1
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 06:04 EDT
Nmap done: 2 IP addresses (0 hosts up) scanned in 15.14 seconds
````

## SCTP INIT Ping:
### 1. Description: This command sends SCTP INIT packets to the specified IP address to determine if the host is up.

````bash

──(root㉿kali)-[~]
└─# nmap -PY 80 10.0.2.2    
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 06:08 EDT
ipToPtr: 10.0.2.2 => 2.2.0.10.in-addr.arpa
Nmap scan report for 10.0.2.2
Host is up (0.00096s latency).
Not shown: 994 filtered tcp ports (no-response)
PORT     STATE SERVICE
80/tcp   open  http
135/tcp  open  msrpc
445/tcp  open  microsoft-ds
902/tcp  open  iss-realsecure
2105/tcp open  eklogin
8443/tcp open  https-alt
MAC Address: 52:54:00:12:35:00 (QEMU virtual NIC)

Nmap done: 2 IP addresses (1 host up) scanned in 30.08 seconds
````

## ICMP Echo Ping:
### 1. Description:

- This command sends ICMP echo requests (ping) to the specified IP address to determine if the host is up.

````bash
┌──(root㉿kali)-[~]
└─# nmap -PE 10.0.2.2 
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 06:10 EDT
ipToPtr: 10.0.2.2 => 2.2.0.10.in-addr.arpa
Nmap scan report for 10.0.2.2
Host is up (0.0011s latency).
Not shown: 993 filtered tcp ports (no-response)
PORT     STATE SERVICE
80/tcp   open  http
135/tcp  open  msrpc
445/tcp  open  microsoft-ds
902/tcp  open  iss-realsecure
912/tcp  open  apex-mesh
1123/tcp open  murray
2179/tcp open  vmrdp
MAC Address: 52:54:00:12:35:00 (QEMU virtual NIC)

Nmap done: 1 IP address (1 host up) scanned in 6.38 seconds
````

## ICMP Timestamp Ping:
### 1. Description:

- This command sends ICMP timestamp requests to the specified IP address to determine if the host is up.

````bash
┌──(root㉿kali)-[~/nmap/zenmap]
└─# nmap -PO 10.0.2.15
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 06:25 EDT
ipToPtr: 10.0.2.15 => 15.2.0.10.in-addr.arpa
Nmap scan report for 10.0.2.15
Host is up (0.0000010s latency).
All 1000 scanned ports on 10.0.2.15 are in ignored states.
Not shown: 1000 closed tcp ports (reset)

Nmap done: 1 IP address (1 host up) scanned in 0.59 seconds

````
##  Address Mask Ping:
### 1. Description:

- This command sends ICMP address mask requests to the specified IP address to determine if the host is up.

````bash
──(root㉿kali)-[~/nmap/zenmap]
└─# nmap -PM 10.0.2.2
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 06:14 EDT
ipToPtr: 10.0.2.2 => 2.2.0.10.in-addr.arpa
Nmap scan report for 10.0.2.2
Host is up (0.0012s latency).
Not shown: 993 filtered tcp ports (no-response)
PORT     STATE SERVICE
80/tcp   open  http
135/tcp  open  msrpc
445/tcp  open  microsoft-ds
902/tcp  open  iss-realsecure
2103/tcp open  zephyr-clt
2105/tcp open  eklogin
8099/tcp open  unknown
MAC Address: 52:54:00:12:35:00 (QEMU virtual NIC)

Nmap done: 1 IP address (1 host up) scanned in 14.24 seconds
````

## IP Protocol Ping:
### 1. Description:

- This command sends IP protocol packets to the specified IP address to determine if the host is up.

````bash
┌──(root㉿kali)-[~]
└─# nmap -PP 10.0.2.6
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 06:25 EDT
ipToPtr: 10.0.2.6 => 6.2.0.10.in-addr.arpa
Nmap scan report for 10.0.2.6
Host is up (0.00057s latency).
All 1000 scanned ports on 10.0.2.6 are in ignored states.
Not shown: 1000 filtered tcp ports (no-response)
MAC Address: 08:00:27:67:BA:E7 (PCS Systemtechnik/Oracle VirtualBox virtual NIC)

Nmap done: 1 IP address (1 host up) scanned in 21.96 seconds
````

## ARP Ping:
### 1. Description: 

- This command sends ARP requests to the specified IP address to determine if the host is up.

````bash
┌──(root㉿kali)-[~]
└─# nmap -PR 10.0.2.2 
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 06:18 EDT
ipToPtr: 10.0.2.2 => 2.2.0.10.in-addr.arpa
Nmap scan report for 10.0.2.2
Host is up (0.00094s latency).
Not shown: 994 filtered tcp ports (no-response)
PORT     STATE SERVICE
80/tcp   open  http
135/tcp  open  msrpc
445/tcp  open  microsoft-ds
1434/tcp open  ms-sql-m
2103/tcp open  zephyr-clt
2107/tcp open  msmq-mgmt
MAC Address: 52:54:00:12:35:00 (QEMU virtual NIC)

Nmap done: 1 IP address (1 host up) scanned in 10.22 seconds
````

## Traceroute:
### 1. Description: This command performs a traceroute to the specified IP address.
````bash
┌──(root㉿kali)-[~]
└─# nmap -traceroute 10.0.2.6
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 06:26 EDT
ipToPtr: 10.0.2.6 => 6.2.0.10.in-addr.arpa
Nmap scan report for 10.0.2.6
Host is up (0.00049s latency).
All 1000 scanned ports on 10.0.2.6 are in ignored states.
Not shown: 1000 filtered tcp ports (no-response)
MAC Address: 08:00:27:67:BA:E7 (PCS Systemtechnik/Oracle VirtualBox virtual NIC)

TRACEROUTE
HOP RTT     ADDRESS
1   0.50 ms 10.0.2.6

Nmap done: 1 IP address (1 host up) scanned in 21.86 seconds
````

## Force Reverse DNS Resolution:
### 1. Description:

- This command forces Nmap to perform reverse DNS resolution for the specified IP address.

`````bash
┌──(root㉿kali)-[~]
└─# nmap -R 10.0.2.2
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 06:28 EDT
ipToPtr: 10.0.2.2 => 2.2.0.10.in-addr.arpa
Nmap scan report for 10.0.2.2
Host is up (0.0012s latency).
Not shown: 994 filtered tcp ports (no-response)
PORT     STATE SERVICE
80/tcp   open  http
135/tcp  open  msrpc
445/tcp  open  microsoft-ds
912/tcp  open  apex-mesh
1123/tcp open  murray
2107/tcp open  msmq-mgmt
MAC Address: 52:54:00:12:35:00 (QEMU virtual NIC)

Nmap done: 1 IP address (1 host up) scanned in 12.49 seconds





┌──(root㉿kali)-[~]
└─# nmap -R 10.0.2.0/24
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 06:31 EDT
ipToPtr: 10.0.2.0 => 0.2.0.10.in-addr.arpa
ipToPtr: 10.0.2.1 => 1.2.0.10.in-addr.arpa
ipToPtr: 10.0.2.2 => 2.2.0.10.in-addr.arpa
ipToPtr: 10.0.2.3 => 3.2.0.10.in-addr.arpa
ipToPtr: 10.0.2.4 => 4.2.0.10.in-addr.arpa
ipToPtr: 10.0.2.5 => 5.2.0.10.in-addr.arpa
ipToPtr: 10.0.2.6 => 6.2.0.10.in-addr.arpa
ipToPtr: 10.0.2.7 => 7.2.0.10.in-addr.arpa
ipToPtr: 10.0.2.8 => 8.2.0.10.in-addr.arpa
ipToPtr: 10.0.2.9 => 9.2.0.10.in-addr.arpa

ipToPtr: 10.0.2.254 => 254.2.0.10.in-addr.arpa
ipToPtr: 10.0.2.255 => 255.2.0.10.in-addr.arpa
ipToPtr: 10.0.2.15 => 15.2.0.10.in-addr.arpa
Nmap scan report for 10.0.2.1
Host is up (0.00042s latency).
Not shown: 999 closed tcp ports (reset)
PORT   STATE SERVICE
53/tcp open  domain
MAC Address: 52:54:00:12:35:00 (QEMU virtual NIC)

Nmap scan report for 10.0.2.2
Host is up (0.0010s latency).
Not shown: 992 filtered tcp ports (no-response)
PORT     STATE SERVICE
80/tcp   open  http
135/tcp  open  msrpc
445/tcp  open  microsoft-ds
902/tcp  open  iss-realsecure
1123/tcp open  murray
1434/tcp open  ms-sql-m
2103/tcp open  zephyr-clt
2105/tcp open  eklogin
MAC Address: 52:54:00:12:35:00 (QEMU virtual NIC)

Nmap scan report for 10.0.2.3
Host is up (0.00043s latency).
All 1000 scanned ports on 10.0.2.3 are in ignored states.
Not shown: 1000 filtered tcp ports (proto-unreach)
MAC Address: 08:00:27:1D:81:28 (PCS Systemtechnik/Oracle VirtualBox virtual NIC)

Nmap scan report for 10.0.2.6
Host is up (0.0011s latency).
All 1000 scanned ports on 10.0.2.6 are in ignored states.
Not shown: 1000 filtered tcp ports (no-response)
MAC Address: 08:00:27:67:BA:E7 (PCS Systemtechnik/Oracle VirtualBox virtual NIC)

Nmap scan report for 10.0.2.15
Host is up (0.0000030s latency).
All 1000 scanned ports on 10.0.2.15 are in ignored states.
Not shown: 1000 closed tcp ports (reset)

Nmap done: 256 IP addresses (5 hosts up) scanned in 10.66 seconds
`````


## Disable Reverse DNS Resolution:
### 1. Description: This command disables reverse DNS resolution for the specified IP address or range.

````bash
┌──(root㉿kali)-[~]
└─# nmap -n 10.0.2.0/24
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 06:34 EDT
Nmap scan report for 10.0.2.1
Host is up (0.00051s latency).
Not shown: 999 closed tcp ports (reset)
PORT   STATE SERVICE
53/tcp open  domain
MAC Address: 52:54:00:12:35:00 (QEMU virtual NIC)

Nmap scan report for 10.0.2.2
Host is up (0.0011s latency).
Not shown: 993 filtered tcp ports (no-response)
PORT     STATE SERVICE
80/tcp   open  http
135/tcp  open  msrpc
445/tcp  open  microsoft-ds
902/tcp  open  iss-realsecure
912/tcp  open  apex-mesh
1123/tcp open  murray
2105/tcp open  eklogin
MAC Address: 52:54:00:12:35:00 (QEMU virtual NIC)

Nmap scan report for 10.0.2.3
Host is up (0.00045s latency).
All 1000 scanned ports on 10.0.2.3 are in ignored states.
Not shown: 1000 filtered tcp ports (proto-unreach)
MAC Address: 08:00:27:1D:81:28 (PCS Systemtechnik/Oracle VirtualBox virtual NIC)

Nmap scan report for 10.0.2.6
Host is up (0.0022s latency).
All 1000 scanned ports on 10.0.2.6 are in ignored states.
Not shown: 1000 filtered tcp ports (no-response)
MAC Address: 08:00:27:67:BA:E7 (PCS Systemtechnik/Oracle VirtualBox virtual NIC)

Nmap scan report for 10.0.2.15
Host is up (0.0000010s latency).
All 1000 scanned ports on 10.0.2.15 are in ignored states.
Not shown: 1000 closed tcp ports (reset)

Nmap done: 256 IP addresses (5 hosts up) scanned in 16.42 seconds
````

## Alternative DNS Lookup Method:
### 1. Description: This command uses an alternative DNS lookup method for the specified IP address.

````bash
┌──(root㉿kali)-[~]
└─# nmap -system-dns 10.0.2.6   
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 06:35 EDT
Nmap scan report for 10.0.2.6
Host is up (0.0030s latency).
All 1000 scanned ports on 10.0.2.6 are in ignored states.
Not shown: 1000 filtered tcp ports (no-response)
MAC Address: 08:00:27:67:BA:E7 (PCS Systemtechnik/Oracle VirtualBox virtual NIC)

Nmap done: 1 IP address (1 host up) scanned in 21.34 seconds

````


## Manually Specify DNS Servers:
### 1. Description:

- This command manually specifies DNS servers for DNS resolution.

````bash
┌──(root㉿kali)-[~]
└─# nmap --dns-servers 8.8.8.8 8.8.8.4, 1.1.1.1 10.0.2.6   
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 06:41 EDT
Failed to resolve "8.8.8.4,".
ipToPtr: 1.1.1.1 => 1.1.1.1.in-addr.arpa
ipToPtr: 10.0.2.6 => 6.2.0.10.in-addr.arpa
Nmap scan report for one.one.one.one (1.1.1.1)
Host is up (0.0026s latency).
Not shown: 996 filtered tcp ports (no-response)
PORT     STATE SERVICE
53/tcp   open  domain
80/tcp   open  http
443/tcp  open  https
8080/tcp open  http-proxy

Nmap scan report for 10.0.2.6
Host is up (0.00082s latency).
All 1000 scanned ports on 10.0.2.6 are in ignored states.
Not shown: 1000 filtered tcp ports (no-response)
MAC Address: 08:00:27:67:BA:E7 (PCS Systemtechnik/Oracle VirtualBox virtual NIC)

Nmap done: 2 IP addresses (2 hosts up) scanned in 26.66 seconds
````







