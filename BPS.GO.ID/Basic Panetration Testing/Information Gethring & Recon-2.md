---
title: Information Gethring & Recon
updated: 2025-12-16 11:13:48Z
created: 2025-12-16 11:13:24Z
latitude: -6.20239360
longitude: 106.65270990
altitude: 0.0000
---

Information Gethring & Recon

Gather Information using Advanced Google Hacking Techniques  
intitle:login site:eccouncil.org

ceh filetype:pdf

intitle:login site:.pk

inurl:certification site:eccouncil.org

intitle:  
allintitle:  
anchor:  
inanchor:  
allinanchor:  
link:  
related:  
info:  
location:

theHarverster  
theHarvester -d nfacademy.id -b yahoo

(untuk cek virus)  
https://www.virustotal.com/gui/home/upload

\[online\]  
https://dnsdumpster.com/

\# recon-ng  
help  
workspaces create nama_workspace  
workspaces load nama_workspace  
marketplace install recon/domains-hosts/hackertarget  
options list

optins set SOURCE nfacademy.id  
run

\## Scanning  
host discovery  
port / service discovery  
banner grabbing / versi dll  
evesion firewall

TCP/IP 3 way handshacking

&nbsp;          # nmap -A -T4 scanme.nmap.org

zenmap (Versi GUI)

\[convert xml to html\]  
sudo apt update -y && sudo apt install xsltproc -y

ex:  
sudo nmap -sV --script vuln -oX nmap-report.xml 192.168.103.4 && xsltproc nmap-report.xml -o nmap-report.html

&nbsp;

└─$ sudo ./Downloads/ZAP_2_16_1_unix.sh

&nbsp;

chmod +x Downloads/ZAP_2_16_1_unix.sh  
chmod +x Downloads/ZAP_2_16_1_unix.sh

install docker  
apt install docker.io

OpenVAS  
https://greenbone.github.io/docs/latest/22.4/container/#docker-compose-file

curl -f -O -L [https://greenbone.github.io/docs/latest/\\\_static/docker-compose.yml](https://greenbone.github.io/docs/latest/%5C_static/docker-compose.yml) --output-dir "$DOWNLOAD_DIR"

&nbsp;

https://github.com/greenbone/openvas-scanner

git clone https://github.com/greenbone/openvas-scanner.git  
cd openvas-scanner

sudo curl -fsSL "https://get.docker.com" | sh  
atau  
sudo apt install docker.io

docker build -t &lt;image-name&gt; -f .docker/prod.Dockerfile .

DVWA  
docker run --rm -it -p 80:80 vulnerables/web-dvwa

&nbsp;

nmap -sn 192.168.10.0/24

Referensi  
https://attack.mitre.org/  
Information gathering: https://osintframework.com/

&nbsp;

&nbsp;