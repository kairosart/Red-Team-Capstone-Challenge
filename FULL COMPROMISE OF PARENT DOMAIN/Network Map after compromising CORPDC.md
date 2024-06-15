
![[Network Map after compromising CORPDC-20240604150302129.webp]]

Looking at the network topology, we can see that the AD Forest contains two child domains–**CORPDC** and **BANKDC**–and a parent **ROOTDC**. Our shortest path to compromise the entire forest would be to compromise the **ROOTDC** first. This will give us access to the other machines on the network.
Starting with some enumeration, we can see that we have a bidirectional trust between **CORP** and **ROOT**:

![[Network Map after compromising CORPDC-20240615160020547.webp]]

The easier way of taking advantage of this Domain Trust if we have Domain Admin rights in the child Domain.

**KRBTGT** is the account used for Microsoft’s implementation of Kerberos. Its name is derived from Kerberos (KRB) and Ticket Granting Ticket (TGT) and acts as the service account for the Kerberos Distribution Center (KDC) service, which handles all Kerberos ticket requests.
The KRBTGT is responsible for the encryption of all Kerberos tickets in the domain and its password is shared across all domain controllers, so that they can verify the authenticity of the received TGT when a resource access is requested.
