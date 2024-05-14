## Overview
TryHackMe, a cybersecurity consultancy firm, has been approached by the government of Trimento to perform a red team engagement against their Reserve Bank (TheReserve).![Trimento Logo](https://tryhackme-images.s3.amazonaws.com/user-uploads/6093e17fa004d20049b6933e/room-content/a29cffb908b62b9564316df5a43f69e9.png) 
Trimento is an island country situated in the Pacific. While they may be small in size, they are by no means not wealthy due to foreign investment. Their reserve bank has two main divisions:

- **Corporate** - The reserve bank of Trimento allows foreign investments, so they have a department that takes care of the country's corporate banking clients.  
    
- **Bank** - The reserve bank of Trimento is in charge of the core banking system in the country, which connects to other banks around the world.

![](https://lh7-us.googleusercontent.com/IqKYa6lfgYl2jXJTrLjeQQr9Yq9ziJGPTqKOB10LSoJ3sDwz5DeOaoX3j9KlW_TMHsSuQFNIdZpD42pWznnf40O8FH4os8ai8Zok280YdizjRVzmMSmMtt9nclFTFMMusPYsGEVwz8TV442V8rkxtzI)

The Trimento government has stated that the assessment will cover the entire reserve bank, including both its perimeter and internal networks. They are concerned that the corporate division while boosting the economy, may be endangering the core banking system due to insufficient segregation. The outcome of this red team engagement will determine whether the corporate division should be spun off into its own company.

**
## Project Goal

The purpose of this assessment is to evaluate whether the corporate division can be compromised and, if so, determine if it could compromise the bank division. A simulated fraudulent money transfer must be performed to fully demonstrate the compromise.

To do this safely, ==TheReserve will create two new core banking accounts for you. You will need to demonstrate that it's possible to transfer funds between these two accounts.== The only way this is possible is by gaining access to SWIFT, the core backend banking system.

![](https://lh7-us.googleusercontent.com/_MuHF0T5RHNNpcYyhet1GJC6-BVwkM5ABpy-yWsPTfC_8QbbrzhQl5R4kSggwyEz6LHYx55XenUb4LjMZBmXs3vFg3EVI-H6fmHiBj5sjWtOFGq7Ez61lBkIGPURIJO-Jd2y55xoIiNVKv2vOYD96Cs)

**

## Project Registration
**

To register, you need to get in touch with the government through its e-Citizen communication portal that uses SSH for communication. Here are the SSH details provided:

|   |   |
|---|---|
|SSH Username|e-citizen|
|SSH Password|stabilitythroughcurrency|
|SSH IP|X.X.X.250|

Once you complete the questions below, the network diagram at the start of the room will show the IP specific to your network. Use that information to replace the X values in your SSH IP.

Once you authenticate, you will be able to communicate with the e-Citizen system. Follow the prompts to register for the challenge, and save the information you get for future reference. Once registered, follow the instructions to verify that you have access to all the relevant systems.

---
### **Process

**

Submit all the answers from Task1 and Task2. That way you’ll get the first IPs.

![](https://lh7-us.googleusercontent.com/hr0Xx5eZMlm1wy5D_xpb61XRuWv6eubq5wR9-H6V6gDn5xRm4kP_YZw8FvQYvezNPcdlJwk9KCPStmhCfftC7QkIuwXu5l2JMd2BSb2xp1ohe1w-mz3GMq3mHu2K6pwAU-mUXKjIFFrMURiaBSpk3oA)

**
### Servers

|   |   |
|---|---|
|WebMail|10.200.17.11|
|VPN|10.200.17.12|
|WEB|10.200.17.13|

### **Register

```
**$ ssh e-citizen@10.200.17.250**
```
**

=======================================

Username: kairosdev

Password: URL_5f-Pg1jKyPEp

MailAddr: kairosdev@corp.th3reserve.loc

IP Range: 10.200.17.0/24

=======================================

**

## Project Scope
**

This section details the project scope.

In-Scope

- Security testing of TheReserve's internal and external networks, including all IP ranges accessible through your VPN connection.
    
- OSINTing of TheReserve's corporate website, which is exposed on the external network of TheReserve. Note, this means that all OSINT activities should be limited to the provided network subnet and no external internet OSINTing is required.
    
- Phishing of any of the employees of TheReserve.
    
- Attacking the mailboxes of TheReserve employees on the WebMail host (.11).
    
- Using any attack methods to complete the goal of performing the transaction between the provided accounts.
    

**