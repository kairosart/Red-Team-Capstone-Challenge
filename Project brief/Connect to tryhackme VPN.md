Go to your [access](https://tryhackme.com/access) page. Select 'Redteamcapstonechallenge' from the VPN servers (under the network tab) and download your configuration file.

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/6093e17fa004d20049b6933e/room-content/a4f66137e423a4df6fc7556523665682.png)  

Use an OpenVPN client to connect. This example is shown on the [Linux](https://tryhackme.com/access#pills-linux) machine; use this guide to connect using [Windows](https://tryhackme.com/access#pills-windows) or [macOS](https://tryhackme.com/access#pills-macos).

Terminal

```
$ sudo openvpn redteamcapstonechallenge.ovpn
```

2024-03-05 04:39:33 TUN/TAP device <font color="#ffc000">capstone</font> opened
2024-03-05 04:39:33 net_iface_mtu_set: mtu 1500 for capstone
2024-03-05 04:39:33 net_iface_up: set capstone up
2024-03-05 04:39:33 net_addr_v4_add: 10.50.110.16/24 dev capstone
2024-03-05 04:39:33 net_route_v4_add: <font color="#ffc000">10.200.113.0/24</font> via 10.50.110.1 dev [NULL] table 0 metric 1000
2024-03-05 04:39:33 Initialization Sequence Completed


The message "Initialization Sequence Completed" tells you that you are now connected to the network. Return to your access page. You can verify you are connected by looking on your access page. Refresh the page, and you should see a green tick next to Connected. It will also show you your internal IP address.

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/6093e17fa004d20049b6933e/room-content/0a924f67f23923031c343eebb572607b.png)

**Next step:** [[Servers]]
