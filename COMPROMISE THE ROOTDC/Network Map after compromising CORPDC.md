
![[Network Map after compromising CORPDC-20240604150302129.webp]]

Looking at the network topology, we can see that the AD Forest contains two child domains–**CORPDC** and **BANKDC**–and a parent **DC–ROOTDC**. Our shortest path to compromise the entire forest would be to compromise the ROOTDC first. This will give us access to the other machines on the network.