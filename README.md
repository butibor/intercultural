# intercultural

Router:
en
conf t
int gig0/0/switchesszam
ip address 192.168.13.1 255.255.255.128
description valami amiekell
no sh //!
int gig0/0/masikrouter
ip address 10.10.10.9 255.255.255.252
description routerek kozti kapcs
no sh //!
exit
ip dhcp pool Lan1
network 192.168.13.0 255.255.255.128
dns-server 192.168.13.129 
default-router 192.168.13.1
exit
ip dhcp excluded-address 192.168.13.120 192.168.13.127
Check dhcp

Server statikusan
192.168.13.129
255.255.255.128
192.168.13.254
192.168.13.129

Access point config
Ssid
WPA 2psk

Laptop háló kártya
Pc wiewlless connect Refresh

Smartphone config wireless ssid jelszó

Masikrouter
en
conf t
int gig0/0/otherrouter
ip address 10.10.10.10 255.255.255.252
description routerek kozti kapcs olat
no sh  !!
int gig0/0/switchfele
ip address 192.168.13.254 255.255.255.128
no sh !!

Server services dhcp on!
Def gateway 192.168.13.254 router ip
DNS server 192.168.13.129 sajat maga
Start ip
Subnet mask
Save

Server services http indexhtml
DNS on!
oldalam.hu 192.168.13.129 szerver ipje

Dhcp bekapcsolása a pcken
Ellenőrzés csukott boritek
Vagy command prompt ping ipcim

Router 1
hostname beirodanevet
enable password/secret en123
line con 0
password con123
login
exit
do wr !!
end
exit
con123
en
en123
banner motd #napi uzenet#
end
exit

Switch1
en
conf t
hostname sw1
enable secret en123
line con 0
password con123
login
exit
banner motd #valami#
exit
do wr !!
exit
con123
en123

Dinamikus routolas
Router1
en
conf t
router rip
ver 2
no auto-summary
network 192.168.13.0
network 10.10.10.8
passive-interface gig0/0/switchfele
exit
do wr

Router2
en
conf t
router rip
ver 2
no auto-summary
network 10.10.10.8
network 192.168.13.128
passive-interface gig0/0/switchfele
exit
do wr

Statikus routolas
Router1
ip route 192.168.13.128 255.255.255.128 10.10.10.10
do wr
ip route 192.168.1.0 255.255.255.0 10.10.10.10
ip route 10.10.10.0 255.255.255.252 10.10.10.10
do wr

Router 2
ip route 192.168.13.0 255.255.255.128 10.10.10.9
do wr
ip route 192.168.1.0 255.255.255.0 10.10.10.2
do wr

Server2
Statikusan adok neki egy ipt
Alhalozat adott
Def gateway a router ipje
Dns server a masikserver ipje

Sever 1
Service DNS 
Cisco.com ip masik server ipje 
add 
Web browser URL es jo
