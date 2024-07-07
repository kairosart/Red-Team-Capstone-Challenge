By looking into the file, we can see two relevant fields, the remote, which has a 10.200.X.X IP address and the Subject CN, which usually identifies the user which the certificate is assigned to, with a value of “temp4”.

<font color="#00b050">remote 10.200.X.X 1194</font>

Certificate:
    Data:
        Version: 3 (0x2)
        Serial Number:
            25:74:28:af:9e:5b:47:c7:35:52:b4:e9:6a:0b:df:21
        Signature Algorithm: sha256WithRSAEncryption
        Issuer: CN=ChangeMe
        Validity
            Not Before: Feb 15 18:35:52 2023 GMT
            Not After : Feb 12 18:35:52 2033 GMT
        <font color="#00b050">Subject: CN=temp4</font>

This means that the file might not be useful to connect to an internal network without modifications, like defining the remote IP correctly and adding the username to the CN field.
## Connect
```
sudo openvpn <filename>.ovpn
```
2024-03-13 06:21:28 net_route_v4_add: **10.200.X.21/32** via 12.100.1.1 dev [NULL] table 0 metric 1000
2024-03-13 06:21:28 net_route_v4_add: **10.200.X.22/32** via 12.100.1.1 dev [NULL] table 0 metric 1000

## VPN Connections

[[WRK1.corp.thereserve.loc 10.200.X.21]]
[[WRK2 Enumeration]]


