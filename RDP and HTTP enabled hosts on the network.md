## RDP
Let’s see if we can find other RDP enabled hosts on the network, using NMAP with the following command, where XXX is our subnet:

`$ nmap -p3389 -Pn 10.200.113.1-254 -open` 

![[RDP enabled hosts on the network-20240528143911389.webp]]


## HTTP
Let’s see if we can also find HTTP enabled hosts on the network, using NMAP with the following command, where XXX is our subnet:

`$ nmap -p80,443 -Pn 10.200.XXX.1-254 -open`

![[RDP and HTTP enabled hosts on the network-20240528144613713.webp]]
