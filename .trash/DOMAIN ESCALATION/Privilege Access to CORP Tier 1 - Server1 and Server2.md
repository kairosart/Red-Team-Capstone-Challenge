## Connect to 10.200.X.12 via SSH

[[Connect via SSH (10.200.X.12)]]

## Routing network traffic with proxychains

Kali Machine

$ `ssh -D 9050 ubuntu@10.200.X.12 -i rsa`

### Test proxychains

$ `proxychains4 nmap -p- 10.200.113.31 -Pn -v`

## Authenticate the flag on e-citizen

[[Flag Submission Process]]

