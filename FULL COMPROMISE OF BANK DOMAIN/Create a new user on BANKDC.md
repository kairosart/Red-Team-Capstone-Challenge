This account will be used to rdp to BANK Tier 2 Machines.

PS C:\Users\Administrator>`$pwd = convertTo-SecureString "Capstone1@" -AsPlainText -Force`

PS C:\Users\Administrator> `New-ADUser -Name "kairosbank" -AccountPassword $pwd -PasswordNeverExpires $true -Enabled $true`

PS C:\Users\Administrator>`$User = Get-ADUser -Identity "kairosbank"  -Server "bankdc.bank.thereserve.loc"`

PS C:\Users\Administrator>`$Group = Get-ADGroup -Identity "Domain Admins" -Server "bankdc.bank.thereserve.loc"`

PS C:\Users\Administrator>`Add-ADGroupMember -Identity $Group -Members $User -Server "bankdc.bank.thereserve.loc"`

### Check out the user and group

PS C:\Users\Administrator> `echo $user`

![[Create a new user on BANKDC-20240618142300177.webp]]

PS C:\Users\Administrator> `echo $group`

![[Create a new user on BANKDC-20240616154446455.webp]]


**Next step**: [[RDP to JMP]]
