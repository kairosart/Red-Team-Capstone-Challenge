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

**Next step:** [[SWIFT Web Capturer Access]]


