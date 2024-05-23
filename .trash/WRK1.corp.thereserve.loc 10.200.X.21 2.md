```
$ nmap -A 10.200.X.21 -Pn

```

## SSH
22/tcp   open  ssh           OpenSSH for_Windows_7.7 (protocol 2.0)
| ssh-hostkey: 
|   2048 21:78:e2:79:d3:93:ee:f9:aa:70:94:ec:01:b3:a5:8f (RSA)
|   256 e0:f7:b6:67:c9:93:b5:74:0f:0a:83:ff:ef:55:c8:9a (ECDSA)
|_  256 bd:83:0c:e3:b4:4f:78:f2:e3:4a:52:03:3c:a5:ce:58 (ED25519)

## SMB
135/tcp  open  msrpc         Microsoft Windows RPC
139/tcp  open  netbios-ssn   Microsoft Windows netbios-ssn
445/tcp  open  microsoft-ds?

Host script results:
| smb2-security-mode: 
|   3:1:1: 
|_    Message signing enabled but not required
| smb2-time: 
|   date: 2024-02-16T18:26:44
|_  start_date: N/A

## RDP
3389/tcp open  ms-wbt-server Microsoft Terminal Services
| ssl-cert: Subject: commonName=WRK1.corp.thereserve.loc
| Not valid before: 2024-02-12T08:43:21
|_Not valid after:  2024-08-13T08:43:21
| rdp-ntlm-info: 
|   Target_Name: CORP
|   NetBIOS_Domain_Name: CORP
|   NetBIOS_Computer_Name: WRK1
|   DNS_Domain_Name: corp.thereserve.loc
|   DNS_Computer_Name: WRK1.corp.thereserve.loc
|   DNS_Tree_Name: thereserve.loc
|   Product_Version: 10.0.17763
|_  System_Time: 2024-02-16T18:26:43+00:00
|_ssl-date: 2024-02-16T18:27:23+00:00; 0s from scanner time.

