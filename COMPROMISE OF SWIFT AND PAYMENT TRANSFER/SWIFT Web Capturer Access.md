After submitting the SWIFT Web Access, got you'll get an email saying:

![[SWIFT Application as Capturer-20240619131355323.webp]]

To get instructions on how to proceed, you can go to the [[SSH connection to the e-Citizen]] and select **option 18** as supposed to you are submitting the proof of compromise. You'll get the below instructions.

`In order to proof that you have capturer access to the SWIFT system, a dummy transaction has been created for you.`

`Please look for a transaction with these details:`

`FROM:   631f60a3311625c0d29f5b32`
`TO:     66844812599a227ad2a8eee7`

`Look for this transfer and capture (forward) the transaction.`

`Once you have captured the provided transaction, please enter Y to verify your access.`

## Compromise capturer in a position to make transfers

From [[Enumerate users CAPTURERS and APPROVERS]] you can see the users with therir properties.
The users of “Payement Capturers” can log in to only **WORK1**.


- Navigate to [SWIFT web application](http://swift.bank.thereserve.loc/)
- Log in as g.watson@bank.thereserve.loc:Corrected1996
- Go to Transactions and approve your last transaction.  
  ![[SWIFT Web Capturer Access-20240715134751952.webp]]
    
- Once completed, request verification of your transaction. Type Y.
- Check your email to get the flag.



## Authenticate the flags on e-citizen

> Flag 18, Access to SWIFT application as capturer  

**Next step:** [[SWIFT Web Approver Access]]

