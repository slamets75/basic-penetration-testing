---
title: Materi BPT
updated: 2025-12-10 23:37:52Z
created: 2025-12-10 23:37:43Z
latitude: -6.24744660
longitude: 107.14845210
altitude: 0.0000
---

# 🎯 **SLIDE DECK — PELATIHAN PENETRATION TESTING DASAR – FULL MODULE**

* * *

# **📘 Modul 1 — Setup Environment Pentest**

* * *

## **Slide 1 – Judul**

**Setup Environment Penetration Testing**  
Kali Linux – Metasploitable2 – DVWA  
Instruktur: *Nama Anda*

* * *

## **Slide 2 – Tujuan Pembelajaran**

Peserta mampu:

- Memahami environment pentest
    
- Menggunakan Kali Linux sebagai platform tools
    
- Menjalankan target vulnerable (Metasploitable2 & DVWA)
    
- Mengidentifikasi workflow pentest
    

* * *

## **Slide 3 – Tools Pentest**

- **Kali Linux** – OS untuk ethical hacking
    
- **Metasploitable 2** – Vulnerable machine
    
- **DVWA** – Web application vuln platform
    
- **VirtualBox / VMware / Proxmox**
    

* * *

## **Slide 4 – Instalasi Kali Linux**

- 2 vCPU
    
- 4 GB RAM
    
- 30 GB Disk
    
- Network: NAT + Host-Only
    
- Default tools sudah built-in
    

* * *

## **Slide 5 – Instalasi Metasploitable 2**

- Import OVA
    
- Network: Host-Only
    
- Services vulnerable:
    
    - VSFTPD Backdoor
        
    - Tomcat
        
    - MySQL weak password
        
    - Mutillidae, DVWA, WebDav, dll.
        

* * *

## **Slide 6 – Setup DVWA**

- Requirement: Apache, PHP, MySQL
    
- Konfigurasi: `config/config.inc.php`
    
- Set security LOW/MEDIUM/HIGH
    
- Enable php-gd & mysqli
    

* * *

* * *

# 📘 **Modul 2 — Prerequisites Fundamental**

* * *

## **Slide 7 – Network Fundamental**

- IP Address
    
- Subnet & Routing
    
- DNS
    
- HTTP/HTTPS
    
- Firewall basics
    

* * *

## **Slide 8 – OSI Layer**

1.  Physical
    
2.  Data Link
    
3.  Network
    
4.  Transport
    
5.  Session
    
6.  Presentation
    
7.  Application
    

* * *

## **Slide 9 – TCP/IP**

- Layer 1: Network Interface
    
- Layer 2: Internet
    
- Layer 3: Transport
    
- Layer 4: Application  
    Protokol: TCP, UDP, IP, ARP, ICMP
    

* * *

## **Slide 10 – Common Services**

| Service | Port | Keterangan |
| --- | --- | --- |
| SSH | 22  | remote login |
| HTTP | 80  | web |
| HTTPS | 443 | secure web |
| FTP | 21  | file transfer |
| SMB | 445 | file sharing |
| MySQL | 3306 | database |

* * *

## **Slide 11 – Linux Fundamental**

- Navigasi file
    
- Permission
    
- Process management
    
- Networking command
    

* * *

## **Slide 12 – Command Linux**

- `ls`, `cd`, `pwd`, `cp`, `mv`
    
- `chmod`, `chown`
    
- `top`, `ps`
    
- `ip a`, `ping`, `netstat`, `tcpdump`
    

* * *

## **Slide 13 – Note Keeping**

Tools recommended:

- CherryTree
    
- Obsidian
    
- Joplin
    
- Standard Notes  
    Digunakan untuk dokumentasi pentest.
    

* * *

* * *

# 📘 **Modul 3 — Introduction to Cyber Security**

* * *

## **Slide 14 – Apa itu Cyber Security?**

“Upaya melindungi sistem, jaringan, dan data dari serangan digital.”

* * *

## **Slide 15 – Penetration Testing**

Simulasi serangan terkontrol untuk menemukan celah keamanan sebelum diserang pihak lain.

* * *

## **Slide 16 – Proses Pentest (PTES)**

1.  Pre-engagement
    
2.  Intelligence gathering
    
3.  Threat modeling
    
4.  Vulnerability identification
    
5.  Exploitation
    
6.  Post-exploitation
    
7.  Reporting
    

* * *

## **Slide 17 – Cyber Kill Chain**

1.  Reconnaissance
    
2.  Weaponization
    
3.  Delivery
    
4.  Exploitation
    
5.  Installation
    
6.  C2
    
7.  Actions on objective
    

* * *

## **Slide 18 – CIA Triad**

- **Confidentiality**
    
- **Integrity**
    
- **Availability**
    

* * *

## **Slide 19 – DAD Model (Offensive Security)**

- **Disclosure**
    
- **Alteration**
    
- **Destruction**
    

* * *

## **Slide 20 – Adversaries**

- Script Kiddies
    
- Hacktivist
    
- Cyber Criminal
    
- Insider Threat
    
- State-Sponsored APT
    

* * *

* * *

# 📘 **Modul 4 — Planning & Scoping**

* * *

## **Slide 21 – Rules of Engagement (RoE)**

Isi utama:

- Scope asset
    
- Teknik yang boleh digunakan
    
- Jam uji
    
- Larangan uji
    
- Proses eskalasi insiden
    
- Dokumentasi & reporting
    

* * *

## **Slide 22 – VA & PT**

| VA (Vulnerability Assessment) | PT (Penetration Testing) |
| --- | --- |
| Deteksi kelemahan | Eksploitasi kelemahan |
| Non-intrusive | Intrusive |
| Automated | Manual/otomasi |

* * *

## **Slide 23 – Scope of Work VAPT**

- IP range
    
- Domain
    
- Infrastruktur
    
- Web application
    
- API
    
- Mobile apps
    

* * *

## **Slide 24 – Type of Assessment**

- Black Box
    
- Grey Box
    
- White Box
    
- External/Internal Test
    

* * *

## **Slide 25 – Testing Standards**

- **OWASP Web Testing Guide**
    
- **NIST SP 800-115**
    
- **OSSTMM**
    
- **PTES**
    

* * *

## **Slide 26 – Compliance Regulatory**

- ISO 27001
    
- PCI DSS
    
- GDPR
    
- HIPAA
    
- PDP Indonesia
    

* * *

* * *

# 📘 **Modul 5 — Information Gathering**

* * *

## **Slide 27 – Jenis Recon**

- Passive Recon
    
- Active Recon
    
- OSINT Analysis
    

* * *

## **Slide 28 – Google Dorking**

Contoh:

- `site:example.com ext:php`
    
- `"index of" password`
    

* * *

## **Slide 29 – Passive Scanning Tools**

- Whois
    
- Nslookup
    
- Censys.io
    
- Shodan.io
    
- TheHarvester
    
- Recon-ng
    

* * *

## **Slide 30 – Active Scanning Tools**

- Nmap
    
- Nessus
    
- OpenVAS
    
- Masscan
    

* * *

## **Slide 31 – Contoh Nmap Command**

`nmap -sV -A 192.168.1.10nmap -p- 192.168.1.10nmap --script vuln target.com`

* * *

* * *

# 📘 **Modul 6 — Exploitation**

* * *

## **Slide 32 – Jenis Serangan Web**

- XSS
    
- SQL Injection
    
- LFI/RFI
    
- Command Injection
    
- CSRF
    
- SSRF
    
- Directory Traversal
    

* * *

## **Slide 33 – XSS**

- Reflected
    
- Stored
    
- DOM Based  
    Payload:
    

`<script>alert(1)</script>`

* * *

## **Slide 34 – SQL Injection**

Teknik:

- Boolean-based
    
- Error-based
    
- Union-based
    
- Blind Injection  
    Tools: SQLmap
    

* * *

## **Slide 35 – Credential Stuffing**

- Gunakan wordlist
    
- Tools: Hydra, Burp Suite Intruder
    

* * *

## **Slide 36 – Membuat Wordlist**

Tools:

- Cewl → berdasarkan konten web
    
- Crunch → berdasarkan pola karakter
    

* * *

## **Slide 37 – Tools Exploit**

- Hydra (bruteforce)
    
- Sqlmap (SQLi automation)
    
- Metasploit (exploit framework)
    

* * *

* * *

# 📘 **Modul 7 — Metasploit Framework**

* * *

## **Slide 38 – Arsitektur Metasploit**

- Modules
    
- Payload
    
- Exploit
    
- Auxiliary
    
- Post modules
    

* * *

## **Slide 39 – Workflow Metasploit**

1.  search exploit
    
2.  use module
    
3.  set RHOST / RPORT
    
4.  set payload
    
5.  exploit
    

* * *

## **Slide 40 – Contoh Metasploit**

`search vsftpduse exploit/unix/ftp/vsftpd_234_backdoorset RHOST 192.168.1.10exploit`

* * *

* * *

# 📘 **Modul 8 — Praktik: DVWA & Metasploitable2**

* * *

## **Slide 41 – DVWA Modules**

- Brute Force
    
- Command Injection
    
- File Upload
    
- SQL Injection
    
- XSS
    
- CSRF
    

* * *

## **Slide 42 – Metasploitable Vulnerabilities**

- VSFTPD backdoor
    
- UnrealIRCd backdoor
    
- Weak SSH passwords
    
- PHPMyAdmin default creds
    
- Tomcat manager default login
    

* * *

* * *

# 📘 **Modul 9 — Reporting**

* * *

## **Slide 43 – Pentest Report Components**

- Executive Summary
    
- Scope & Methodology
    
- Findings
    
- Impact & Risk Rating
    
- Evidence
    
- Remediation
    
- Appendix (logs, payloads, screenshots)
    

* * *

## **Slide 44 – Severity Rating**

- Critical
    
- High
    
- Medium
    
- Low
    
- Informational
    

* * *

## **Slide 45 – Tools Membuat Report**

- Dradis
    
- Serpico
    
- Markdown
    
- Obsidian
    
- WPS/Word Template
    

* * *

* * *

# 📘 **Slide 46 – Penutup**

Terima kasih.  
Sesi praktik akan dilakukan menggunakan:

- Kali Linux
    
- Metasploitable2
    
- DVWA
    
- Metasploit
    
- Nmap
    
- Burp Suite