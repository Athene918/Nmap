![Nmap](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*ZdtgJhMMZWMB0BeSIKbvAQ.jpeg)
## Operating System Detection:
### 1. Description:

- Attempts to determine the operating system of the target host based on various characteristics such as open ports and responses to specific probes.

````bash
┌──(root㉿kali)-[~]
└─# nmap -O 192.168.56.1
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 07:23 EDT
ipToPtr: 192.168.56.1 => 1.56.168.192.in-addr.arpa
Nmap scan report for 192.168.56.1
Host is up (0.0011s latency).
Not shown: 995 filtered tcp ports (no-response)
PORT    STATE SERVICE
80/tcp  open  http
135/tcp open  msrpc
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds
902/tcp open  iss-realsecure
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
Device type: bridge|specialized|VoIP phone|webcam|firewall
Running (JUST GUESSING): Oracle Virtualbox (94%), lwIP (94%), 2N embedded (93%), Grandstream embedded (93%), Garmin embedded (89%), Cisco ASA 9.X (87%), Intelbras embedded (87%), FireBrick embedded (85%)
OS CPE: cpe:/a:oracle:vm_virtualbox cpe:/a:lwip_project:lwip cpe:/h:2n:helios cpe:/h:grandstream:gxp1105 cpe:/h:garmin:virb_elite cpe:/o:cisco:asa:9.2 cpe:/h:firebrick:fb2700
Aggressive OS guesses: Oracle Virtualbox lwIP NAT bridge (94%), 2N Helios IP VoIP doorbell (93%), Grandstream GXP1105 VoIP phone (93%), Garmin Virb Elite action camera (89%), Cisco Adaptive Security Appliance (ASA 9.2) (87%), Intelbras VIP 3220 camera (87%), FireBrick FB2700 firewall (85%)
No exact OS matches for host (test conditions non-ideal).

OS detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 10.46 seconds

------------------------

┌──(root㉿kali)-[~]
└─# nmap -O --osscan-guess 192.168.56.1
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 07:25 EDT
ipToPtr: 192.168.56.1 => 1.56.168.192.in-addr.arpa
Nmap scan report for 192.168.56.1
Host is up (0.0013s latency).
Not shown: 993 filtered tcp ports (no-response)
PORT     STATE SERVICE
80/tcp   open  http
135/tcp  open  msrpc
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
1801/tcp open  msmq
2103/tcp open  zephyr-clt
2107/tcp open  msmq-mgmt
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
Device type: bridge|specialized|VoIP phone|general purpose|webcam
Running (JUST GUESSING): Oracle Virtualbox (95%), lwIP 2.X (95%), 2N embedded (89%), Grandstream embedded (88%), Garmin embedded (85%)
OS CPE: cpe:/a:oracle:vm_virtualbox cpe:/a:lwip_project:lwip cpe:/h:2n:helios cpe:/h:grandstream:gxp1105 cpe:/a:lwip_project:lwip:2 cpe:/h:garmin:virb_elite
Aggressive OS guesses: Oracle Virtualbox lwIP NAT bridge (95%), 2N Helios IP VoIP doorbell (89%), Grandstream GXP1105 VoIP phone (88%), lwIP 2.1.0 - 2.2.0 (86%), lwIP 1.4.1 - 2.0.3 (86%), Garmin Virb Elite action camera (85%)
No exact OS matches for host (test conditions non-ideal).

OS detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 18.45 seconds
````


## Service Version Detection:
### 1. Description:

- Determines the versions of services running on open ports of the target host.

````bash

┌──(root㉿kali)-[~]
└─# nmap -sV 10.0.2.2
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 07:28 EDT
ipToPtr: 10.0.2.2 => 2.2.0.10.in-addr.arpa
Nmap scan report for 10.0.2.2
Host is up (0.0016s latency).
Not shown: 993 filtered tcp ports (no-response)
PORT     STATE SERVICE       VERSION
80/tcp   open  http          Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
135/tcp  open  msrpc         Microsoft Windows RPC
445/tcp  open  microsoft-ds?
1801/tcp open  msmq?
2107/tcp open  msrpc         Microsoft Windows RPC
2179/tcp open  vmrdp?
8099/tcp open  remoting      MS .NET Remoting services
MAC Address: 52:54:00:12:35:00 (QEMU virtual NIC)
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 68.61 seconds
                                                                          
┌──(root㉿kali)-[~]
└─# nmap -sV --version-trace 10.0.2.2
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 07:29 EDT
PORTS: Using ports open on 0% or more average hosts (TCP:1000, UDP:0, SCTP:0)
--------------- Timing report ---------------
  hostgroups: min 1, max 100000
  rtt-timeouts: init 1000, min 100, max 10000
  max-scan-delay: TCP 1000, UDP 1000, SCTP 1000
  parallelism: min 0, max 0
  max-retries: 10, host-timeout: 0
  min-rate: 0, max-rate: 0
---------------------------------------------
NSE: Using Lua 5.4.
NSE: Arguments from CLI: 
NSE: Loaded 47 scripts for scanning.
Packet capture filter (device eth0): arp and arp[18:4] = 0x080027FE and arp[22:2] = 0xDDA8
Overall sending rates: 20.64 packets / s, 866.78 bytes / s.
mass_dns: Using DNS server 1.1.1.1
mass_dns: Using DNS server 8.8.8.8
ipToPtr: 10.0.2.2 => 2.2.0.10.in-addr.arpa
mass_dns: 0.01s 0/1 [#: 2, OK: 0, NX: 0, DR: 0, SF: 0, TR: 1]
DNS resolution of 1 IPs took 0.50s. Mode: Async [#: 2, OK: 0, NX: 1, DR: 0, SF: 0, TR: 1, CN: 0]
Packet capture filter (device eth0): dst host 10.0.2.15 and (icmp or icmp6 or ((tcp or udp or sctp) and (src host 10.0.2.2)))
doAnyOutstandingRetransmits took 37ms
Overall sending rates: 166.61 packets / s, 7330.79 bytes / s.
NSOCK INFO [12.8380s] nsock_iod_new2(): nsock_iod_new (IOD #1)
NSOCK INFO [12.8390s] nsock_connect_tcp(): TCP connection requested to 10.0.2.2:80 (IOD #1) EID 8
NSOCK INFO [12.8390s] nsock_iod_new2(): nsock_iod_new (IOD #2)
NSOCK INFO [12.8440s] nsock_connect_tcp(): TCP connection requested to 10.0.2.2:135 (IOD #2) EID 16
````


