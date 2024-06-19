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

