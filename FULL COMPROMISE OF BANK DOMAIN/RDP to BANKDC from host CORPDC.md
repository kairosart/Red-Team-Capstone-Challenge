
Now that we are Enterprise Admins, the compromise of the other child domain should be easy. We can start by connecting through RDP into the **BANKDC** from **ROOTDC**, with our newly created user:


Computer: `10.200.X.101`

### RDP to BANKDC

1. **Open Remote Desktop Connection**:
    
    - Press `Win + R`, type `mstsc`, and press `Enter`.
    - ![[Maintain persistence-20240615154522456.webp]]
1. **Enter the Host Machine’s Name or IP Address**:
    
    - In the Remote Desktop Connection window, enter the computer name or IP address of the host machine.
3. **Enter Credentials**:
    
    - When prompted, enter the username and password for the account on the host machine.
    - Username: `kairosroot`
    - Password: `Capstone1@`
1. **Optional: Save Connection Settings**:
    
    - You can save the connection settings to an RDP file by clicking on **Show Options** > **Save As**.
5. **Connect**:
    
    - Click **Connect** to start the remote session.

    ![[RDP to BANKDC from host CORPDC-20240616153040546.webp]]

### Getting flags 13 and 14
[[Flag Submission Process]]

**Next step**: [[Create user at BANK Forest]]
