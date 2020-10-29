This is the first iteration of my github repository.
This repository was created by Adrien Daley-Frenette 
Contact info: 
Email: w0420897@nscc.ca
Secondary email: frenetteas@gmail.com
This Git Repo was created for Matt Redmonds OSYS3030 course provided by Nova scotia community collage
commits arnt accurate due to trying to figure them out

These are config files from a Ubuntu server 20.04 linux distro and contains files configured to ips in the 10.0.0.0/24 network and the 192.168.2.0/24 network. 
192 network being the public network for the server and internet access for the client. 
The purpose of this applance was to familiarize myself with dns(bind9), dhcp, firewalls(ufw) and proxy servers(squid).

This is a in progress build

The ips on the adapters are as follows.

ens38: 10.0.0.250/24
ens33: 192.168.2.50/24

The sevices provided are DNS, DHCP, UFW Masquardeing and squid proxy server redirects.

How to set up.
This enviroment was built on a Virtual machine based off vmware
Go to https://releases.ubuntu.com/20.04/ and download the serve distro, proceed to do a basic install, be sure to download the bind9, dhcp, UFW, and squid services 
using the apt-get install commands. Once that has been completed you can download winscp or your preferance in order to move the files to the proper location easly.
Files needed 00-installer-config.yaml , named.conf.local , db.adrien.sysninja , named.conf.options , dhcpd.conf , before.rules , sysctl.conf and squid.conf


Each directory to be modified:

/etc/netplan
/etc/bind
/etc/dhcp
/etc/ufw    
/etc/squid

What to replace or upload to the directories and where:

00-installer-config.yaml belongs in /etc/netplan
named.conf.local , db.adrien.sysninja and named.conf.options belong in /etc/bind
dhcpd.conf belongs in /etc/dhcp
before.rules and sysctl.conf belong in /etc/ufw
squid.conf belongs in /etc/squid

Items you may have to modify:

If modification is necessary my personal preferance is to pull the file to a windows machine and use vscode to replace the file

Be sure to modify IP addresses as needed for your own network.

If you need to mdify the static IP please modify 00-installer-config.yaml
if you need to adjust dns sevice fowarders please view the named.conf.options file 
if you need to adjust the DNS service itself please modify the paths and FQDNs in named.conf.local and db.adrien.sysninja
If you need to adjust the dhcp please modify the domain(lines 10-11) and pool(lines 52-62) under dhcpd.conf 
If you need to change the ip for Masquerade please view before.rules and edit line 13
If you need to active or deactivate ipv4 or ipv6 fowarding please vist the sysctl.conf and comment or uncomment lines 10-12  
If you need to adjust the proxys redirect and block please view squid.conf lines 1188-1212 or ctrl w to search using keyword acl mynet src
Currently the proxy will block neverssl.com and redirect you to http://google.com


Changelog:
Changed squid proxy config to not rick roll you on redirect. will now redirect to google
Added direct link to ubuntu server download



