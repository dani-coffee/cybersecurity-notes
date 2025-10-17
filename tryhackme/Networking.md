# 📡 **Protocols**

• `SSH` (Secure Shell) - a protocol used for secure communication between devices. It encrypts the entire session—including commands and responses—and decrypts the data once it reaches the destination.
To connect to a Linux machine remotely I can use :
`ssh username@ip_address` ,then I'll ne asked to type the password

• `ICMP` - Internet Control Message Protocol.It’s a network protocol used for:sending error messages,communicating network diagnostics,reporting things like unreachable hosts, packet loss, or delays.It's part of the IP protocol suite

• `ARP` - allows a device to associate its MAC address with an IP address on the network.Consists of an ARP request that sends a broadcast message to the LAN devices asking what is the MAC of the Ip I'm looking for and an ARP reply in which the device returns its MAC.The mapping is stored in the ARP cache of the requesting device

• `DHCP` - protocol used on Internet Protocol (IP) networks for automatically assigning IP addresses and other communication parameters to devices connected to the network . Steps: DORA. Discover(broadcast message to locate available DHCP servers),Offer( the DHCP server(can be a router) responds with an offer, including an available IP address and other config info.),Request(the requesting device responds with a request for the offered IP address),Accept(The DHCP server sends an acknowledgment, confirming the lease and assigning the IP address to the client)

• `TCP` -Transmission Control Protocol, a protocol designed for reliable, ordered, and error-checked delivery of data between devices.
It is connection-oriented and used in situations where guaranteed delivery matters — such as file sharing, web browsing (HTTP/HTTPS), or email (SMTP/IMAP).


• `TCP/IP model` - includes TCP and UDP protocols and consists of 4 layers ( application,transport,internet,network) with information that is added to each layer of the model (encapsulation).The headers added to the packet traversing  the layers (using TCP)are for example: source port ( chose randomly ,value between 0 to 65535) and a destination port ( if it's a website using HTTP protocol,the port is always 80),checksum,source  and destination IP ,sequence number and ACK number (important note,in TCP these numbers are using the number of bytes,not the number of the messages,also ACK number is seqence number+1(in bytes!)).
For UDP the headers are: source and destination port,source and destination IP,checksu,Data and TTL

• `UDP` - User Datagram Protocol,a transport layer protocol that is stateless(doesn't need a constant connection between the 2 devices) and does not guarantee delivery, order, or error checking like TCP.
It’s useful in scenarios where speed is more important than reliability, such as live streaming, online gaming, VoIP (e.g., Zoom), or protocols like DHCP and DNS.

• `DNS` - Domain Name System, a protocol dictating how website addresses are translated into IP addresses. multiple types of DNS record exist,for example: MX record (Specifies where to deliver email for the domain (Mail eXchange)),A record ( resolve to IPv4 addresses), AAAA record( resolve to IPv6 addresses),CNAME record(A canonical name record that points one domain or subdomain to another domain name, for example, TryHackMe's online shop has the subdomain name store.tryhackme.com which returns a CNAME record shops.shopify.com.),TXT record (free text fields where any text-based data can be stored.Can be used for example SPF records to list which servers are allowed to send email on behalf of a domain (helps fight spam and spoofing) or domain verification for services like Google or Microsoft).A DNS request consists of: firstly my local cache is checked to see if i've looked up the address reently,if not a request to my recursive DNS server is made (which is usually provided by  my ISP),it also has a local cache and if the result of the domain name I'm looking for is thre,the answer is sent to my own cache(names like youtube,twitter,google are common to find here).If domain isn't found even in the recursive server, the request passes to the internet's root DNS server (redirect me to the correct Top Level Domain Server).The TLD server holds records for where to find the authoritative server to answer the DNS request. The authoritative server is often also known as the nameserver for the domain. For example, the name server for tryhackme.com is kip.ns.cloudflare.com and uma.ns.cloudflare.com.Then it's the authoratative DNS server ( which holds all the records for a domain)that gives us our answer and then the DNS record is sent back to the Recursive DNS Server, where a local copy will be cached for future requests and then relayed back to the original client that made the request. DNS records all come with a TTL (Time To Live) value.

• `HTTP` -  HyperText Transfer Protocol ,the protocol my web browser uses to request and receive web pages from servers

• `IPv4` -  a protocol which uses a numbering system of 2^32 IP addresses (4.29 billion)

• `IPv6` - a protocol which uses a numbering system of up to 2^128 of IP addresses



# 🔧 **Tools**
• `ping` - determines the performance of a connection between devices, for example, if the connection exists or not. Uses ICMP 
##### ✏️examples:
    -ping 8.8.8.8
    -ping google.com

• `nslookup` - command-line tool used to query DNS records for a domain. 
##### ✏️examples:
    -nslookup -type=CNAME google.com
    -nslookup -type=TXT google.com

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

• `Switch` - Used in the data link layer.It's a device within a network that are designed to aggregate multiple other networking-capable devices using ethernet.When it receives a packet, instead of repeating that packet to every port like a hub would do, it just sends it to the intended target, thus reducing network traffic. Switches can connect a large number of devices by having ports of 4, 8, 16, 24, 32, 64 etc for devices to plug into.They use MAC addresses to forward data within the same local network (LAN).Switches and Routers can be connected to one another.🔸note:a switch maintains a MAC address table (also called a CAM table) that maps each device’s MAC address to the switch physical (or wireless) port it is connected to.

• `Router` - a device that connects networks and passes data between them.Operates in the network layer and uses IPs.I can log in to the router using a web browser (like typing an IP address) or a command-line console.Through this interface, I can change settings and set up rules for how the router behaves.

• `Network address` - The portion of an IP address used to identify the network segment (consists of the most significant bits)

• `Host address` - The portion of an IP address that  used to identify devices within a network (consists of the least significant bits)

• `packet` - A unit of data at the Network Layer.It contains logical addressing information, such as IP addresses (source and destination).It's typically created by protocols like IP.A packet using IP will have a set of headers like the TTL(time to leave,to not let a packet being sent endlessly if it never reaches the distination),or the checksum to check the correctness of the message ,source IP and destination IP

• `frame` - A unit of data at the Data Link Layer .It encapsulates a packet and adds additional information like:MAC addresses (source and destination),Error-checking bits (e.g. CRC), etc.It's used for physical transmission over the medium (like Ethernet or Wi-Fi)

• `A connection between devices` - It consists of messages:SYN ( initial message sent by the client),SYN/ACK (acknowledge) sent by the receiver to acknowledge the synchronisation attempt,ACK - The acknowledgement packet can be used by either the client or server to acknowledge that a series of messages/packets have been successfully received,DATA-data (such as bytes of a file) is sent via the "DATA" message,FIN-close a connection,RST- this packet abruptly ends all communication

• `The-three-way-handshake` - a process that establishes a connection between both devices that wish to communicate.It consists of the messages SYN,SYN/ACK and ACK(in order)

• `End of an TCP connection` - consists of the messages FIN,ACK,FIN,ACK(ir order)

• I might use non-standard ports for development, testing, permissions, or running multiple apps ,i just need to add `:` for example https://example.com:1234 (using 1234 instead of the default port of https which is 443),if i were to use the standard one so i simply write https://example.com 

• `Ip` - internet protocol,belongs to the network layer.Its role is to identify a device on a network.Think of it like a home address — it says where to send the data.Used by: Routers, firewalls, and almost everything on the internet.

• `Port`- Identifies a specific application/service on a device.used in the transport layer.
Think of it like an apartment number in a building — it says which program on the computer should receive the data.Used by: TCP and UDP (transport protocols).

• `firewall` - a device or software within or between a network responsible for determining what traffic is allowed to enter and exit.
 It can be hardware (like a dedicated firewall appliance) or software (like Windows Firewall,snort).
It sits between networks (e.g., between your LAN and the Internet) or sometimes within a single network.
It checks packets using rules based on:IP addresses,Ports and protocols (meaning it operates on network and transport layers ).

• `stateless firewall` -(static) it looks at each packet individually.It doesn’t remember anything about previous packets.It makes decisions only based on static rules, like:Source IP
,Destination IP,Port number,Protocol (TCP/UDP).these firewalls are great when receiving large amounts of traffic from a set of hosts (such as a Distributed Denial-of-Service attack)

• `stateful firewall` - (dynamic) tracks the state of each connection (like TCP handshakes).It keeps a state table to remember active sessions.It understands:Which connections are new, established, or related. Also understands whether a packet belongs to an existing session.

• `VPN` - virtual private network.It's like a secure, private tunnel through the internet.Offers privacy and IP masking,allows networks in different geographical locations to be connected.
Encrypts your internet traffic,hides your IP address and location,lets you access region-locked content (like watching U.S. Netflix from Europe),protects your data on public Wi-Fi.example: DNS are usually unencrypted (even if i use https) but using a vpn encrypts the DNS.

• `PPP` - This technology is used by PPTP (explained below) to allow for authentication and provide encryption of data. VPNs work by using a private key and public certificate (similar to SSH). A private key & certificate must match for you to connect.

This technology is not capable of leaving a network by itself (non-routable).

• `PPTP` - The Point-to-Point Tunneling Protocol is the technology that allows the data from PPP to travel and leave a network. PPTP is very easy to set up and is supported by most devices. It is, however, weakly encrypted in comparison to alternatives.

• `IPsec` - 	Internet Protocol Security encrypts data using the existing Internet Protocol framework.IPSec is difficult to set up in comparison to alternatives; however, if successful, it boasts strong encryption and is also supported on many devices.

• `IANA` - IANA.org is the website for the Internet Assigned Numbers Authority, the organization that manages IP addresses, port numbers, DNS root zones, and other core internet identifiers.

• `Domanin hierarchy` -
 A. `TLD ` (Top-Level Domain) which is divided into 2 types:gTLD (Generic Top Level) and ccTLD (Country Code Top Level Domain).gTLD was meant to tell the user the domain name's purpose; for example, a .com would be for commercial purposes, .org for an organisation, .edu for education and .gov for government. ccTLD was used for geographical purposes, for example, .ca for sites based in Canada, .co.uk for sites based in the United Kingdom.B. `Second-level-domain ` : Taking tryhackme.com as an example, the .com part is the TLD, and tryhackme is the Second Level Domain ,limited to 63 characters + the TLD and can only use a-z 0-9 and hyphens (cannot start or end with hyphens or have consecutive hyphens). 
 C. `Subdomain` -  in the name admin.tryhackme.com the admin part is the subdomain. A subdomain name has the same creation restrictions as a Second-Level Domain, being limited to 63 characters and can only use a-z 0-9 and hyphens (cannot start or end with hyphens or have consecutive hyphens). You can use multiple subdomains split with periods to create longer names, such as jupiter.servers.tryhackme.com. But the length must be kept to 253 characters or less. There is no limit to the number of subdomains you can create for your domain name.
