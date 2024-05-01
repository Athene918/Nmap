![Nmap](https://miro.medium.com/v2/resize:fit:720/format:webp/1*7pgFmLlvzV6p9oFssW8KUQ.jpeg)
## TCP SYN Scan (-sS) :
## 1. Description : 

- Nmap sends a TCP SYN packet to the target port and observes the response to determine if the port is open, closed, or filtered.
````bash

┌──(root㉿kali)-[~]
└─# nmap -sS 192.168.56.1
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 06:47 EDT
ipToPtr: 192.168.56.1 => 1.56.168.192.in-addr.arpa
Nmap scan report for 192.168.56.1
Host is up (0.0014s latency).
Not shown: 995 filtered tcp ports (no-response)
PORT     STATE SERVICE
80/tcp   open  http
135/tcp  open  msrpc
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
2105/tcp open  eklogin

Nmap done: 1 IP address (1 host up) scanned in 4.96 seconds
````

## TCP Connect Scan (-sT) :
### 1. Description : Nmap attempts to connect to each target port using the standard TCP connection function of the operating system.

````bash
┌──(root㉿kali)-[~]
└─# nmap -sT 192.168.56.1
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 06:51 EDT
ipToPtr: 192.168.56.1 => 1.56.168.192.in-addr.arpa
Nmap scan report for 192.168.56.1
Host is up (0.0030s latency).
Not shown: 993 filtered tcp ports (no-response)
PORT     STATE SERVICE
80/tcp   open  http
135/tcp  open  msrpc
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
1801/tcp open  msmq
2103/tcp open  zephyr-clt
8443/tcp open  https-alt

Nmap done: 1 IP address (1 host up) scanned in 17.35 seconds
````

## UDP Scan (-sU) :
### 1. Description :

- Nmap operates by sending a UDP packet to each target port and listening for any responses.

````bash
┌──(root㉿kali)-[~]
└─# nmap -sU 192.168.56.1
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 06:54 EDT
ipToPtr: 192.168.56.1 => 1.56.168.192.in-addr.arpa
Nmap scan report for 192.168.56.1
Host is up (0.00091s latency).
All 1000 scanned ports on 192.168.56.1 are in ignored states.
Not shown: 1000 open|filtered udp ports (no-response)

Nmap done: 1 IP address (1 host up) scanned in 5.16 seconds
````

## TCP NULL Scan (-sN) :
### 1. Description :

- Nmap sends a TCP packet with no flags set (NULL), indicating no control flags are set in the packet.

````bash
┌──(root㉿kali)-[~]
└─# nmap -sN 10.0.2.2
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 06:58 EDT
ipToPtr: 10.0.2.2 => 2.2.0.10.in-addr.arpa
Nmap scan report for 10.0.2.2
Host is up (0.00021s latency).
All 1000 scanned ports on 10.0.2.2 are in ignored states.
Not shown: 1000 open|filtered tcp ports (no-response)
MAC Address: 52:54:00:12:35:00 (QEMU virtual NIC)

Nmap done: 1 IP address (1 host up) scanned in 21.80 seconds
````

## TCP FIN Scan (-sF) :
### 1. Description : Nmap sends a TCP packet with the FIN flag set, indicating a connection closure.

````bash
┌──(root㉿kali)-[~]
└─# nmap -sF 10.0.2.2
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 07:00 EDT
ipToPtr: 10.0.2.2 => 2.2.0.10.in-addr.arpa
Nmap scan report for 10.0.2.2
Host is up (0.00033s latency).
All 1000 scanned ports on 10.0.2.2 are in ignored states.
Not shown: 1000 open|filtered tcp ports (no-response)
MAC Address: 52:54:00:12:35:00 (QEMU virtual NIC)

Nmap done: 1 IP address (1 host up) scanned in 21.82 seconds
````


## Xmas Scan (-sX) :
### 1. Description :

- Nmap sends a TCP packet with the FIN, PSH, and URG flags set, simulating a "Christmas" packet.

````bash

┌──(root㉿kali)-[~]
└─# nmap -sX 192.168.56.1
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 07:05 EDT
ipToPtr: 192.168.56.1 => 1.56.168.192.in-addr.arpa
Nmap scan report for 192.168.56.1
Host is up (0.0012s latency).
All 1000 scanned ports on 192.168.56.1 are in ignored states.
Not shown: 1000 open|filtered tcp ports (no-response)

Nmap done: 1 IP address (1 host up) scanned in 21.88 seconds
````

## TCP ACK Scan (-sA) :
### 1. Description :

- Nmap sends a TCP ACK packet to the target port and observes the response to determine if the port is filtered or not.

````bash
┌──(root㉿kali)-[~]
└─# nmap -sA 192.168.56.1
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 07:08 EDT
ipToPtr: 192.168.56.1 => 1.56.168.192.in-addr.arpa
Nmap scan report for 192.168.56.1
Host is up (0.00031s latency).
All 1000 scanned ports on 192.168.56.1 are in ignored states.
Not shown: 1000 unfiltered tcp ports (reset)

Nmap done: 1 IP address (1 host up) scanned in 0.85 seconds
````


## IP Protocol Scan (-sO) :
### 1. Description :

- Nmap scans for supported IP protocols on the target host.

````bash
┌──(root㉿kali)-[~]
└─# nmap -sO 192.168.56.1
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 07:10 EDT
ipToPtr: 192.168.56.1 => 1.56.168.192.in-addr.arpa
Nmap scan report for 192.168.56.1
Host is up (0.00095s latency).
Not shown: 254 open|filtered n/a protocols (no-response)
PROTOCOL STATE SERVICE
1        open  icmp
6        open  tcp

Nmap done: 1 IP address (1 host up) scanned in 3.24 seconds
````


## Send Raw Ethernet Packets (-send-eth) :
### 1. Description :

- Nmap sends Ethernet frames directly on the network rather than using standard IP sockets.

````bash
┌──(root㉿kali)-[~]
└─# nmap -send-eth 10.0.2.6    
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 07:15 EDT
ipToPtr: 10.0.2.6 => 6.2.0.10.in-addr.arpa
Nmap scan report for 10.0.2.6
Host is up (0.00082s latency).
All 1000 scanned ports on 10.0.2.6 are in ignored states.
Not shown: 1000 filtered tcp ports (no-response)
MAC Address: 08:00:27:67:BA:E7 (PCS Systemtechnik/Oracle VirtualBox virtual NIC)

Nmap done: 1 IP address (1 host up) scanned in 21.97 seconds
┌──(root㉿kali)-[~]
└─# nmap -send-ip 192.168.56.1
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 07:17 EDT
ipToPtr: 192.168.56.1 => 1.56.168.192.in-addr.arpa
Nmap scan report for 192.168.56.1
Host is up (0.0012s latency).
Not shown: 996 filtered tcp ports (no-response)
PORT    STATE SERVICE
80/tcp  open  http
135/tcp open  msrpc
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds

Nmap done: 1 IP address (1 host up) scanned in 5.36 seconds
````

Send IP Packets (-send-ip) :
Description : Nmap sends IP packets directly on the network to scan ports and services.

````bash
nmap -send-ip 192.168.1.100

````






