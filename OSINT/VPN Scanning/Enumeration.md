
## Enumerate ports and services.
	PORT   STATE SERVICE VERSION
	22/tcp open  ssh  OpenSSH 7.6p1 Ubuntu 4ubuntu0.5 (Ubuntu Linux; protocol 2.0)
	80/tcp open  http    Apache httpd 2.4.29 ((Ubuntu))
	Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

## Enumerate port 80
	http://10.200.X.12
	
![[thereserve 1.png]]

Posible user/password attack.
## Gobuster
	http://vpn.thereserve.loc/vpn
		Found config VPN
		
		http://vpn.thereserve.loc/vpn/corpUsername.ovpn
		
	http://vpn.thereserve.loc/vpns

![[corpusernamevpn.png]]
## Connect to the VPN
corpUsername.vpn
	- Create a file on your Attacking Machine with the content of corpUsername.ovpn.
	- Change the Remote IP to VPN Server IP.
	- Save the file.
	- Connect to the VPN.

