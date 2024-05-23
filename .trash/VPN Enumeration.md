
## Enumerate ports and services
`nmap -A 10.200.113.12`  

	`PORT   STATE SERVICE VERSION`
	`22/tcp open  ssh  OpenSSH 7.6p1 Ubuntu 4ubuntu0.5 (Ubuntu Linux; protocol 2.0)`
	`80/tcp open  http    Apache httpd 2.4.29 ((Ubuntu))`
	`Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel``
`
## Enumerate port 80
	http://10.200.X.12
		![[Screenshot from 2024-02-11 20-09-38.png]]
		Posible user/password attack.



## Dirb
```
dirb http://10.200.X.12:80 /usr/share/wordlists/dirb/big.txt
```


![[vpn_dirb.png]]

## Download opvn file

http://10.200.X.12/vpn/corpUsername.ovpn

## Connect to the VPN
[[ovpn file]]


- Create a file on your Attacking Machine with the content of corpUsername.ovpn.
- Change the Remote IP to VPN Server IP.
- Save the file.
- Connect to the VPN.

