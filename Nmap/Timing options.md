![Nmap](https://miro.medium.com/v2/resize:fit:720/format:webp/1*taPS7rj99lVcJTwf_gYHKQ.jpeg)
## Timing Templates (-T):
### 1. Description:

- Sets the timing template for the scan. The higher the number, the faster and more aggressive the scan.

````bash
┌──(root㉿kali)-[~]
└─# nmap -T5 192.168.56.1            
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 07:38 EDT
ipToPtr: 192.168.56.1 => 1.56.168.192.in-addr.arpa
Nmap scan report for 192.168.56.1
Host is up (0.0015s latency).
Not shown: 993 filtered tcp ports (no-response)
PORT     STATE SERVICE
80/tcp   open  http
135/tcp  open  msrpc
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
912/tcp  open  apex-mesh
2107/tcp open  msmq-mgmt
8443/tcp open  https-alt

Nmap done: 1 IP address (1 host up) scanned in 5.25 seconds
````


## Minimum & Maximum Number of Parallel Operations:
### 1. Description:

- Specifies the minimum or maximum number of parallel operations to be performed during the scan.

````bash
┌──(root㉿kali)-[~]
└─# nmap --min-parallelism 100 192.168.56.1
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 07:42 EDT
ipToPtr: 192.168.56.1 => 1.56.168.192.in-addr.arpa
Nmap scan report for 192.168.56.1
Host is up (0.0013s latency).
Not shown: 995 filtered tcp ports (no-response)
PORT     STATE SERVICE
80/tcp   open  http
135/tcp  open  msrpc
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
2105/tcp open  eklogin

Nmap done: 1 IP address (1 host up) scanned in 3.77 seconds

----

──(root㉿kali)-[~]
└─# nmap --max-parallelism 100 192.168.56.1
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 07:44 EDT
ipToPtr: 192.168.56.1 => 1.56.168.192.in-addr.arpa
Nmap scan report for 192.168.56.1
Host is up (0.0011s latency).
Not shown: 995 filtered tcp ports (no-response)
PORT     STATE SERVICE
80/tcp   open  http
135/tcp  open  msrpc
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
8443/tcp open  https-alt

Nmap done: 1 IP address (1 host up) scanned in 5.01 seconds
````

## Minimum & Maximum Host Group Size:
### 1. Description:

- Controls the size of host groups for more efficient scanning.

````bash
┌──(root㉿kali)-[~]
└─# nmap --max-hostgroup 10 192.168.56.1
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 07:47 EDT
ipToPtr: 192.168.56.1 => 1.56.168.192.in-addr.arpa
Nmap scan report for 192.168.56.1
Host is up (0.0014s latency).
Not shown: 994 filtered tcp ports (no-response)
PORT     STATE SERVICE
80/tcp   open  http
135/tcp  open  msrpc
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
912/tcp  open  apex-mesh
2179/tcp open  vmrdp

Nmap done: 1 IP address (1 host up) scanned in 11.95 seconds
-----------
┌──(root㉿kali)-[~]
└─# nmap --min-hostgroup 20 192.168.56.1
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 07:49 EDT
ipToPtr: 192.168.56.1 => 1.56.168.192.in-addr.arpa
Nmap scan report for 192.168.56.1
Host is up (0.00053s latency).
Not shown: 996 filtered tcp ports (no-response)
PORT    STATE SERVICE
80/tcp  open  http
135/tcp open  msrpc
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds

Nmap done: 1 IP address (1 host up) scanned in 5.44 seconds
````

## Initial RTT Timeout:
### 1. Description:

- Sets the initial round-trip time (RTT) timeout for the scan.

````bash
┌──(root㉿kali)-[~]
└─# nmap --max-rtt-timeout 1000ms 10.0.2.6              
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 07:50 EDT
ipToPtr: 10.0.2.6 => 6.2.0.10.in-addr.arpa
Nmap scan report for 10.0.2.6
Host is up (0.0014s latency).
All 1000 scanned ports on 10.0.2.6 are in ignored states.
Not shown: 1000 filtered tcp ports (no-response)
MAC Address: 08:00:27:67:BA:E7 (PCS Systemtechnik/Oracle VirtualBox virtual NIC)

Nmap done: 1 IP address (1 host up) scanned in 22.07 seconds

-------------

┌──(root㉿kali)-[~]
└─# nmap --initial-rtt-timeout 1000ms 10.0.2.6
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 07:51 EDT
ipToPtr: 10.0.2.6 => 6.2.0.10.in-addr.arpa
Nmap scan report for 10.0.2.6
Host is up (0.00077s latency).
All 1000 scanned ports on 10.0.2.6 are in ignored states.
Not shown: 1000 filtered tcp ports (no-response)
MAC Address: 08:00:27:67:BA:E7 (PCS Systemtechnik/Oracle VirtualBox virtual NIC)

Nmap done: 1 IP address (1 host up) scanned in 22.09 seconds
````


## Maximum Retries:
### 1. Description: Specifies the maximum number of retries Nmap will attempt before considering a port closed or filtered.

````bash
──(root㉿kali)-[~]
└─# nmap --max-retries 5  10.0.2.6
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 07:56 EDT
ipToPtr: 10.0.2.6 => 6.2.0.10.in-addr.arpa
Nmap scan report for 10.0.2.6
Host is up (0.00091s latency).
All 1000 scanned ports on 10.0.2.6 are in ignored states.
Not shown: 1000 filtered tcp ports (no-response)
MAC Address: 08:00:27:67:BA:E7 (PCS Systemtechnik/Oracle VirtualBox virtual NIC)

Nmap done: 1 IP address (1 host up) scanned in 22.09 seconds
````

## Set Packet TTL:
### 1. Description:

- Sets the time-to-live (TTL) value for packets sent during the scan.

````bash
┌──(root㉿kali)-[~]
└─# nmap --ttl 5s  10.0.2.6
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 07:59 EDT
ipToPtr: 10.0.2.6 => 6.2.0.10.in-addr.arpa
Nmap scan report for 10.0.2.6
Host is up (0.00069s latency).
All 1000 scanned ports on 10.0.2.6 are in ignored states.
Not shown: 1000 filtered tcp ports (no-response)
MAC Address: 08:00:27:67:BA:E7 (PCS Systemtechnik/Oracle VirtualBox virtual NIC)

Nmap done: 1 IP address (1 host up) scanned in 22.03 seconds
````


## Host Timeout:
### 1. Description: 

- Specifies the maximum time Nmap will wait for a response from a host before considering it timed out.

````bash
┌──(root㉿kali)-[~]
└─# nmap --host-timeout 1s  10.0.2.6
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 08:01 EDT
ipToPtr: 10.0.2.6 => 6.2.0.10.in-addr.arpa
Nmap scan report for 10.0.2.6
Host is up (0.00088s latency).
Skipping host 10.0.2.6 due to host timeout
Nmap done: 1 IP address (1 host up) scanned in 1.70 seconds
                                                                          
┌──(root㉿kali)-[~]
└─# nmap --host-timeout 1m  10.0.2.6
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 08:01 EDT
ipToPtr: 10.0.2.6 => 6.2.0.10.in-addr.arpa
Nmap scan report for 10.0.2.6
Host is up (0.00069s latency).
All 1000 scanned ports on 10.0.2.6 are in ignored states.
Not shown: 1000 filtered tcp ports (no-response)
MAC Address: 08:00:27:67:BA:E7 (PCS Systemtechnik/Oracle VirtualBox virtual NIC)

Nmap done: 1 IP address (1 host up) scanned in 21.76 seconds
````


## Minimum and Maximum Scan Delay:
### 1. Description:

- Controls the delay between sending packets during the scan.


````bash

┌──(root㉿kali)-[~]
└─# nmap --scan-delay  10ms 10.0.2.6
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 08:04 EDT
Stats: 0:00:00 elapsed; 0 hosts completed (0 up), 1 undergoing ARP Ping Scan
ARP Ping Scan Timing: About 0.00% done
ipToPtr: 10.0.2.6 => 6.2.0.10.in-addr.arpa
Nmap scan report for 10.0.2.6
Host is up (0.00054s latency).
All 1000 scanned ports on 10.0.2.6 are in ignored states.
Not shown: 1000 filtered tcp ports (no-response)
MAC Address: 08:00:27:67:BA:E7 (PCS Systemtechnik/Oracle VirtualBox virtual NIC)

Nmap done: 1 IP address (1 host up) scanned in 22.67 seconds

---------------
┌──(root㉿kali)-[~]
└─# nmap --max-scan-delay  10ms 10.0.2.6
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 08:06 EDT
ipToPtr: 10.0.2.6 => 6.2.0.10.in-addr.arpa
Nmap scan report for 10.0.2.6
Host is up (0.0011s latency).
All 1000 scanned ports on 10.0.2.6 are in ignored states.
Not shown: 1000 filtered tcp ports (no-response)
MAC Address: 08:00:27:67:BA:E7 (PCS Systemtechnik/Oracle VirtualBox virtual NIC)

Nmap done: 1 IP address (1 host up) scanned in 22.10 seconds
````

## Minimum and Maximum Packet Rate:
### 1. Description:

- Sets the minimum and maximum packet rate for the scan.

````bash
┌──(root㉿kali)-[~]
└─# nmap --min-rate 50 10.0.2.6
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 08:07 EDT
ipToPtr: 10.0.2.6 => 6.2.0.10.in-addr.arpa
Nmap scan report for 10.0.2.6
Host is up (0.00100s latency).
All 1000 scanned ports on 10.0.2.6 are in ignored states.
Not shown: 1000 filtered tcp ports (no-response)
MAC Address: 08:00:27:67:BA:E7 (PCS Systemtechnik/Oracle VirtualBox virtual NIC)

Nmap done: 1 IP address (1 host up) scanned in 20.86 seconds
````


## Defeat Reset Rate Limiting:
### 1. Description: Attempts to defeat reset rate limiting by sending probe packets at a slower rate.

````bash
┌──(root㉿kali)-[~]
└─# nmap -defeat-rst-ratelimit 10.0.2.6 
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 08:10 EDT
ipToPtr: 10.0.2.6 => 6.2.0.10.in-addr.arpa
Nmap scan report for 10.0.2.6
Host is up (0.0012s latency).
All 1000 scanned ports on 10.0.2.6 are in ignored states.
Not shown: 1000 filtered tcp ports (no-response)
MAC Address: 08:00:27:67:BA:E7 (PCS Systemtechnik/Oracle VirtualBox virtual NIC)

Nmap done: 1 IP address (1 host up) scanned in 21.83 seconds
```


 


