
Pivoting is a technique used in cybersecurity to move from one compromised system to another within the same network, typically to gain deeper access to sensitive information or critical systems. This technique is commonly used during penetration testing and by attackers to exploit network vulnerabilities.

### Types of Pivoting

- Network Pivoting:

	- Port Forwarding: This involves redirecting network traffic from one port to another, allowing access to services running on a different machine.

	- VPN Pivoting: Establishing a virtual private network (VPN) connection to route all traffic through the compromised host, making it appear as if the traffic originates from that host.


- Proxy Pivoting:

	- SOCKS Proxy: Setting up a SOCKS proxy on the compromised machine to tunnel traffic through it.

	- SSH Tunneling: Using Secure Shell (SSH) to create encrypted tunnels, allowing secure access to internal network services.

### Tools Used for Pivoting

1. Metasploit: A penetration testing framework that includes tools for various types of pivoting, such as Meterpreter, which allows for creating tunnels and routing traffic through compromised hosts.
    
2. ProxyChains: A tool to chain multiple proxy servers, which can be used in conjunction with other tools to route traffic through a compromised machine.
    

SSH: SSH can be used to create tunnels and forward ports, enabling access to services on internal networks.