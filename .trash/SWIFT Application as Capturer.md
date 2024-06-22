## Email

After submitting the SWIFT flag 17 you'll have an email like the following:

![[SWIFT Application as Capturer-20240619131355323.webp]]

### Getting flag 18
[[Flag Submission Process]]

When you go to submit the flag and select the [18 SWIFT Capturer Access] you'll see the following message:

*In order to proof that you have capturer access to the SWIFT system, a dummy transaction has been created for you.*

*Please look for a transaction with these details:*

*FROM:   631f60a3311625c0d29f5b32*
*TO:     6671df6e599a22670d98b587*

*Look for this transfer and capture (forward) the transaction.*

*Once you have captured the provided transaction, please enter Y to verify your access.*

## Payment Capturer users

List all **“Payment Capturer”** users.

PS C:\Users\kairosbank> `net group "Payment Capturers" /domain`

![[SWIFT Application as Capturer-20240619134101947.webp]]

### Change g.watson's passwword and RDP to WRK

- Open powershell as Administrator.
- Run the following code:
	`net user g.watson Hacker@123`
- RDP to WRK1 from BANKDC ass g.watson.
- Go to the Documents\SWIFT folder and you'll find a file called `swift`.
- Open it,
	![[SWIFT Application as Capturer-20240622134650494.webp]]


## Log in into Swift portal as Capturer using provided password

- From WRK1 computer Chrome browser go to http://swift.bank.thereserve.loc/.
- Log in as :
	Username: g.watson@bank.thereserve.loc
	Password: Corrected1996
	![[SWIFT Application as Capturer-20240622135930453.webp]]

[[SWIFT Web Capturer Access]]

## 