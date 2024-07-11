$ `proxychains4 -q xfreerdp /v:10.200.113.102 /u:Administrator /p:Hacker@123`

## Disable CORPDC firewall

Disabled firewall.

![[RDP to CORPDC with the Administrator's credentials-20240711140249092.webp]]
 
PS C:\Users\Administrator> `Set-MpPreference -DisableRealTimeMonitoring $true`

## Disable virus protection

Disable virus and turned off Real-time protection from settings.
- **Open Windows Security:**
    
    - Click on the **Start** button.
    - Type **Windows Security** in the search bar and press Enter.
    - Alternatively, you can also find it by navigating through **Settings > Update & Security > Windows Security**.
    - ![[Preparing the path-20240607143234384.webp]]


## Authenticate the flags on e-citizen

>Flag-8, Administrative access to Corporate Division Tier 0 Infrastructure

**Next step:** [[Golden Ticket Attack with mimikatz]]
