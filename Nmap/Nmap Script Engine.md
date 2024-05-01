![Nmap](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*glOR7rKpTq8Y7ymG3p-UKg.jpeg)
## Execute Individual Script (WHOIS):
### 1. Description:

- Executes a WHOIS script to retrieve domain information for the target host.

````bash
┌──(root㉿kali)-[~]
└─# nmap -sn --script whois-* google.com 
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 08:33 EDT
ipToPtr: 142.250.179.78 => 78.179.250.142.in-addr.arpa
Nmap scan report for google.com (142.250.179.78)
Host is up (0.00083s latency).
Other addresses for google.com (not scanned): 2a00:1450:4007:819::200e
rDNS record for 142.250.179.78: par21s19-in-f14.1e100.net

Host script results:
| whois-domain: 
| 
| Domain name record found at whois.verisign-grs.com
|    Domain Name: GOOGLE.COM\x0D
|    Registry Domain ID: 2138514_DOMAIN_COM-VRSN\x0D
|    Registrar WHOIS Server: whois.markmonitor.com\x0D
|    Registrar URL: http://www.markmonitor.com\x0D
|    Updated Date: 2019-09-09T15:39:04Z\x0D
|    Creation Date: 1997-09-15T04:00:00Z\x0D
|    Registry Expiry Date: 2028-09-14T04:00:00Z\x0D
|    Registrar: MarkMonitor Inc.\x0D
|    Registrar IANA ID: 292\x0D
|    Registrar Abuse Contact Email: abusecomplaints@markmonitor.com\x0D
|    Registrar Abuse Contact Phone: +1.2086851750\x0D
|    Domain Status: clientDeleteProhibited https://icann.org/epp#clientDeleteProhibited\x0D
|    Domain Status: clientTransferProhibited https://icann.org/epp#clientTransferProhibited\x0D
|    Domain Status: clientUpdateProhibited https://icann.org/epp#clientUpdateProhibited\x0D
|    Domain Status: serverDeleteProhibited https://icann.org/epp#serverDeleteProhibited\x0D
|    Domain Status: serverTransferProhibited https://icann.org/epp#serverTransferProhibited\x0D
|    Domain Status: serverUpdateProhibited https://icann.org/epp#serverUpdateProhibited\x0D
|    Name Server: NS1.GOOGLE.COM\x0D
|    Name Server: NS2.GOOGLE.COM\x0D
|    Name Server: NS3.GOOGLE.COM\x0D
|    Name Server: NS4.GOOGLE.COM\x0D
|    DNSSEC: unsigned\x0D
|    URL of the ICANN Whois Inaccuracy Complaint Form: https://www.icann.org/wicf/\x0D
| >>> Last update of whois database: 2024-04-27T12:33:43Z <<<\x0D
| \x0D
| For more information on Whois status codes, please visit https://icann.org/epp\x0D
| \x0D
````

## Execute Individual Script (Traceroute Geolocation):
### 1. Description:

- Executes a traceroute geolocation script to determine the geographical

````bash
┌──(root㉿kali)-[~]
└─# nmap -traceroute  --script traceroute-geolocation www.google.com 
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 08:38 EDT
ipToPtr: 142.250.179.68 => 68.179.250.142.in-addr.arpa
Nmap scan report for www.google.com (142.250.179.68)
Host is up (0.00071s latency).
Other addresses for www.google.com (not scanned): 2a00:1450:4007:813::2004
rDNS record for 142.250.179.68: par21s19-in-f4.1e100.net
Not shown: 998 filtered tcp ports (no-response)
PORT    STATE SERVICE
80/tcp  open  http
443/tcp open  https

Host script results:
| traceroute-geolocation: 
|   HOP  RTT   ADDRESS                                    GEOLOCATION
|_  1    0.47  par21s19-in-f4.1e100.net (142.250.179.68)  - ,- 

TRACEROUTE (using port 80/tcp)
HOP RTT     ADDRESS
1   0.47 ms par21s19-in-f4.1e100.net (142.250.179.68)

Nmap done: 1 IP address (1 host up) scanned in 20.78 seconds
````


## Output Option in Nmap:
### 1. Description:

- Specifies the output format for Nmap scan results and saves them to files with the specified basename.

````bash
┌──(root㉿kali)-[~]
└─# nmap -oA scan 192.168.56.1
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 08:43 EDT
ipToPtr: 192.168.56.1 => 1.56.168.192.in-addr.arpa
Nmap scan report for 192.168.56.1
Host is up (0.00067s latency).
Not shown: 995 filtered tcp ports (no-response)
PORT    STATE SERVICE
80/tcp  open  http
135/tcp open  msrpc
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds
902/tcp open  iss-realsecure

Nmap done: 1 IP address (1 host up) scanned in 5.58 seconds
````

## Display Scan Statistics:
### 1. Description:

- Displays scan statistics at specified intervals during the Nmap scan.

````bash
┌──(root㉿kali)-[~]
└─# nmap -stats-every 2s 192.168.56.1
Starting Nmap 7.95SVN ( https://nmap.org ) at 2024-04-27 08:45 EDT
ipToPtr: 192.168.56.1 => 1.56.168.192.in-addr.arpa
Stats: 0:00:02 elapsed; 0 hosts completed (1 up), 1 undergoing SYN Stealth Scan
SYN Stealth Scan Timing: About 4.85% done; ETC: 08:45 (0:00:20 remaining)
Stats: 0:00:04 elapsed; 0 hosts completed (1 up), 1 undergoing SYN Stealth Scan
SYN Stealth Scan Timing: About 16.75% done; ETC: 08:45 (0:00:15 remaining)
Stats: 0:00:06 elapsed; 0 hosts completed (1 up), 1 undergoing SYN Stealth Scan
SYN Stealth Scan Timing: About 26.10% done; ETC: 08:45 (0:00:14 remaining)
Stats: 0:00:08 elapsed; 0 hosts completed (1 up), 1 undergoing SYN Stealth Scan
SYN Stealth Scan Timing: About 30.60% done; ETC: 08:45 (0:00:16 remaining)
Stats: 0:00:10 elapsed; 0 hosts completed (1 up), 1 undergoing SYN Stealth Scan
SYN Stealth Scan Timing: About 50.30% done; ETC: 08:45 (0:00:09 remaining)
Stats: 0:00:12 elapsed; 0 hosts completed (1 up), 1 undergoing SYN Stealth Scan
SYN Stealth Scan Timing: About 60.80% done; ETC: 08:45 (0:00:07 remaining)
Stats: 0:00:14 elapsed; 0 hosts completed (1 up), 1 undergoing SYN Stealth Scan
SYN Stealth Scan Timing: About 79.70% done; ETC: 08:45 (0:00:03 remaining)
Stats: 0:00:16 elapsed; 0 hosts completed (1 up), 1 undergoing SYN Stealth Scan
SYN Stealth Scan Timing: About 91.60% done; ETC: 08:45 (0:00:01 remaining)
Nmap scan report for 192.168.56.1
Host is up (0.0015s latency).
Not shown: 995 filtered tcp ports (no-response)
PORT    STATE SERVICE
80/tcp  open  http
135/tcp open  msrpc
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds
912/tcp open  apex-mesh

Nmap done: 1 IP address (1 host up) scanned in 17.00 seconds
````


