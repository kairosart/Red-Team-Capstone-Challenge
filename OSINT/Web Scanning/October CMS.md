http://web.thereserve.loc/october/index.php code.
```
 <meta name="generator" content="**OctoberCMS**">
```

### About October CMS
https://octobercms.com/features

### Admin Panel
http://web.thereserve.loc/october/index.php/backend/backend/auth/signin
![[octobercms_admin_panel 1.png]]

### Accessing with default credentials (admin/admin)
Proxy the request to Burp and you'll get the following response:
> `A user was found to match all plain text credentials however hashed credential &quot;password&quot; did not match.`

login=admin