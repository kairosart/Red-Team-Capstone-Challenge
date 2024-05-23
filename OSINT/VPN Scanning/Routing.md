==If [[ovpn file]] doesn't work fine, use this method.==


> The `ip route` command is used in Linux systems to manage the kernel's IP routing table. It allows you to view, add, modify, or delete routing entries. Here are some common uses of the `ip route` command:

## **Viewing the Routing Table**
To display the current routing table, use:

`ip route show`

## **Adding a Route**
To add a new route to the routing table, use:
`ip route add -host <destination_network> gw <gateway_ip>`
Replace `<destination_network>` with the destination network or IP address, and `<gateway_ip>` with the IP address of the gateway through which packets should be forwarded to reach the destination.

`sudo route add -host 10.200.121.22 gw 10.50.118.43`
## **Deleting a Route**
To delete an existing route from the routing table, use:

`ip route delete <destination_network>`

Replace `<destination_network>` with the destination network or IP address of the route you want to delete.

## netstat
This command displays a list of active network connections along with the local and remote addresses, the protocol used (TCP or UDP), and the current state of each connection.

However, `netstat` has many options and can display different types of information based on the options provided. Some common options include:

- `-a`: Displays all active connections and listening ports.
- `-t`: Displays TCP connections.
- `-u`: Displays UDP connections.
- `-n`: Displays addresses and port numbers in numerical form.
- `-p`: Displays the PID and name of the program to which each socket belongs.
- `-r`: Displays the kernel routing table.

`netstat -r`

Kernel IP routing table
Destination     Gateway         Genmask              Flags     MSS Window  irtt   Iface
default            10.0.2.2           0.0.0.0                   UG        0       0             0      eth0
10.0.2.0           0.0.0.0            255.255.255.0       U          0       0             0      eth0
10.50.118.0      0.0.0.0            255.255.255.0       U          0       0             0      capstone
10.200.121.0    10.50.118.1      255.255.255.0       UG       0       0             0      capstone
1**0.200.121.22  10.50.118.43   255.255.255.255  UGH     0       0             0      capstone**
172.17.0.0        0.0.0.0             255.255.0.0           U          0       0             0      docker0

> In the context of network routing, the "UGH" flags typically appear in the output of the `netstat -rn` command on Unix-like operating systems. Each flag represents a specific attribute of a route entry in the routing table. Here's what "UGH" stands for:

- **U**: Stands for "Up", indicating that the route is active and usable.
- **G**: Stands for "Gateway", indicating that the route uses a gateway to reach the destination.
- **H**: Stands for "Host", indicating that the route is a host-specific route, meaning it is for a specific IP address rather than an entire network.

So, when you see "UGH" flags in the routing table, it means that the route entry is active, uses a gateway, and is for a specific host IP address.
