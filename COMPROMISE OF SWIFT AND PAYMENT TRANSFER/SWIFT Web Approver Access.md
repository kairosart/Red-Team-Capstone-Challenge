To get instructions on how to proceed, you can go to the [[SSH connection to the e-Citizen]] and select **option 19** as supposed to you are submitting the proof of compromise. You'll get the below instructions.

*In order to proof that you have approver access to the SWIFT system, a dummy transaction has been created for you.*

*Please look for a transaction with these details:*

FROM:   631f60a3311625c0d29f5b31
TO:     66844812599a227ad2a8eee7


*Look for this transfer and approve (forward) the transaction.*

*Once you have approved the provided transaction, please enter Y to verify your access.*

## Rdp to BANKDC as BANK\\kairosbank
- Check for groups in JMP on powershell.
- PS C:\Windows\system32> `net groups /domain`
	![[SWIFT Web Approver Access-20240622153349232.webp]]
	There is also a group as **“Payment Approvers”**
- Change the a.holt's password.
	- PS C:\Windows\system32> `net user a.holt Hacker@123 /domain`

## Rdp from BANKDC to JMP as a.holt

Computer: `10.200.113.61`
- Checking the folders contents you'll find a note for the approver.
- Go to `C:\Users\a.holt\Documents\Swift`.
- Open the swift file.
	![[Enumerate users CAPTURERS and APPROVERS-20240621155345848.webp]]

> There is a note that clarifies why AD credentials did not work for a.holt on the bank login page.
> **"The approvers account credentials are not same as their AD account."**


## Navigate to [SWIFT web application](http://swift.bank.thereserve.loc/)

- Notice that when trying to log in to the bank application using Google Chrome, the username and password fields get auto-filled! On checking the Settings in the browser, we see that credentials are saved for the site! We can log in now and approve the transaction.
	![[SWIFT Web Approver Access-20240623154143575.webp]]

- Go to Transactions and approve your last transaction.
	![[SWIFT Web Approver Access-20240623154427457.webp]]

- Once completed, request verification of your transaction. Type Y.
- Check your email to get the flag.

## Authenticate the flags on e-citizen

> Flag 19, Access to SWIFT application as approver  

[[Flag Submission Process]]

**Next step:** [[SWIFT PAYMENT MADE]]
