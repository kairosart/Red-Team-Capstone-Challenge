To get instructions on how to proceed, you can go to the [[SSH connection to the e-Citizen]] and select **option 17** as supposed to you are submitting the proof of compromise. You'll get the below instructions.

In order to proof that you have access to the SWIFT system, dummy accounts have been created for you and you will have to perform the following steps to prove access.

Account Details:
Source Email:           kairosdev@source.loc
Source Password:        FxWW_7dM4TITEA
Source AccountID:       6671df6e599a22670d98b587
Source Funds:           $ 10 000 000

Destination Email:      kairosdev@destination.loc
Destination Password:   Wl4r7AIox51Xng
Destination AccountID:  6671df70599a22670d98b588
Destination Funds:      $ 10 000 000


Using these details, perform the following steps:
1. Go to the [SWIFT web application](http://swift.bank.thereserve.loc/)
2. Navigate to the **Make a Transaction page**.
3. Issue a transfer using the Source account as Sender and the Destination account as Receiver. You will have to use the corresponding account IDs.
	![[SWIFT Web Access-20240618153308780.webp]]

4. Issue the transfer for the full 10 million dollars.
	![[SWIFT Web Access-20240619134837785.webp]]
5. Once completed, request verification of your transaction here (No need to check your email once the transfer has been created). Type Y.

### Getting flag 17
[[Flag Submission Process]]

**Next step:** [[Enumerate users CAPTURERS and APPROVERS]]
