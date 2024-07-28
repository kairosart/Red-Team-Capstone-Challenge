Yoou can access via IP or via hostname if you have add the machine to the /etc/hosts file.
http://10.200.X.13
http://web.thereserve.loc
![[thereserve 2.png]]

## Meet the team
“Meet the Team” page might give us some useful information regarding the employees of the organization, the team’s structure, roles, and email addresses.

http://web.thereserve.loc/october/index.php/demo/meettheteam
![[the_team 1.png]]

## Names
By accessing the path identified (/october/themes/demo/assets/images/) we can see that a vulnerability of directory listing exists, allowing us to get all the names associated with images.
http://web.thereserve.loc/october/themes/demo/assets/images/

![[images 1.png]]

There is a strong chance that those names are using the same nomenclature as their corporate email addresses. By looking at the “ContactUs” page, we can see that we can send our CV and other type of documents to applications@corp.thereserve.loc address. This information disclosures the domain used in corporate emails, which allows us to compile a potential list of usernames: 
● antony.ross@corp.thereserve.loc ● ashley.chan@corp.thereserve.loc ● brenda.henderson@corp.thereserve.loc ● charlene.thomas@corp.thereserve.loc ● christopher.smith@corp.thereserve.loc ● emily.harvey@corp.thereserve.loc ● keith.allen@corp.thereserve.loc ● laura.wood@corp.thereserve.loc ● leslie.morley@corp.thereserve.loc ● lynda.gordon@corp.thereserve.loc ● martin.savage@corp.thereserve.loc ● mohammad.ahmed@corp.thereserve.loc ● paula.bailey@corp.thereserve.loc ● rhys.parsons@corp.thereserve.loc ● roy.sims@corp.thereserve.loc

**Next step:** [[OSINT/WebMail Scanning/Technologies of the website]]
