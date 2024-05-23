```
$ nmap -A 10.200.X.22 -Pn

```

## SSH
22/tcp   open  ssh           OpenSSH for_Windows_7.7 (protocol 2.0)
| ssh-hostkey: 
|   2048 e6:f0:fb:5b:24:28:68:13:da:dd:c5:5f:67:4e:be:4f (RSA)
|   256 93:f5:8f:4c:31:15:fc:8e:38:03:3e:d5:b7:1c:ed:d3 (ECDSA)
|_  256 56:3f:8a:33:a4:1f:dc:11:9a:a1:67:a6:7d:f8:76:18 (ED25519)

## SMB
135/tcp  open  msrpc         Microsoft Windows RPC
139/tcp  open  netbios-ssn   Microsoft Windows netbios-ssn
445/tcp  open  microsoft-ds?

Host script results:
| smb2-security-mode: 
|   3:1:1: 
|_    Message signing enabled but not required
|_clock-skew: mean: -1s, deviation: 0s, median: -1s
| smb2-time: 
|   date: 2024-02-14T20:50:32
|_  start_date: N/A

## RDP
3389/tcp open  ms-wbt-server Microsoft Terminal Services
| rdp-ntlm-info: 
|   Target_Name: CORP
|   NetBIOS_Domain_Name: CORP
|   NetBIOS_Computer_Name: WRK2
|   DNS_Domain_Name: corp.thereserve.loc
|   DNS_Computer_Name: WRK2.corp.thereserve.loc
|   DNS_Tree_Name: thereserve.loc
|   Product_Version: 10.0.17763
|_  System_Time: 2024-02-14T20:50:29+00:00
|_ssl-date: 2024-02-14T20:51:07+00:00; -1s from scanner time.
| ssl-cert: Subject: commonName=WRK2.corp.thereserve.loc
| Not valid before: 2024-02-12T08:43:20
|_Not valid after:  2024-08-13T08:43:20
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows
