## Enumeration
## All ports 

```
sudo nmap -sV -sT -O -p 1-65535 10.200.103.11

```

PORT      STATE SERVICE       VERSION
22/tcp    open  ssh           OpenSSH for_Windows_7.7 (protocol 2.0)
25/tcp    open  smtp          hMailServer smtpd
80/tcp    open  http          Microsoft IIS httpd 10.0
110/tcp   open  pop3          hMailServer pop3d
135/tcp   open  msrpc         Microsoft Windows RPC
139/tcp   open  netbios-ssn   Microsoft Windows netbios-ssn
143/tcp   open  imap          hMailServer imapd
445/tcp   open  microsoft-ds?
587/tcp   open  smtp          hMailServer smtpd
3306/tcp  open  mysql         MySQL 8.0.31
3389/tcp  open  ms-wbt-server Microsoft Terminal Services
5985/tcp  open  http          Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
33060/tcp open  mysqlx?
47001/tcp open  http          Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
49664/tcp open  msrpc         Microsoft Windows RPC
49665/tcp open  msrpc         Microsoft Windows RPC
49666/tcp open  msrpc         Microsoft Windows RPC
49667/tcp open  msrpc         Microsoft Windows RPC
49668/tcp open  msrpc         Microsoft Windows RPC
49669/tcp open  msrpc         Microsoft Windows RPC
49670/tcp open  msrpc         Microsoft Windows RPC
49680/tcp open  msrpc         Microsoft Windows RPC

Network Distance: 2 hops
Service Info: Host: **MAIL**; OS: **Windows**; CPE: cpe:/o:microsoft:windows


## Ports and Services
```
	nmap -p 22,25,80,110,135,139,143,445,587,3306,3389,5985,33060,47001 -A 10.200.103.11 -v
```

PORT     STATE SERVICE       VERSION
22/tcp   open  ssh           OpenSSH for_Windows_7.7 (protocol 2.0)
| ssh-hostkey: 
|   2048 f3:6c:52:d2:7f:e9:0e:1c:c1:c7:ac:96:2c:d1:ec:2d (RSA)
|   256 c2:56:3c:ed:c4:b0:69:a8:e7:ad:3c:31:05:05:e9:85 (ECDSA)
|_  256 d3:e5:f0:73:75:d5:20:d9:c0:bb:41:99:e7:af:a0:00 (ED25519)

25/tcp   open  smtp          hMailServer smtpd
| smtp-commands: MAIL, SIZE 20480000, AUTH LOGIN, HELP
|_ 211 DATA HELO EHLO MAIL NOOP QUIT RCPT RSET SAML TURN VRFY

80/tcp   open  http          Microsoft IIS httpd 10.0
| http-methods: 
|   Supported Methods: OPTIONS TRACE GET HEAD POST
|_  Potentially risky methods: TRACE
|_http-server-header: Microsoft-IIS/10.0
|_http-title: IIS Windows Server

110/tcp  open  pop3          hMailServer pop3d
|_pop3-capabilities: UIDL TOP USER

135/tcp  open  msrpc         Microsoft Windows RPC

139/tcp  open  netbios-ssn   Microsoft Windows netbios-ssn

143/tcp  open  imap          hMailServer imapd
|_imap-capabilities: ACL NAMESPACE IMAP4 OK IMAP4rev1 completed QUOTA IDLE RIGHTS=texkA0001 CAPABILITY CHILDREN SORT

445/tcp  open  microsoft-ds?

587/tcp  open  smtp          hMailServer smtpd
| smtp-commands: MAIL, SIZE 20480000, AUTH LOGIN, HELP
|_ 211 DATA HELO EHLO MAIL NOOP QUIT RCPT RSET SAML TURN VRFY

3306/tcp open  mysql         MySQL 8.0.31
|_ssl-date: TLS randomness does not represent time
| mysql-info: 
|   Protocol: 10
|   Version: 8.0.31
|   Thread ID: 12
|   Capabilities flags: 65535
|   Some Capabilities: IgnoreSpaceBeforeParenthesis, SupportsLoadDataLocal, ODBCClient, LongColumnFlag, SupportsTransactions, FoundRows, DontAllowDatabaseTableColumn, ConnectWithDatabase, Speaks41ProtocolNew, Speaks41ProtocolOld, IgnoreSigpipes, LongPassword, SupportsCompression, SwitchToSSLAfterHandshake, InteractiveClient, Support41Auth, SupportsMultipleResults, SupportsMultipleStatments, SupportsAuthPlugins
|   Status: Autocommit
|   Salt: \x0D_\x02R^RH(\x1AjsEK\x04*\x11\x7F
| \x1D}
|_  Auth Plugin Name: caching_sha2_password
| ssl-cert: Subject: commonName=MySQL_Server_8.0.31_Auto_Generated_Server_Certificate
| Issuer: commonName=MySQL_Server_8.0.31_Auto_Generated_CA_Certificate
| Public Key type: rsa
| Public Key bits: 2048
| Signature Algorithm: sha256WithRSAEncryption
| Not valid before: 2023-01-10T07:46:11
| Not valid after:  2033-01-07T07:46:11
| MD5:   1bd2:ba34:dd9d:39a0:fba2:5013:eb1f:b3f6
|_SHA-1: 406b:cedd:04f3:dd8e:1784:2fd6:cefd:a0d7:1382:4cdf

3389/tcp open  ms-wbt-server Microsoft Terminal Services
|_ssl-date: 2024-02-18T18:34:36+00:00; +1s from scanner time.
| rdp-ntlm-info: 
|   Target_Name: THERESERVE
|   NetBIOS_Domain_Name: THERESERVE
|   NetBIOS_Computer_Name: MAIL
|   DNS_Domain_Name: thereserve.loc
|   DNS_Computer_Name: MAIL.thereserve.loc
|   DNS_Tree_Name: thereserve.loc
|   Product_Version: 10.0.17763
|_  System_Time: 2024-02-18T18:34:27+00:00
| ssl-cert: Subject: commonName=MAIL.thereserve.loc
| Issuer: commonName=MAIL.thereserve.loc
| Public Key type: rsa
| Public Key bits: 2048
| Signature Algorithm: sha256WithRSAEncryption
| Not valid before: 2024-02-16T15:35:33
| Not valid after:  2024-08-17T15:35:33
| MD5:   ed6e:c970:b140:fc34:908f:1179:d6f0:2499
|_SHA-1: cd87:9908:a40a:7b83:0eb6:dc2a:3c06:54a5:869e:f155
Service Info: Host: MAIL; OS: Windows; CPE: cpe:/o:microsoft:windows

5985/tcp  open  http          Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
|_http-server-header: Microsoft-HTTPAPI/2.0
|_http-title: Not Found

33060/tcp open  mysqlx?
| fingerprint-strings: 
|   DNSStatusRequestTCP, LDAPSearchReq, NotesRPC, SSLSessionReq, X11Probe, afp: 
|     Invalid message"
|     HY000
|   LDAPBindReq: 
|     *Parse error unserializing protobuf message"
|     HY000
|   oracle-tns: 
|     Invalid message-frame."
|_    HY000

47001/tcp open  http          Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
|_http-title: Not Found
|_http-server-header: Microsoft-HTTPAPI/2.0

Host script results:
| smb2-time: 
|   date: 2024-02-18T18:34:28
|_  start_date: N/A
| smb2-security-mode: 
|   3:1:1: 
|_    Message signing enabled but not required

Aggressive OS guesses: Microsoft Windows Server 2019 (96%), Microsoft Windows 10 1709 - 1909 (93%), Microsoft Windows Server 2012 (93%), Microsoft Windows Vista SP1 (92%), Microsoft Windows Longhorn (92%), Microsoft Windows 10 1709 - 1803 (91%), Microsoft Windows 10 1809 - 2004 (91%), Microsoft Windows Server 2012 R2 (91%), Microsoft Windows Server 2012 R2 Update 1 (91%), Microsoft Windows Server 2016 build 10586 - 14393 (91%)

No exact OS matches for host (test conditions non-ideal).
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=263 (Good luck!)
IP ID Sequence Generation: Incremental
Service Info: Host: MAIL; OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
| smb2-time: 
|   date: 2024-02-21T19:07:17
|_  start_date: N/A
|_clock-skew: mean: 2s, deviation: 0s, median: 2s
| smb2-security-mode: 
|   3:1:1: 
|_    Message signing enabled but not required

TRACEROUTE (using port 80/tcp)
HOP RTT       ADDRESS
1   129.35 ms 10.50.99.1
2   232.34 ms corp.th3reserve.lo (10.200.103.11)

NSE: Script Post-scanning.
Initiating NSE at 14:07
Completed NSE at 14:07, 0.00s elapsed
Initiating NSE at 14:07
Completed NSE at 14:07, 0.00s elapsed
Initiating NSE at 14:07
Completed NSE at 14:07, 0.00s elapsed
Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 64.42 seconds
           Raw packets sent: 62 (4.104KB) | Rcvd: 62 (3.828KB)
