After [[Connect via SSH (10.200.X.12)|connecting to VPN Sever]] via SSH from the Attacker Machine let's enumerate Server1.

root@ip-10-200-113-12:/home/ubuntu# `nmap -A 10.200.X.31`

Starting Nmap 7.60 ( https://nmap.org ) at 2024-05-29 19:53 UTC
Nmap scan report for ip-10-200-113-31.eu-west-1.compute.internal (10.200.113.31)
Host is up (0.00032s latency).
Not shown: 995 filtered ports
PORT     STATE SERVICE       VERSION
<font color="#00b050">22/tcp</font>   open  ssh           OpenSSH for_Windows_7.7 (protocol 2.0)
| ssh-hostkey: 
|   2048 82:ae:22:cc:49:19:d9:56:3e:44:c6:6a:e0:5d:48:af (RSA)
|   256 5a:27:8f:c0:5b:1c:5e:9b:58:ac:33:06:40:3d:e6:ce (ECDSA)
|_  256 73:6e:08:4c:4d:ab:33:c7:48:13:7c:81:7e:5f:cb:38 (EdDSA)

<font color="#00b050">135/tcp</font>  open  msrpc         Microsoft Windows RPC

<font color="#00b050">139/tcp</font>  open  netbios-ssn   Microsoft Windows netbios-ssn

<font color="#00b050">445/tcp</font>  open  microsoft-ds?

<font color="#00b050">3389/tcp</font> open  ms-wbt-server Microsoft Terminal Services
| ssl-cert: Subject: commonName=SERVER1.corp.thereserve.loc
| Not valid before: 2024-05-26T23:06:11
|_Not valid after:  2024-11-25T23:06:11
|_ssl-date: 2024-05-29T19:53:39+00:00; 0s from scanner time.
MAC Address: 02:D2:0C:A5:49:57 (Unknown)
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
Device type: specialized
Running (JUST GUESSING): AVtech embedded (87%)
Aggressive OS guesses: AVtech Room Alert 26W environmental monitor (87%)
No exact OS matches for host (test conditions non-ideal).
Network Distance: 1 hop
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
| smb2-security-mode: 
|   2.02: 
|_    Message signing enabled but not required
| smb2-time: 
|   date: 2024-05-29 19:53:44
|_  start_date: 1601-01-01 00:00:00

TRACEROUTE
HOP RTT     ADDRESS
1   0.32 ms ip-10-200-113-31.eu-west-1.compute.internal (10.200.113.31)

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 76.88 seconds

