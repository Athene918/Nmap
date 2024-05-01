# Nmap Scripts to Master

![Nmap](https://miro.medium.com/v2/resize:fit:720/format:webp/1*aCc8wKAC-7N-UPd1SgsAjw.jpeg)
1. http-title:
   - The script extracts the title of a web page from HTTP services. This is extremely useful for quickly identifying the content of a web page without manually visiting the URL. It can provide quick insights into the nature of the service behind a port, often revealing the application name or the content of the website.

````bash
nmap -p 80,443 --script=http-title 192.168.56.1

Nmap scan report for example.com (93.184.216.34)
Host is up (0.014s latency).

PORT    STATE SERVICE
80/tcp  open  http
|_http-title: Example Domain

443/tcp open  https
|_http-title: Example Domain
````

2. ssl-cert:

    - The script is designed to extract a server’s SSL certificate to provide information such as its validity, issuer, subject, and more. This script is particularly useful for verifying the authenticity and configuration of SSL/TLS services on a server, which is crucial for maintaining the security and integrity of encrypted communications.

    - The ssl-cert script can help identify potential security issues, such as expired certificates, certificates signed by untrusted or unknown authorities, or the use of weak encryption algorithms. It's commonly used during security assessments and for monitoring the SSL/TLS configurations of publicly accessible servers.

````bash
nmap -p 443 --script=ssl-cert <target-ip-or-domain>
Nmap scan report for example.com (93.184.216.34)
Host is up (0.020s latency).

PORT    STATE SERVICE
443/tcp open  https
| ssl-cert: Subject: commonName=example.com
| Issuer: commonName=Example CA
| Public Key type: rsa
| Public Key bits: 2048
| Signature Algorithm: sha256WithRSAEncryption
| Not valid before: 2021-01-01T00:00:00
| Not valid after:  2023-12-31T23:59:59
| MD5:   d4e5 f6g7 h8i9 j0k1 l2m3 n4o5 p6q7 r8s9
|_SHA-1: a1b2 c3d4 e5f6 g7h8 i9j0 k1l2 m3n4 o5p6 q7r8 s9t0
````

3. vuln:

    - The script is designed to detect vulnerabilities on target systems and can be used to identify known security weaknesses in network services, software applications, and protocols. The power of NSE (Nmap Scripting Engine) scripts, especially those in the vuln category, is that they enable automated scanning for vulnerabilities, making them a valuable resource for security assessments, audits, and compliance checks.

    - The scripts in the vuln category range from detecting specific CVEs (Common Vulnerabilities and Exposures) to identifying generic issues such as SQL injection vulnerabilities, cross-site scripting (XSS) vulnerabilities, or misconfigurations that could lead to security breaches.

````bash
nmap -p 80,443 --script=vuln <target-ip-or-domain>
Nmap scan report for example.com (93.184.216.34)
Host is up (0.030s latency).

PORT    STATE SERVICE
80/tcp  open  http
| http-vuln-cve2017-5638: 
|   VULNERABLE:
|   Apache Struts Dynamic Method Invocation Remote Code Execution
|     State: VULNERABLE
|     IDs:  CVE:CVE-2017-5638
|     Description: Apache Struts 2.x before 2.3.32 and 2.5.x before 2.5.10.1 allows remote attackers to execute arbitrary code via a crafted Content-Type, Content-Disposition, or Content-Length HTTP header.
|_    References: https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5638

443/tcp open  https
| ssl-vuln-cve2014-0224: 
|   VULNERABLE:
|   OpenSSL CCS Injection Vulnerability
|     State: VULNERABLE
|     IDs:  CVE:CVE-2014-0224
|     Description: OpenSSL before 0.9.8za, 1.0.0 before 1.0.0m, and 1.0.1 before 1.0.1h does not properly restrict processing of ChangeCipherSpec messages.
|_    References: https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2014-0224
````

4. smb-os-discovery:

      - The script is specifically designed to gather information about the operating system and network shares of a target machine using the SMB protocol. SMB (Server Message Block) is a network file sharing protocol that allows applications on a computer to read and write to files and to request services from server programs in a computer network.

      - The smb-os-discovery script can reveal details such as the operating system version, hostname, network domain, and workgroup, making it particularly useful in the early stages of a network penetration test or security assessment to identify potential targets and plan further exploitation or analysis.

````bash
nmap -p 445 --script=smb-os-discovery <target-ip-or-domain>
Nmap scan report for example.com (192.168.1.1)
Host is up (0.0010s latency).

PORT    STATE SERVICE
445/tcp open  microsoft-ds

| smb-os-discovery: 
|   OS: Windows 10 Pro 1909 (Windows 10 Pro 6.3)
|   OS CPE: cpe:/o:microsoft:windows_10::-
|   Computer name: example-pc
|   NetBIOS computer name: EXAMPLE-PC\x00
|   Domain name: example.com
|   Forest name: example.com
|   FQDN: example-pc.example.com
|_  System time: 2021-03-15T12:34:56-05:00
````

5. http-robots.txt:

  - The http-robots.txt script in Nmap is designed to retrieve and examine the contents of the robots.txt file from a web server. The file is a standard used by websites to communicate with web crawlers and other web robots which tells these bots which areas of the site should not be processed or scanned. While primarily used for search engine optimization (SEO) purposes to prevent certain pages from being indexed, the robots.txt file can also inadvertently reveal sensitive directories or pages that the website administrators would prefer to keep private.

  - By examining the robots.txt file, a security analyst can discover potentially interesting or sensitive paths on the website that could be further explored for vulnerabilities or valuable information.

````bash
nmap -p 80,443 --script=http-robots.txt <target-ip-or-domain>
Nmap scan report for example.com (93.184.216.34)
Host is up (0.030s latency).

PORT    STATE SERVICE
80/tcp  open  http
| http-robots.txt: 
|   User-agent: *
|   Disallow: /private/
|   Disallow: /admin/
|_  Disallow: /sensitive-info/

443/tcp open  https
| http-robots.txt: 
|   User-agent: *
|   Disallow: /private/
|   Disallow: /admin/
|_  Disallow: /sensitive-info/
````

6. ssh-hostkey:

 - SSH (Secure Shell) is a protocol used for secure remote login and other secure network services over an insecure network. The SSH keys are a pair of cryptographic keys that can be used to authenticate a server to a client and vice versa. The public key is shared openly and can be safely distributed, while the private key is kept secret.

 - The ssh-hostkey script in Nmap is designed to retrieve a server's public SSH keys. It can also obtain the key's fingerprints, which are shorter, human-readable hashes of the keys. These fingerprints can be used to verify the identity of the server to which you're connecting, helping to prevent Man-in-the-Middle (MitM) attacks.

````bash
nmap -p 22 --script=ssh-hostkey <target-ip-or-domain>
Nmap scan report for example.com (93.184.216.34)
Host is up (0.0020s latency).

PORT   STATE SERVICE
22/tcp open  ssh
| ssh-hostkey: 
|   2048 SHA256:abc123xyz456 (RSA)
|   256 SHA256:def789xyz012 (ECDSA)
|_  256 SHA256:ghi345xyz678 (ED25519)
````

7. dns-brute:

 - The script is designed for brute-forcing subdomains of a target domain using DNS queries. It attempts to find valid subdomains by guessing names and querying the DNS server to resolve them. This can be particularly useful in the reconnaissance phase of a penetration test or security audit, where discovering hidden or less obvious subdomains of a target can reveal additional attack vectors or information about the organization’s infrastructure.
 - The dns-brute script can take several arguments to customize its operation, including a custom dictionary file for subdomain names, the ability to set a maximum number of hosts to query, and more. However, for a basic usage example, you can run it without any special arguments.

````bash
nmap --script=dns-brute --script-args dns-brute.domain=example.com
Starting Nmap
Nmap scan report for example.com
Host is up.

Other addresses for example.com (not scanned): 93.184.216.34
| dns-brute: 
|   DNS Brute-force hostnames:
|     admin.example.com - 93.184.216.35
|     mail.example.com - 93.184.216.36
|     dev.example.com - 93.184.216.37
|_    vpn.example.com - 93.184.216.38
````