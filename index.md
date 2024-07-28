![[index-20240725150248390.webp]]

**STEPS**

## PROJECT BRIEF
- [[Welcome]]
- [[Trimento]]
- [[SWIFT]]
- [[Project Goal]]
- [[Project scope]]
- [[Project Tools]]
- [[Connect to tryhackme VPN]]
- [[Project Registration]]
- [[Summary]]
- [[Flag Submission Process]]

---


## FIRST THINGS TO DO

- [[Servers]]
- [[Project Registration]]

---

## OSINT
- [[OSINT/Active enumeration of the 3 servers|Active enumeration of the 3 servers]]

### Web Server Scanning

- [[Gobuster]]
- [[OSINT/Web Scanning/Technologies of the website]]
- [[October CMS]]
- [[Website web.thereserve.loc]]

### WebMail scanning

- [[OSINT/WebMail Scanning/Technologies of the website]]
- [[Mail access]]
- [[Brute force SMTP]]

### VPN Scanning

- [[Reverse Shell]]
- [[Connect via SSH (10.200.X.12)]]
- [[Privilege Escalation]]
- [[Scanning other hosts]]
- [[Pivoting]]

## PERIMETER BREACH

- [[Enumerate 10.200.X.21]]
- [[Connect to 10.200.X.21 via RDP]]
- [[Enumerate 10.200.X.22]]
- [[Connect to 10.200.X.22 via RDP]]
- [[Credentials recovery through Kerberosting]]
- [[Enumerate 10.200.X.31 and 32]]
- [[Connect to SERVER1 via RDP]]
- [[Network Map after Server1 and Server2 compromises]]

## FULL COMPROMISE OF CORP DOMAIN

- [[Dumping secrets from the AD machines]]
- [[Dumping secrets from CORPDC]]
- [[Connect CORPDC with evil-winrm]]
- [[RDP to CORPDC]]
- [[Change Administrator's password]]
- [[RDP to CORPDC with the Administrator's credentials]]
- [[Network Map after compromising CORPDC]]

## FULL COMPROMISE OF ROOT DOMAIN

- [[Golden Ticket Attack with mimikatz]]
- [[Maintain persistence]]
- [[Network Map after CORPDC and ROOTDC compromises]]

## FULL COMPROMISE OF BANK DOMAIN

- [[RDP to BANKDC from host CORPDC]]
- [[Create user at BANKDC]]
- [[RDP to JMP]]
- [[RDP to WORK 1]]
- [[Network Map after BANKDC compromise]]

## COMPROMISE OF SWIFT AND PAYMENT TRANSFER


- [[Change g.watson's password and RDP to WRK1]]
- [[Log in into Swift portal as Capturer using provided password]]
- [[SWIFT Web Access]]
- [[Enumerate users CAPTURERS and APPROVERS]]
- [[SWIFT Web Capturer Access]]
- [[SWIFT Web Approver Access]]
- [[SWIFT PAYMENT MADE]]
- [[Final Network Map]]

## APPENDIX

- [[Flag Submission Process]]
- [[Pivoting overview]]
- [[Proxychains]]
- [[Hosts]]
- [[Flags]]
