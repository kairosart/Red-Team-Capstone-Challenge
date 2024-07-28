
![[Network Map after compromising CORPDC-20240604150302129.webp]]

Looking at the network topology, we can see that the AD Forest contains two child domains–**CORPDC** and **BANKDC**–and a parent **ROOTDC**. Our shortest path to compromise the entire forest would be to compromise the **ROOTDC** first. This will give us access to the other machines on the network.
Starting with some enumeration, we can see that we have a bidirectional trust between **CORP** and **ROOT**:

![[Network Map after compromising CORPDC-20240615160020547.webp]]

The easier way of taking advantage of this Domain Trust if we have Domain Admin rights in the child Domain.

Bidirectional domain trusts allow two Active Directory domains to trust each other, meaning users and resources from one domain can access resources in the other domain, and vice versa. Here are some common ways attackers abuse bidirectional domain trusts:

1. **Pass-the-Ticket (PtT) Attacks**: With access to one domain, attackers can use PtT attacks to obtain Ticket Granting Tickets (TGTs) for users in the trusted domain. These TGTs can then be used to authenticate to resources in the trusted domain, allowing the attacker to move laterally.
2. **Pass-the-Hash (PtH) Attacks**: Similar to PtT attacks, PtH attacks involve stealing password hashes of privileged accounts in one domain and using them to authenticate to resources in the trusted domain. This allows attackers to move laterally without needing to know the plaintext passwords.
3. **Golden Ticket Attacks**: Attackers can forge Kerberos tickets, known as Golden Tickets, using the KRBTGT account’s password hash from one domain and the trust relationship between the domains. With a Golden Ticket, attackers gain unrestricted access to any resource in the trusted domain.
4. **Silver Ticket Attacks**: Silver Ticket attacks involve forging Service Principal Name (SPN) tickets to impersonate specific services in the trusted domain. This allows attackers to access resources associated with those SPNs without needing the service account’s credentials.
5. **Abusing AdminSDHolder**: If the domains have differing security postures or if the trust is not properly configured, attackers may abuse AdminSDHolder, a mechanism in Active Directory that enforces permissions on sensitive accounts like Domain Admins. By escalating privileges or modifying permissions through AdminSDHolder, attackers can gain unauthorized access to critical accounts and resources in the trusted domain.
6. **Exploiting Misconfigurations**: Attackers may look for misconfigurations in the trust relationship, such as weak authentication settings or improper trust permissions. Exploiting these misconfigurations can provide avenues for unauthorized access and lateral movement.

**Next step:** [[RDP to BANKDC from host CORPDC]]
