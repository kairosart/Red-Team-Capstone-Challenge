**SWIFT (Society for Worldwide Interbank Financial Telecommunications) is the actual system that is used by banks for backend transfers. In this assessment, a core backend system has been created. However, for security reasons, intentional inaccuracies have been introduced into this process.**


---


SWIFT backend exposes an internal web application at [http://swift.bank.thereserve.loc/,](http://swift.bank.thereserve.loc/,) which TheReserve uses to facilitate transfers. The government has provided a general process for transfers. To transfer funds:

1. A customer makes a request that funds should be transferred and receives a transfer code.

2. The customer contacts the bank and provides this transfer code.  

3. An employee with the capturer role authenticates to the SWIFT application and captures the transfer.  

4. An employee with the approver role reviews the transfer details and, if verified, approves the transfer. This has to be performed from a jump host.  

5. Once approval for the transfer is received by the SWIFT network, the transfer is facilitated and the customer is notified.
  

Separation of duties is performed to ensure that no single employee can both capture and approve the same transfer.

**Next step:** [[Project Goal]]

