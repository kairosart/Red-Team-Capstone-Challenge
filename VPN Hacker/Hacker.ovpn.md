- Connect 
```
- sudo openvpn hacker.ovpn
```
2024-02-22 15:06:56 net_addr_v4_add: **12.100.1.X/24 dev tun1**
2024-02-22 15:06:56 net_route_v4_add: 10.200.103.21/32 via 12.100.1.1 dev [NULL] table 0 metric 1000
2024-02-22 15:06:56 sitnl_send: rtnl: generic error (-17): File exists
2024-02-22 15:06:56 NOTE: Linux route add command failed because route exists
2024-02-22 15:06:56 net_route_v4_add: 10.200.103.22/32 via 12.100.1.1 dev [NULL] table 0 metric 1000
2024-02-22 15:06:56 sitnl_send: rtnl: generic error (-17): File exists
2024-02-22 15:06:56 NOTE: Linux route add command failed because route exists
2024-02-22 15:06:56 Initialization Sequence Completed

- Check the adapters.
```
ip a
```
t**un1**: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UNKNOWN group default qlen 500
    link/none 
    inet 12.100.1.12/24 scope global tun1
       valid_lft forever preferred_lft forever
    inet6 fe80::f161:42dd:657:92/64 scope link stable-privacy 
       valid_lft forever preferred_lft forever

[[Net Enumeration]]
