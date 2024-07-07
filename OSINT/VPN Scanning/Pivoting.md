
So far you have compromised the VPN Server and you are root. Now you have to get access to the interior network. As you can see in this [image](https://docs.google.com/document/d/1W1_Ck-x7nQn1f0XNTezp6Y_KslWEIjCmp_8pLg_ucrs/edit#bookmark=id.z9s26cqsw79w) there are 3 tiers.

You can’t access that network because there’s a firewall in the middle. Use [[Pivoting overview]]to get access to the interior network.

Routing network traffic with [[Proxychains]].

On your Attacking Machine run the following.

$ `ssh -D 9050 ubuntu@10.200.X.12 -i rsa`

**Next step:** [[Enumerate 10.200.X.21]]