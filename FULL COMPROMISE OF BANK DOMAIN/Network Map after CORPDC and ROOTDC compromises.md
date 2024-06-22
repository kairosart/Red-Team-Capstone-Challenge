
![[Network Map after CORPDC and ROOTDC compromises-20240612144446331.webp]]



| Source | Target | User            | Password   |
| ------ | ------ | --------------- | ---------- |
| VPN    | CORPDC | CORP\kairos     | K41r@s123  |
| CORPDC | BANKDC | BANK\kairosbank | Capstone1@ |
| BANKDC | JMP    | BANK\kairosroot | Capstone1@ |
| BANKDC | WORK1  | g.watson        | Hacker@123 |
| BANKDC | JMP*   | BANK\kairosbank | Capstone1@ |
