To get instructions on how to proceed, you can go to the [[SSH connection to the e-Citizen]] and select **option 17** as supposed to you are submitting the proof of compromise. You'll get the below instructions.

In order to proof that you have access to the SWIFT system, dummy accounts have been created for you and you will have to perform the following steps to prove access.

Account Details:
Source Email:           kairosdev@source.loc
Source Password:        xxjskPcgtohnGg
Source AccountID:       66844812599a227ad2a8eee7
Source Funds:           $ 10 000 000

Destination Email:      kairosdev@destination.loc
Destination Password:   H2Tu6LyGAqtIiw
Destination AccountID:  66844814599a227ad2a8eee8
Destination Funds:      $ 10



Using these details, perform the following steps:
1. [[RDP to JMP]] 
	Username: `kairosbank`
	Password: `Capstone1@`
3. Go to the [SWIFT web application](http://swift.bank.thereserve.loc/)
4. Log in with the Source Email.
5. Navigate to the **Make a Transaction page**.
6. Issue a transfer using the Source account as Sender and the Destination account as Receiver. You will have to use the corresponding account IDs.
	![[SWIFT Web Access-20240618153308780.webp]]

4. Issue the transfer for the full 10 million dollars.
	![[SWIFT Web Access-20240619134837785.webp]]
5. Once completed, request verification of your transaction here. Type Y.
6. Check your email once the transfer has been created and you'll get the PIN for your transaction and the flag.
7. Confirm the transaction using the PIN number received.
	![[SWIFT Web Access-20240701135015979.webp]]
	![[SWIFT Web Access-20240701135136648.webp]]
## Authenticate the flags on e-citizen

> Flag 17, Access to SWIFT application 

[[Flag Submission Process]]

**Next step:** [[Enumerate users CAPTURERS and APPROVERS]]
