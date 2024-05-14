Chisel is a command-line tool that creates a TCP tunnel between two endpoints to relay traffic. It is commonly used for bypassing firewalls, accessing restricted networks, or creating secure tunnels for remote access.

![[chisel.png.png]]

1. **Download Chisel**: You can download the Chisel binary from the official GitHub repository: https://github.com/jpillora/chisel/releases
    
2. **Start the Chisel Server**: Run the Chisel server on a machine with public access. For example:
    
    bashCopy code
    
    `./chisel server --port 8080 --reverse`
    
    This command starts the Chisel server on port 8080 in reverse mode, meaning it will accept incoming connections from clients and create a tunnel to them.
    
3. **Connect the Chisel Client**: Run the Chisel client on the machine you want to connect from. For example:
    
    bashCopy code
    
    `./chisel client <server-ip>:8080 R:1234:localhost:1234`
    
    Replace `<server-ip>` with the IP address of the Chisel server. This command creates a tunnel from port 1234 on the server to port 1234 on the client.
    
4. **Access the Tunnel**: With the tunnel established, you can now access services running on the client machine as if they were running locally on the server.
    

Chisel supports various modes of operation, including reverse tunnels (like the example above), forward tunnels, and HTTP tunnels. You can find more information about Chisel and its usage in the official documentation: https://github.com/jpillora/chisel