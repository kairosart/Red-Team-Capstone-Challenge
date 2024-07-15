Scanned from VPN server.
## Enumerate ports and services
```
sudo nmap -A 10.200.X.102
```

PORT     STATE SERVICE       VERSION
**22/tcp   open  ssh           OpenSSH for_Windows_7.7 (protocol 2.0)**
| ssh-hostkey: 
|   2048 8f:54:ec:97:2e:10:85:d5:82:6d:fe:b0:c3:44:33:7d (RSA)
|   256 6f:93:4b:6b:c5:59:40:6f:29:88:ec:04:85:69:a2:ad (ECDSA)
|_  256 a4:9c:57:ef:0f:9b:62:21:c7:73:3f:a1:87:00:4c:15 (EdDSA)

**53/tcp   open  domain        Microsoft DNS**

**88/tcp   open  kerberos-sec  Microsoft Windows Kerberos (server time: 2024-03-10 19:48:27Z)**

**135/tcp  open  msrpc         Microsoft Windows RPC**

**139/tcp  open  netbios-ssn   Microsoft Windows netbios-ssn****
**
**389/tcp  open  ldap          Microsoft Windows Active Directory LDAP (Domain: thereserve.loc0., Site: Default-First-Site-Name)**
| ssl-cert: Subject: 
| Subject Alternative Name: DNS:CORPDC.corp.thereserve.loc
| Not valid before: 2023-02-14T18:56:50
|_Not valid after:  2024-02-14T18:56:50
|_ssl-date: 2024-03-10T19:49:09+00:00; 0s from scanner time.

**445/tcp  open  microsoft-ds?**

**464/tcp  open  kpasswd5?**

**593/tcp  open  ncacn_http    Microsoft Windows RPC over HTTP 1.0**

**636/tcp  open  ssl/ldap      Microsoft Windows Active Directory LDAP (Domain: thereserve.loc0., Site: Default-First-Site-Name)**
| ssl-cert: Subject: 
| Subject Alternative Name: DNS:CORPDC.corp.thereserve.loc
| Not valid before: 2023-02-14T18:56:50
|_Not valid after:  2024-02-14T18:56:50
|_ssl-date: 2024-03-10T19:49:09+00:00; 0s from scanner time.

**3268/tcp open  ldap          Microsoft Windows Active Directory LDAP (Domain: thereserve.loc0., Site: Default-First-Site-Name)**
| ssl-cert: Subject: 
| Subject Alternative Name: DNS:CORPDC.corp.thereserve.loc
| Not valid before: 2023-02-14T18:56:50
|_Not valid after:  2024-02-14T18:56:50
|_ssl-date: 2024-03-10T19:49:10+00:00; +1s from scanner time.

**3269/tcp open  ssl           Microsoft SChannel TLS**
| fingerprint-strings: 
|   TLSSessionReq: 
|     VMzJ
|     loc1
|     thereserve1
|     corp1
|     THERESERVE-CA0
|     230214185650Z
|     240214185650Z0
|     \xe5f
|     p\x803
|     Ptu)
|     (0&0
|_    ldap:///CN=THERESERVE-CA,CN=CORPDC,CN=CDP,CN=Public%20Key%20
| ssl-cert: Subject: 
| Subject Alternative Name: DNS:CORPDC.corp.thereserve.loc
| Not valid before: 2023-02-14T18:56:50
|_Not valid after:  2024-02-14T18:56:50
|_ssl-date: 2024-03-10T19:49:09+00:00; 0s from scanner time.

**3389/tcp open  ms-wbt-server Microsoft Terminal Services**
| ssl-cert: Subject: commonName=CORPDC.corp.thereserve.loc
| Not valid before: 2024-03-09T10:07:58
|_Not valid after:  2024-09-08T10:07:58
|_ssl-date: 2024-03-10T19:49:09+00:00; 0s from scanner time.
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at https://nmap.org/cgi-bin/submit.cgi?new-service :
SF-Port3269-TCP:V=7.60%I=7%D=3/10%Time=65EE0EAB%P=x86_64-pc-linux-gnu%r(TL
SF:SSessionReq,673,"\x16\x03\x03\x06n\x02\0\0M\x03\x03e\xee\x0e\xa7t\xd7\x
SF:08<\xdee\x1a\x81\x85yg\xc37\xc1g\t\x20\x94\x1d\x1fQC\xed\x8b\x1ez\|\x02
SF:\x2053\0\x004\[\x81L\x0b\xd0\x04\xf3}\x98\xa2\xb1VMzJ\xb41\xccw\x9d\xd1
SF:\rXw{\xabG\0/\0\0\x05\xff\x01\0\x01\0\x0b\0\x05\xf7\0\x05\xf4\0\x05\xf1
SF:0\x82\x05\xed0\x82\x04\xd5\xa0\x03\x02\x01\x02\x02\x13\?\0\0\0\x05\xf6\
SF:xce\xb4H2\x89\xdeP\0\0\0\0\0\x050\r\x06\t\*\x86H\x86\xf7\r\x01\x01\x0b\
SF:x05\x000_1\x130\x11\x06\n\t\x92&\x89\x93\xf2,d\x01\x19\x16\x03loc1\x1a0
SF:\x18\x06\n\t\x92&\x89\x93\xf2,d\x01\x19\x16\nthereserve1\x140\x12\x06\n
SF:\t\x92&\x89\x93\xf2,d\x01\x19\x16\x04corp1\x160\x14\x06\x03U\x04\x03\x1
SF:3\rTHERESERVE-CA0\x1e\x17\r230214185650Z\x17\r240214185650Z0\x000\x82\x
SF:01\"0\r\x06\t\*\x86H\x86\xf7\r\x01\x01\x01\x05\0\x03\x82\x01\x0f\x000\x
SF:82\x01\n\x02\x82\x01\x01\0\xc6Z\xc8<\xc2\xbf\x0bl\xf3\x16f\x82\x1f\\\xe
SF:5f\xe3\xe27\|\xf4\x03p\\\x803\xa5\xe4\x1b\x0e\x17\xf1\x89\xa6\x8dl\xd5S
SF:9v\xe61\xd5o\x0e\xa6\x9f\x18U\xb1\x82\xc5E\x7f\xb1HX\x1b\xc78\x0by\x18\
SF:xb9\xef\r\]\xdau\xd8}\xc992\x88\xe1\x1b\xb2\x9eT\x10\xa0\x87\xf9\(\xd1\
SF:x98\xa2\xe5\xdd\xab\xdeGc\xb3I\xbb\xdb=J\xfeU\x7f\xe4\xaa\xa9\x7f\xa7{&
SF:\xba\x88\xddey\x89t\xf4x\x01\xfbj7s\x92\xb7\xff\xcd\xad\x0f&\xe0\xf4\xd
SF:62\x06\xdeRf\xd1\xd09\xd5\xf0\x18U\x80\x02\xbf3\xcc\xa3\x06\x85\xe2w%\x
SF:d3\xcd\x11\x1e\xd0h\x08&\xe8\xc2sJ\xf2n\xdd\xd4\xbe\xbd\xaa\xe8\xa7\xd8
SF:\xb3\xd6\xb4\xb3q\xc2\n~\x1b\x8e\x03\xe2\x82x1\x81\xef_H\xc7dm\xa5\xe3\
SF:xc6pN\x8b#\xc4\xc4\xd5\xac\xd1\xea\xec\xef\xce\xba\xdc\xd4Y\xae\xcd\xc4
SF:\x13Ptu\)\xac\xde\x1a9\xa7\x04\xd4\xc1\xf4\xbf\xeecaP\xfa\xc5<\xf9\xf9\
SF:x10\xd6\x0b\xeco\xa9u\xa5\x02\x03\x01\0\x01\xa3\x82\x02\xff0\x82\x02\xf
SF:b08\x06\t\+\x06\x01\x04\x01\x827\x15\x07\x04\+0\)\x06!\+\x06\x01\x04\x0
SF:1\x827\x15\x08\x85\x94\xa5H\x87\xe8\xbaN\x84\xd9\x9f\x08\x83\x94\x81V\x
SF:81\x9d\xfa`\x81\x13\x01\x1c\x02\x01n\x02\x01\x000\)\x06\x03U\x1d%\x04\"
SF:0\x20\x06\x08\+\x06\x01\x05\x05\x07\x03\x02\x06\x08\+\x06\x01\x05\x05\x
SF:07\x03\x01\x06\n\+\x06\x01\x04\x01\x827\x14\x02\x020\x0e\x06\x03U\x1d\x
SF:0f\x01\x01\xff\x04\x04\x03\x02\x05\xa005\x06\t\+\x06\x01\x04\x01\x827\x
SF:15\n\x04\(0&0\n\x06\x08\+\x06\x01\x05\x05\x07\x03\x020\n\x06\x08\+\x06\
SF:x01\x05\x05\x07\x03\x010\x0c\x06\n\+\x06\x01\x04\x01\x827\x14\x02\x020\
SF:x1d\x06\x03U\x1d\x0e\x04\x16\x04\x14\x1duT\xc0\x93\x8c\xd3\xc3\xe2\xf3\
SF:^\xdf\xe9q`\[\x0b\x99%\x110\x1f\x06\x03U\x1d#\x04\x180\x16\x80\x14\xa6\
SF:x0c\xfcR\xb2\xc8H\xe00UB\x90M\xca4\x20s\x94\xa9\xc60\x81\xcd\x06\x03U\x
SF:1d\x1f\x04\x81\xc50\x81\xc20\x81\xbf\xa0\x81\xbc\xa0\x81\xb9\x86\x81\xb
SF:6ldap:///CN=THERESERVE-CA,CN=CORPDC,CN=CDP,CN=Public%20Key%20");
MAC Address: 02:21:96:FD:E8:3F (Unknown)
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
OS fingerprint not ideal because: Missing a closed TCP port so results incomplete
No OS matches for host
Network Distance: 1 hop
Service Info: Host: CORPDC; OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
|_nbstat: NetBIOS name: CORPDC, NetBIOS user: <unknown>, NetBIOS MAC: 02:21:96:fd:e8:3f (unknown)
| smb2-security-mode: 
|   2.02: 
|_    Message signing enabled and required
| smb2-time: 
|   date: 2024-03-10 19:49:10
|_  start_date: 1601-01-01 00:00:00

TRACEROUTE
HOP RTT     ADDRESS
1   0.29 ms ip-10-200-10-102.eu-west-1.compute.internal (10.200.10.102)

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 109.00 seconds
