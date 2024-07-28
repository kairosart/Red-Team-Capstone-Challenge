So far, we have gathered a lot of useful information from our OSINT research, by passive means or just browsing normally. Alongside the identified technologies and versions, we manage to compile a list of potential usernames and passwords. Now we need to identify a point of failure and get inside the perimeter.

## Port and Service scan using nmap (web.thereserve.loc)

We use the flags -sC (running default scripts) and -sV (performing version detection, as well as -Pn (disable host discovery, or also known as ping scanning, considering the hosts alive).

### web.thereserve.loc

```
nmap -sC -sV -Pn 10.200.121.13
```

![[nmap_web.png]]

### vpn.thereserve.loc

```
nmap -sC -sV -Pn 10.200.121.12
```

![[nmap_vpn 1.png]]

### mail.thereserve.loc

```
nmap -sC -sV -Pn 10.200.121.11
```



![[nmap_mail.png|939]]
**Next step:** [[Gobuster]]
