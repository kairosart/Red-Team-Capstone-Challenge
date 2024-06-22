### RDP to JMP

- Rdp as BANK\kairosbank.
- Check for groups in JMP on powershell.
- PS C:\Windows\system32> `net groups /domain`
	![[SWIFT Web Approver Access-20240622153349232.webp]]
	There is also a group as **“Payment Approvers”**
- Change the a.holt's password.
	- PS C:\Windows\system32> `net user a.holt Hacker@123 /domain`

- Rdp from BANKDC to JMP as a.holt.
- 
Checking the folders contents you'll find a note for the approver.
- Go to `C:\Users\a.holt\Documents\Swift`.
- Open the swift file.
	![[Enumerate users CAPTURERS and APPROVERS-20240621155345848.webp]]


