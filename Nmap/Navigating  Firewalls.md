![Nmap](https://miro.medium.com/v2/resize:fit:720/format:webp/1*ZvZ75mOue5mjcnEqhD8SMg.png)
## Fragmenting Custom MTU for Evasion:
### 1. Description:

- Adjusts the Maximum Transmission Unit (MTU) size to 16 bytes to evade detection.

````bash
┌──(root㉿kali)-[~]
└─# nmap -mtu 16 192.168.56.1
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 08:13 EDT
ipToPtr: 192.168.56.1 => 1.56.168.192.in-addr.arpa
Nmap scan report for 192.168.56.1
Host is up (0.0013s latency).
All 1000 scanned ports on 192.168.56.1 are in ignored states.
Not shown: 1000 filtered tcp ports (no-response)

Nmap done: 1 IP address (1 host up) scanned in 21.96 seconds
````

## Decoy Scanning for Anonymity:
### 1. Description: Scans the target while sending decoy packets from randomized IP addresses to obscure the true source of the scan.

````bash
──(root㉿kali)-[~]
└─# nmap -D RND:5 192.168.56.1
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 08:15 EDT
ipToPtr: 192.168.56.1 => 1.56.168.192.in-addr.arpa
Nmap scan report for 192.168.56.1
Host is up (0.0013s latency).
Not shown: 997 filtered tcp ports (no-response)
PORT    STATE SERVICE
80/tcp  open  http
135/tcp open  msrpc
445/tcp open  microsoft-ds

Nmap done: 1 IP address (1 host up) scanned in 5.70 seconds
````


## Idle Zombie Scan:
### 1. Description:

- Performs an idle scan using a zombie host (192.168.56.1) to avoid detection by leveraging the idle state of the zombie host.

````bash
┌──(root㉿kali)-[~]
└─# nmap -sI 192.168.56.1 10.0.2.2
WARNING: Many people use -Pn w/Idlescan to prevent pings from their true IP.  On the other hand, timing info Nmap gains from pings can allow for faster, more reliable scans.
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 08:17 EDT
ipToPtr: 10.0.2.2 => 2.2.0.10.in-addr.arpa
Idle scan using zombie 192.168.56.1 (192.168.56.1:443); Class: Incremental
Nmap scan report for 10.0.2.2
Host is up (0.0082s latency).
All 1000 scanned ports on 10.0.2.2 are in ignored states.
Not shown: 1000 closed|filtered tcp ports (no-ipid-change)
MAC Address: 52:54:00:12:35:00 (QEMU virtual NIC)

Nmap done: 1 IP address (1 host up) scanned in 8.74 seconds
````


## Manually Specify a Source Port Number:
### 1. Description:

- Sets the source port number to 53 (DNS) for the scan.

````bash
┌──(root㉿kali)-[~]
└─# nmap -source-port 53 192.168.56.1
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 08:21 EDT
ipToPtr: 192.168.56.1 => 1.56.168.192.in-addr.arpa
Nmap scan report for 192.168.56.1
Host is up (0.00089s latency).
Not shown: 990 filtered tcp ports (no-response)
PORT     STATE SERVICE
80/tcp   open  http
135/tcp  open  msrpc
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
902/tcp  open  iss-realsecure
1801/tcp open  msmq
2103/tcp open  zephyr-clt
2105/tcp open  eklogin
2179/tcp open  vmrdp
8443/tcp open  https-alt

Nmap done: 1 IP address (1 host up) scanned in 14.26 seconds
````


## Append Random Data:
### 1. Description:

- Appends random data to each packet sent during the scan to obfuscate the scan's purpose.

````bash
┌──(root㉿kali)-[~]
└─# nmap -data-length 25 192.168.56.1
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 08:23 EDT
ipToPtr: 192.168.56.1 => 1.56.168.192.in-addr.arpa
Nmap scan report for 192.168.56.1
Host is up (0.0012s latency).
Not shown: 991 filtered tcp ports (no-response)
PORT     STATE SERVICE
80/tcp   open  http
135/tcp  open  msrpc
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
902/tcp  open  iss-realsecure
912/tcp  open  apex-mesh
1801/tcp open  msmq
2107/tcp open  msmq-mgmt
8443/tcp open  https-alt

Nmap done: 1 IP address (1 host up) scanned in 20.02 seconds
````

## Randomize Target Scan Order:
### 1. Description:

- Randomizes the order in which targets are scanned to make the scan less predictable and harder to defend against.

````bash
──(root㉿kali)-[~]
└─# nmap -randomize-hosts 25 192.168.56.1-100
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 08:25 EDT
ipToPtr: 192.168.56.53 => 53.56.168.192.in-addr.arpa
ipToPtr: 192.168.56.34 => 34.56.168.192.in-addr.arpa
ipToPtr: 192.168.56.2 => 2.56.168.192.in-addr.arpa
ipToPtr: 192.168.56.83 => 83.56.168.192.in-addr.arpa
ipToPtr: 192.168.56.6 => 6.56.168.192.in-addr.arpa
ipToPtr: 192.168.56.86 => 86.56.168.192.in-addr.arpa
ipToPtr: 192.168.56.57 => 57.56.168.192.in-addr.arpa
ipToPtr: 192.168.56.50 => 50.56.168.192.in-addr.arpa
ipToPtr: 192.168.56.78 => 78.56.168.192.in-addr.arpa
ipToPtr: 192.168.56.55 => 55.56.168.192.in-addr.arpa
ipToPtr: 192.168.56.8 => 8.56.168.192.in-addr.arpa
ipToPtr: 192.168.56.33 => 33.56.168.192.in-addr.arpa
ipToPtr: 192.168.56.60 => 60.56.168.192.in-addr.arpa
````


## Spoof MAC Address:
### 1. Description: Spoofs the MAC address of the scanning device to appear as a different device on the network.

````bash
┌──(root㉿kali)-[~]
└─# nmap -spoof-mac 0 192.168.56      
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 08:27 EDT
Spoofing MAC address 8F:44:6C:F9:52:BD (No registered vendor)
ipToPtr: 192.168.0.56 => 56.0.168.192.in-addr.arpa
Nmap scan report for 192.168.56 (192.168.0.56)
Host is up (0.00072s latency).
Not shown: 999 filtered tcp ports (no-response)
PORT   STATE SERVICE
53/tcp open  domain

Nmap done: 1 IP address (1 host up) scanned in 4.70 seconds
````


## Send Bad Checksums:
### 1. Description:

- Generates packets with intentionally incorrect checksums to potentially bypass certain types of packet filtering.

````bash
┌──(root㉿kali)-[~]
└─# nmap -badsum 0 192.168.56.1
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 08:29 EDT
ipToPtr: 0.0.0.0 => 0.0.0.0.in-addr.arpa
Nmap scan report for 0 (0.0.0.0)
Host is up.
All 1000 scanned ports on 0 (0.0.0.0) are in ignored states.
Not shown: 1000 filtered tcp ports (no-response)

Nmap done: 2 IP addresses (1 host up) scanned in 217.98 seconds
````



