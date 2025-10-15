# 📡 **Protocols**

• `SSH` (Secure Shell) - a protocol used for secure communication between devices. It encrypts the entire session—including commands and responses—and decrypts the data once it reaches the destination.
To connect to a Linux machine remotely I can use :
`ssh username@ip_address` ,then I'll ne asked to type the password

• `ICMP` - Internet Control Message Protocol.It’s a network protocol used for:sending error messages,communicating network diagnostics,reporting things like unreachable hosts, packet loss, or delays.It's part of the IP protocol suite

• `ARP` - allows a device to associate its MAC address with an IP address on the network.Consists of an ARP request that sends a broadcast message to the LAN devices asking what is the MAC of the Ip I'm looking for and an ARP reply in which the device returns its MAC.The mapping is stored in the ARP cache of the requesting device

• `DHCP` - protocol used on Internet Protocol (IP) networks for automatically assigning IP addresses and other communication parameters to devices connected to the network . Steps: DORA. Discover(broadcast message to locate available DHCP servers),Offer( the DHCP server(can be a router) responds with an offer, including an available IP address and other config info.),Request(the requesting device responds with a request for the offered IP address),Accept(The DHCP server sends an acknowledgment, confirming the lease and assigning the IP address to the client)

• `TCP` -Transmission Control Protocol, a protocol designed for reliable, ordered, and error-checked delivery of data between devices.
It is connection-oriented and used in situations where guaranteed delivery matters — such as file sharing, web browsing (HTTP/HTTPS), or email (SMTP/IMAP).

• `UDP` - User Datagram Protocol,a transport layer protocol that is connectionless and does not guarantee delivery, order, or error checking like TCP.
It’s useful in scenarios where speed is more important than reliability, such as live streaming, online gaming, VoIP (e.g., Zoom), or protocols like DHCP and DNS.

• `DNS` - Domain Name System, a protocol dictating how website addresses are translated into IP addresses.

• `HTTP` -  HyperText Transfer Protocol ,the protocol my web browser uses to request and receive web pages from servers

• `IPv4` -  a protocol which uses a numbering system of 2^32 IP addresses (4.29 billion)

• `IPv6` - a protocol which uses a numbering system of up to 2^128 of IP addresses



# 🔧 **Tools**
• `ping` - determines the performance of a connection between devices, for example, if the connection exists or not. Uses ICMP 
##### ✏️examples:
    -ping 8.8.8.8
    -ping google.com




# 🖧 **Topologies**
• `Star topology` - devices are connected via a central networking device such as a switch or hub. This topology is the most commonly found today because of its reliability and scalability (costs a lot compared to other topologies)

• `Bus topology` - This type of connection relies upon a single connection which is known as a backbone cable. cost-efficient to set up but prone to becoming slow and bottlenecked

• `Ring topology` - Devices are connected directly to each other to form a loop through which data is sent until it reaches the destined device, using other devices along the loop to forward the data.fairly easy to troubleshoot ,but isn't an efficient way to send data


# 🍰 **OSI model**
The OSI model taught in tryhackme consists of 7 layers.

• `Physical layer` - connected devices transfer data in binary to one another using electrical signals

• `Data link` - handles communication between devices on the same network. It adds MAC addresses, creates data frames, and performs error detection (and sometimes correction) using techniques like parity bits, CRC, or Hamming codes.

• `Network` - determines the most optimal path through which the data will be sent using protocols like OSPF (Open Shortest Path First) and RIP (Routing Information Protocol).

• `Transport layer` - responsible for the reliable delivery of data between applications on different devices across a network. Follows one of the 2 protocols depending on the circumstances: TCP or UDP.

• `Session layer` - responsible for starting, managing, and ending communication sessions between two devices.(in the 5 layer model this one is absorbed into the application/ transport layers).Each session is a distinct communication channel between two endpoints.Data that's part of one session is kept separate from data in another session.

• `Presentation layer` -responsible for how data is formatted, encoded, encrypted, and translated so that it’s properly understood by both the sender and the receiver.It’s like a translator or formatter between applications.Security features such as data encryption (like HTTPS when visiting a secure site) occur at this layer.
In a 5 layer model ,it's in the application layer.

• `Application layer` -Defines protocols and services that enable software applications to communicate over the network.Protocols used here are for example DNS and HTTP



# 🧠 **Additional notes**
• `ISP` - Internet Service Provider at a monthly fee

• `MAC` -Media access control,a physical network interface, which is a microchip board found on the device's motherboard

• `Switch` - device within a network that are designed to aggregate multiple other networking-capable devices using ethernet.When it receives a packet, instead of repeating that packet to every port like a hub would do, it just sends it to the intended target, thus reducing network traffic. Switches can connect a large number of devices by having ports of 4, 8, 16, 24, 32, 64 etc for devices to plug into.Switches and Routers can be connected to one another

• `Router` - a device that connects networks and passes data between them

• `Network address` - The portion of an IP address used to identify the network segment (consists of the most significant bits)

• `Host address` - The portion of an IP address that  used to identify devices within a network (consists of the least significant bits)
