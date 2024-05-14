## nmap
`$ nmap -p- 10.200.X.21 -Pn -v`

PORT     STATE SERVICE
22/tcp   open  ssh
135/tcp  open  msrpc
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
3389/tcp open  ms-wbt-server
5985/tcp open  wsman

## RDP
```
$ nmap --script "rdp-enum-encryption or rdp-vuln-ms12-020 or rdp-ntlm-info" -p 3389 -T4 10.200.103.21 -Pn
```

PORT     STATE SERVICE
3389/tcp open  ms-wbt-server
| rdp-enum-encryption: 
|   Security layer
|     CredSSP (NLA): SUCCESS
|     CredSSP with Early User Auth: SUCCESS
|_    RDSTLS: SUCCESS
| rdp-ntlm-info: 
|   Target_Name: CORP
|   NetBIOS_Domain_Name: CORP
|   NetBIOS_Computer_Name: **<font color="#ffc000">WRK1</font>**
|   DNS_Domain_Name: corp.thereserve.loc
|   DNS_Computer_Name: **<font color="#ffc000">WRK1.corp.thereserve.loc</font>**
|   DNS_Tree_Name: thereserve.loc
|   Product_Version: 10.0.17763
|_  System_Time: 2024-02-14T20:56:45+00:00

Nmap done: 1 IP address (1 host up) scanned in 6.06 seconds
