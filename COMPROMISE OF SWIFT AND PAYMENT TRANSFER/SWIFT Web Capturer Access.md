After submitting the SWIFT Web Access, got yu'll get an email saying:

![[SWIFT Application as Capturer-20240619131355323.webp]]

To get instructions on how to proceed, you can go to the [[SSH connection to the e-Citizen]] and select **option 18** as supposed to you are submitting the proof of compromise. You'll get the below instructions.

*In order to proof that you have capturer access to the SWIFT system, a dummy transaction has been created for you.*

*Please look for a transaction with these details:*

From: 631f60a3311625c0d29f5b31
To: 6682fa22599a226d03485319

*Look for this transfer and capture (forward) the transaction.*

*Once you have captured the provided transaction, please enter Y to verify your access.*

## Compromise capturer in a position to make transfers

From [[Enumerate users CAPTURERS and APPROVERS]] you can see the users with therir properties.
The users of “Payement Capturers” can log in to only **WORK1**.

### Change the a.barker's password

- On BANKDC powershell run:
	PS C:\Windows\system32>`net user g.watson Hacker@123 /domain`

- Log in to **WORK1** as user **g.watson**.
- Open the C:\Users\g.watson\Documents\SWIFT document which contains a password.
	![[SWIFT Application as Capturer-20240622134650494.webp]]


## Navigate to [SWIFT web application](http://swift.bank.thereserve.loc/)

- Log in as g.watson@bank.thereserve.loc:Corrected1996
- Go to Transactions and approve your last transaction.  
    ![SWIFT Web Approver Access-20240623154427457.webp](app://7e9b693e1be8380628bc863b9de3e1fc772f/media/sf_obsidian/Red%20Team%20Capstone%20Challenge/SWIFT%20Web%20Approver%20Access-20240623154427457.webp?1719171867435)
    
- Once completed, request verification of your transaction. Type Y.
    
- Check your email to get the flag.



## Authenticate the flags on e-citizen

> Flag 18, Access to SWIFT application as capturer  

**Next step:** [[SWIFT Web Approver Access]]

