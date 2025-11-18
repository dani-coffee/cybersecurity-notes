# 📡 **Protocols**

• `SSH` (Secure Shell) – A protocol used for **secure communication** between devices over a network.  
It encrypts everything I send and receive — including commands, passwords, and responses — so no one can spy on the data while it’s traveling.  
The `-X` option enables **X11 forwarding**, which lets me run graphical (GUI) applications from the remote machine and display them on my local screen.
To connect to a Linux machine remotely, I can use:
`ssh username@ip_address`
then type the password for that user.
##### ✏️ **Example:**
       ssh user@192.168.124.148 -X

---

• `ICMP` - Internet Control Message Protocol.It’s a network protocol used for:sending error messages,communicating network diagnostics,reporting things like unreachable hosts, packet loss, or delays.It's part of the IP protocol suite

---

• `ARP` - allows a device to associate its MAC address with an IP address on the network.Consists of an ARP request that sends a broadcast message to the LAN devices asking what is the MAC of the Ip I'm looking for and an ARP reply in which the device returns its MAC.The mapping is stored in the ARP cache of the requesting device.

---

• `DHCP` - protocol used on Internet Protocol (IP) networks for automatically assigning IP addresses and other communication parameters to devices connected to the network . Steps: DORA. Discover(sends packets from the IP address 0.0.0.0 to broadcast IP address to locate available DHCP servers),Offer( the DHCP server(can be a router) responds with an offer, including an available IP address and other config info.),Request(the requesting device responds with a request for the offered IP address),Accept(The DHCP server sends an acknowledgment, confirming the lease and assigning the IP address to the client)

---

• `TCP` -Transmission Control Protocol, a protocol designed for reliable, ordered, and error-checked delivery of data between devices.
It is connection-oriented and used in situations where guaranteed delivery matters — such as file sharing, web browsing (HTTP/HTTPS), or email (SMTP/IMAP).

---

• `TCP/IP model` - includes TCP and UDP protocols and consists of 4 layers ( application,transport,internet,network) with information that is added to each layer of the model (encapsulation).The headers added to the packet traversing  the layers (using TCP)are for example: source port ( chose randomly ,value between 0 to 65535) and a destination port ( if it's a website using HTTP protocol,the port is always 80),checksum,source  and destination IP ,sequence number and ACK number (important note,in TCP these numbers are using the number of bytes,not the number of the messages,also ACK number is seqence number+1(in bytes!)).
For UDP the headers are: source and destination port,source and destination IP,checksu,Data and TTL

---

• `UDP` - User Datagram Protocol,a transport layer protocol that is stateless(doesn't need a constant connection between the 2 devices) and does not guarantee delivery, order, or error checking like TCP.
It’s useful in scenarios where speed is more important than reliability, such as live streaming, online gaming, VoIP (e.g., Zoom), or protocols like DHCP and DNS.

---

• `DNS` - Domain Name System,a protocol that translates human-friendly domain names (like `tryhackme.com`) into IP addresses that computers use to communicate over the internet.
Common DNS Record Types:

| Record Type | Purpose |
|-------------|---------|
| **A**       | Maps a domain to an **IPv4** address |
| **AAAA**    | Maps a domain to an **IPv6** address |
| **MX**      | Specifies the **mail server** responsible for handling email for the domain |
| **CNAME**   | Creates an alias that points one domain/subdomain to another domain name  |
| **TXT**     | Stores **text-based data**; commonly used for SPF records (email security) and domain verification (e.g., Google, Microsoft) |

#####  ✏️ **example**:  
       `store.tryhackme.com`    ➝ could be a CNAME for `shops.shopify.com`.



 How DNS Resolution Works:

When you access a website, DNS follows these steps to resolve the domain name:

| Step | Component                | Purpose                                                                 | Example |
|------|--------------------------|-------------------------------------------------------------------------|---------|
| 1    | **Local Cache**          | Checks your device's DNS cache for a recent answer                     | —       |
| 2    | **Recursive DNS Server** | Queries the DNS server (usually from ISP) and checks its own cache     | —       |
| 3a   | **Root DNS Server**      | Points the request to the correct TLD server based on the domain       | `.com` → TLD server |
| 3b   | **TLD Server**           | Directs the query to the correct authoritative nameserver              | —       |
| 3c   | **Authoritative DNS Server** | Final source of truth. Holds all DNS records for the domain      | `tryhackme.com` → `kip.ns.cloudflare.com`, `uma.ns.cloudflare.com` |
| 4    | **Response Returned**    | The record is cached and returned to your device                       | —       |

🔸note: Each DNS record includes a TTL

---

• `HTTP` -  HyperText Transfer Protocol ,the protocol my web browser uses to request and receive web pages from servers ( transmitting of webpage data, whether that is HTML, Images, Videos, etc).An http request consists of requests like : get ( request for the info),post (request to submit data and create new records),delete(request to delete info), put(requets to usbmit data )

---
• `HTTPs` - HTTPS is the secure version of HTTP. HTTPS data is encrypted so people don't see my actual data.It also makes sure I'm connecting to an authentic web page.

---

• `IPv4` -  a protocol which uses a numbering system of 2^32 IP addresses (4.29 billion)

---

• `IPv6` - a protocol which uses a numbering system of up to 2^128 of IP addresses

---

• `File Transfer Protocol (FTP) ` - FTP (File Transfer Protocol) is used to transfer files between computers over a TCP/IP network, such as the Internet. It enables users to upload, download, and manage files on remote servers.

#####  ✏️ **example**:  
       -ftp 10.10.154.57 ( connect to 10.10.154.47)  then i use the username and password ( existing feature is using anonymous as username and no psasword,but i can user user@example,com for example too-my mail)
       then i can type: type ascii- ASCII mode is used for transferring text files (like .txt, .html, .csv . I can also use type binary for  Non-text files (images, zips, etc.)
       then I do : get file1.txt to retreive this file , it's downloaded to my current working directory in the terminal

--- 

• `File Transfer Protocol Secure (FTPS) ` - FTP with added security using SSL/TLS encryption, like HTTPS for websites. It encrypts login and/or file data.
#####  ✏️ **example**:  
       ftps://ftp.example.com

---
• SFTP (SSH File Transfer Protocol) – a secure way to transfer files between computers over the internet. It’s built on SSH (Secure Shell), which means everything — login credentials, commands, and file contents — is encrypted. That’s why it’s considered more secure and simpler to configure than FTPS.
#####  ✏️ **example**:  
       sftp user@192.168.1.10
#####  then I can use commands like :
        put file.txt   # upload a file
        get report.pdf # download a file

---

• `SMTP (Simple Mail Transfer Protocol)` -  is the standard protocol used to send emails across the internet. It works by transferring messages from a sender’s email client to the recipient’s email server.SMTP can be used via Telnet, but it's not the standard way people send emails today.
#####  ✏️ **example**: 
       telnet smtp.example.com 25
              HELO mydomain.com
              MAIL FROM:<me@mydomain.com>
              RCPT TO:<you@example.com>
              DATA
              Subject: Test
              This is a test email.
              .
              QUIT
🔸note: Telnet only creates plain, unencrypted TCP connections, which Gmail rejects for security reasons. Gmail uses secure SMTP over port 587 (STARTTLS) or port 465 (SSL).It requires authentication (your username and password).It also requires encryption, which Telnet does not support.


---
• `POP3 (Post Office Protocol version 3)` - Retrieves emails from a server to my device. Can also Delete emails from the server after downloading (unless configured otherwise).
#####  ✏️ **example**: 
              telnet mail.example.com 110
              USER yourname@example.com
              PASS yourpassword
              LIST           # shows list of emails
              RETR 1         # retrieves email #1
              DELE 1         # deletes email #1 from server
              QUIT           # ends session
              
🔸note: Telnet only creates plain, unencrypted TCP connections, which Gmail rejects for security reasons. Gmail uses secure SMTP over port 587 (STARTTLS) or port 465 (SSL).It requires authentication (your username and password).It also requires encryption, which Telnet does not support.
#####  ✏️ **example**: 
       openssl s_client -connect pop.gmail.com:995       ➝The secure POP3 port (SSL/TLS)
       USER yourname@gmail.com
       PASS yourapppassword
       LIST
       RETR 1
       QUIT


----

• `IMAP (Internet Message Access Protocol) ` - IMAP lets me access my emails directly from the server, without downloading or deleting them.I can read, organize, and manage my emails from multiple devices — phone, laptop, tablet — and everything stays in sync.
#####  ✏️ **example**: 
       telnet mail.example.com 143
       a001 LOGIN yourname@example.com yourpassword
       a002 SELECT INBOX
       a003 FETCH 1 BODY[TEXT]       # reads the first email
       a004 LOGOUT

---

• `TLS (Transport Layer Security) ` - TLS is a security technology that keeps data private and safe while it’s moving between your device (like your computer or phone) and a server (like Gmail, a website, or an online game).
#####  ✏️ **example**: 
       I type my Gmail password → TLS encrypts it → Gmail decrypts it safely on their end.
       1. I ask to connect securely
       2.Gmail sends a certificat.The server sends a digital certificate containing its public key , identity info and A signature from a trusted Certificate Authority (CA).
       3.my phone/computer verifies the certificate is valid
       4.They perform a key exchange (like Diffie-Hellman-a method that lets two people or devices create a shared secret key — even if they're talking over an insecure network-used in protocols like TLS, VPNs, and SSH to start secure sessions) to agree on a shared session key.
       5.Encrypted communication begins.Now both sides use the shared symmetric session key  to encrypt and decrypt all the actual email traffic (USER, PASS, RETR, etc.). Only someone who knows this session key can read the messages.



---









# 🔧 **Tools**
• `ping` - determines the performance of a connection between devices, for example, if the connection exists or not. Uses ICMP 
##### ✏️examples:
    -ping 8.8.8.8
    -ping google.com
    -ping 192.168.11.1 -c 4       -c stands for counting how many packets to send before stopping

    
---
    

• `nslookup` - command-line tool used to query DNS records for a domain. 
##### ✏️examples:
    -nslookup -type=CNAME google.com
    -nslookup -type=TXT google.com

• `tshark` - TShark is the command-line version of Wireshark which:
1.  Captures packets live from a network interface, or reads from a capture file (.pcap or .pcapng).
2.  Decodes (dissects) network protocols in great detail (Ethernet, IP, ARP, DHCP, HTTP, TLS, etc.).
3.  Can filter, export, and summarize packets just like Wireshark.     
##### ✏️examples:
    -tshark -r arp.pcapng -Nn       ➝ reads the capture file and displays packets using numeric addresses only (no DNS or name lookups).-r arp.pcapng means Read packets from the file arp.pcapng. -N Controls name resolution display style (it’s a Wireshark/TShark internal flag)..The lowercase n here means don’t resolve names — i.e., show raw IP addresses and port numbers, no DNS or hostname lookups.
    -tshark -r dns-query.pcapng -Nn       ➝This tells TShark not to capture live traffic, but instead to read packets from the existing file dns-query.pcapng.


• `Tcpdump` - A classic command-line packet sniffer and analyzer.Captures live packets or reads from a .pcap file.
##### ✏️examples:
    -tcpdump -r arp.pcapng -n -v .-n  Meaning: Don’t resolve hostnames or port names. -v stands for more detailed packet information than the default summary


• `tracert` (Windows)/` traceroute` ( Linux) - Shows the path packets take from your computer to a destination (like a website or IP)
##### ✏️examples:
    -traceroute example.com
    
---    
• `Crowds tool ` - a tool developed to protect user anonymity online. It works by routing my web requests through a group (or “crowd”) of users, so no one — not even the destination server — can tell who originally made the request.
Steps with an example:
1. I make a request (e.g., “Show me cat photos on Google”).
2. My request is sent to a random crowd member.
3. That member either:  Forwards it to another crowd member Or sends it to Google (the destination)
4. The response from Google goes back through the same path, in reverse.
5. Eventually, the response reaches me, but no one along the path knows if I am the original requester or just forwarding.
Not used today anymore .Modern tools that build on or surpass Crowds’ ideas include: Tor,I2P etc..

---






 

# 🖧 **Topologies**
• `Star topology` - devices are connected via a central networking device such as a switch or hub. This topology is the most commonly found today because of its reliability and scalability (costs a lot compared to other topologies)

---
• `Bus topology` - This type of connection relies upon a single connection which is known as a backbone cable. cost-efficient to set up but prone to becoming slow and bottlenecked

---

• `Ring topology` - Devices are connected directly to each other to form a loop through which data is sent until it reaches the destined device, using other devices along the loop to forward the data.fairly easy to troubleshoot ,but isn't an efficient way to send data

 ---

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

---
# 🦈 **Wireshark**
| Function | Description |
|----------|-------------|
| `Statistics → Capture File Properties` / `pcap icon (bottom left` | Provides a structured summary of the capture file. |
| `Go → Go to Packet` | Jump to a specific packet by entering its number. |
| `Edit → Find Packet` | Search for a specific event or value inside the packets. |
| `File → Export Packets` | Export packets from the capture. Works for all protocols. Options: all packets, only displayed (filtered), marked packets, or a specific range. |
| `File → Export Objects` | Export objects (files/data) from certain protocols that support file reconstruction, such as HTTP, SMB, TFTP, DICOM, IMF. TCP and HTTPS do not provide objects unless decrypted. |
| `Analyze → Expert Info` | Analyzes the capture and highlights potential problems, unusual behaviors, or noteworthy events. May contain false positives/negatives. |
| `Right-click → Apply as Filter` | Creates a filter based on the value clicked. Shows only packets that match that value. |
| `Right-click → Conversation Filter` | Filters all packets belonging to a specific conversation between two endpoints (devices). |
| `Right-click → Prepare as Filter` | Creates a filter based on the clicked value like Apply as Filter, but does **not immediately apply** it. |
| `Right-click → Follow → TCP/UDP/HTTP Stream` | Shows all packets in a single connection or stream in order. Reconstructs the data into a continuous flow instead of individual packets. |



# 🌐 **TCPdump**

| Command | Description |
|---------|-------------|
| `sudo tcpdump -i any` | Capture packets on all network interfaces such as Ethernet,Wi-fi. |
| `sudo tcpdump -i eth0` | Capture packets on interface `eth0`. |
| `ip a s` |Shows all network interfaces on my system and their IP addresses |
| `tcpdump -i eth0 -w capture.pcap` |captures packets on interface eth0 and writes them to capture.pcap. |
| `tcpdump -r capture.pcap` |reads the packets from capture.pcap and prints them to the terminal. |
| `tcpdump -i eth0 -c 10` |-c 10 means: capture 10 packets from the specified interface (eth0 in this case) and then exit.|
| `tcpdump -n -i eth0` | Disable hostname resolution. Meaning the output will be something like : 93.184.216.34.http > 192.168.1.10.52345: Flags [S], seq 0, win 65535, length 0--> as we can see : Hostnames not resolved → IP addresses shown,ports still resolved → port 80 shows as http |
 | `tcpdump -nn -i eth0` | Disable both hostname and service name resolution. Meaning the output will be something like : 93.184.216.34.80 > 192.168.1.10.52345: Flags [S], seq 0, win 65535, length 0 --> as we can see : Hostnames not resolved → IP addresses shown,Ports not resolved → port numbers shown (80 instead of http) |
| `tcpdump -v -i eth0` | Provides additional information about each packet beyond the basic summary,-vv → even more verbose, shows deeper details (like TCP options),-vvv → maximum verbosity, can include things like packet timestamps and more protocol headers |
| `tcpdump -r traffic.pcap icmp host 192.168.124.1 -n ` | Reads the file traffic.pcap and prints only ICMP packets to/from IP 192.168.124.1, with numeric IPs/ports |
| `sudo tcpdump -r traffic.pcap arp and host 192.168.124.137` |Reads traffic.pcap and shows only ARP packets that involve the IP 192.168.124.137 — either asking for it or answering from it. |
| `sudo tcpdump -r traffic.pcap port 53 -A` | Reads traffic.pcap and shows all DNS traffic (port 53) with the full packet payload in ASCII (like seeing the actual domain names in queries).|
| `sudo tcpdump -r traffic.pcap 'arp[6:2] == 1' -n'`| an example of command type proto[expr:size]. In this example we read traffic.pcap and show only ARP REQUEST packets — with numeric IPs/MACs (no name resolution).arp[6:2] = Read 2 bytes starting at offset 6 → Operation field. → "Operation = 1" → ARP REQUEST ( if it were 2 then it means reply) |
| `sudo tcpdump -r traffic.pcap 'tcp[tcpflags] == tcp-rst'` then doing wc ,note,could also write it as: `tcp[13:1] & 0x04 != 0` tcp[13:1] meaning "read 1 byte starting at offset 13(flags)" | Counts how many TCP packets in traffic.pcap have the RST (Reset) flag set — i.e., how many connections were abruptly terminated. Other main flags are: tcp-ack ,tcp-syn ,tcp-fin,tcp-push .|
| `sudo tcpdump -r traffic.pcap 'greater 15000' -n'`| Reads traffic.pcap and shows only packets larger than 15,000 bytes — with numeric IPs (no name resolution).The opposite option is using less |
| `sudo tcpdump -q'`|Shows only the most important info|
| `sudo tcpdump -e'`|Shows the MAC addresses|
| `tcpdump -A port 80'`|Shows packet content in text|
| `tcpdump -xx port 53'`|Print all packet bytes (headers + data) in hexadecimal.|
| `tcpdump -X port 53'`|Print all packet bytes (headers + data) in hexadecimal.|



# 🗺️  **Nmap – Network Mapping**
| Command | Description |
|---------|-------------|
| `nmap -sn 192.168.1.0/24` |Means "Ping Scan".Discovers which hosts are alive/up on the network.It does not scan any ports |
| `nmap -sL 192.168.1.0/24` |List Scan. It does not send a single packet to any target.It takes the list of IPs/hosts I gave it and does a reverse DNS lookup on every single one of them.|
| `nmap -sT 192.168.1.1` |nmap performs a complete TCP three-way handshake with every port I'm scanning|
| `nmap -sS 192.168.1.1` |sends only SYN → never completes the handshake (sends RST immediately if SYN-ACK comes back). This is the famous “stealth scan”|
| `nmap -sU 192.168.1.1` |sends empty UDP packets to ports. If I get ICMP “port unreachable” back → port is closed. No reply or other ICMP → probably open or filtered.|
| `sudo nmap -sU -p- 192.168.1.1` |Adding -p- means scan all 65535 ports instead of the default ~1000 common ports. |
| `sudo nmap -sS -p10-1024 192.168.1.1` |Only check ports 10–1024|
| `sudo nmap -sS -F 192.168.1.0/24` |Fast scan – nmap scans only the 100 most common ports|
| `nmap -sS -O 192.168.124.211 ` |-O does operating System detection (and version fingerprinting) Usually 90–98 % correc|
| `nmap -sS -sV 192.168.124.211` |-sV  finds OS + exact software versions|
| `nmap -A 192.168.124.211` |-A  enables -O + -sV ( and other flags like --traceroute)|
| `sudo nmap -sS -Pn 192.168.1.1` | -Pn Tells nmap to skip the host-discovery (ping) phase completely and treat the target as online, even if it doesn’t reply to any pings.Many modern devices — such as home routers , Windows computers with firewalls, or certain IoT gadgets — deliberately ignore ping requests for security. Without -Pn, nmap would wrongly conclude “the host is down” and stop scanning entirely.|
| `sudo nmap -sS -sV --min-parallelism 100 192.168.1.50` |--min-parallelism <num>  Sets the minimum number of probes (nmap's packets) ,here 100, nmap is allowed to have in flight simultaneously.Prevents nmap from slowing down too much on slow or lossy targets.Very useful for speeding up scans of sluggish IoT devices, printers, or rate-limited hosts.Typical values: 100–500 on local networks.|
| `sudo nmap -sS -sV --min-rate 150 192.168.1.23` |Forces nmap to never send slower than this (<number>)  many packets per second, no matter what.|
| `sudo nmap -sS -sV --max-rate 8 203.0.113.50` |nmap will never send faster than this (<number>) many packets per second|
| `sudo nmap -sS -p- -sV -O --host-timeout 10m 192.168.1.100` |Maximum time nmap is allowed to spend on one single host.After this limit, nmap abandons that host and continues with the next.Prevents one slow/broken device from making the entire scan take forever.|
| `sudo nmap -sS -p 12345 --reason 192.168.1.50` |Makes nmap explain why it decided a port is open/closed/filtered.Shows the exact packet that came back (syn-ack, reset, or nothing).Very helpful for learning and for understanding firewalls.|
| `sudo nmap -sS -sV -v 192.168.1.1` |Shows every host as it’s found + open ports in real time. adding -vv adds even more info, can do up to -vvvv ( can also write -v2 instead of -vv for example) |
| `sudo nmap -sS -sV -p 12345 --reason -d 192.168.1.50` |Prints everything nmap is doing internally (packets, timing, decisions).Good to use -d when a scan behaves strangely and I need to see why. -dd or higher (until -d9) = expert/developer territory.|
| `sudo nmap -sS -sV 192.168.1.1 -oN myrouter.txt` |Human-readable text, exactly like on screen (.nmap)|
| `sudo nmap -sS -sV 192.168.1.1 -oX myrouter.xml` |Structured XML file (.xml)|
| `sudo nmap -F 192.168.1.0/24 -oG homescan.gnmap` |Grepable output - written in a way that is super easy to search with normal Linux tools like grep, awk, cut, etc.|
| `sudo nmap -sS -sV -O -oA office_scan_2025` |Creates three files at once: .nmap + .xml + .gnmap|

---

# 🧠 **Additional notes**
• `ISP` - Internet Service Provider at a monthly fee

---

• `MAC` -Media access control,a physical network interface, which is a microchip board found on the device's motherboard

---

• `Switch` - Used in the data link layer.It's a device within a network that are designed to aggregate multiple other networking-capable devices using ethernet.When it receives a packet, instead of repeating that packet to every port like a hub would do, it just sends it to the intended target, thus reducing network traffic. Switches can connect a large number of devices by having ports of 4, 8, 16, 24, 32, 64 etc for devices to plug into.They use MAC addresses to forward data within the same local network (LAN).Switches and Routers can be connected to one another.
🔸note: a switch maintains a MAC address table (also called a CAM table) that maps each device’s MAC address to the switch physical (or wireless) port it is connected to.

---

• `Router` - a device that connects networks and passes data between them.Operates in the network layer and uses IPs.I can log in to the router using a web browser (like typing an IP address) or a command-line console.Through this interface, I can change settings and set up rules for how the router behaves.

---
• `NAT (Network Address Translation) ` - a process that happens on a router (or firewall) that changes IP addresses as packets pass through it.There aren’t enough public IPv4 addresses for every device on Earth.AT solves this by letting many devices share one public IP address when they access the Internet.
🔸note: NAT isn’t a separate physical device — it’s a function (software feature) that runs on my router or firewall.


---

• `Network address` - The portion of an IP address used to identify the network segment (consists of the most significant bits)

---

• `Host address` - The portion of an IP address that  used to identify devices within a network (consists of the least significant bits)

---

• `packet` - A unit of data at the Network Layer.It contains logical addressing information, such as IP addresses (source and destination).It's typically created by protocols like IP.A packet using IP will have a set of headers like the TTL(time to leave,to not let a packet being sent endlessly if it never reaches the distination),or the checksum to check the correctness of the message ,source IP and destination IP

---

• `frame` - A unit of data at the Data Link Layer .It encapsulates a packet and adds additional information like:MAC addresses (source and destination),Error-checking bits (e.g. CRC), etc.It's used for physical transmission over the medium (like Ethernet or Wi-Fi)

---

• `A connection between devices` - It consists of messages:SYN ( initial message sent by the client),SYN/ACK (acknowledge) sent by the receiver to acknowledge the synchronisation attempt,ACK - The acknowledgement packet can be used by either the client or server to acknowledge that a series of messages/packets have been successfully received,DATA-data (such as bytes of a file) is sent via the "DATA" message,FIN-close a connection,RST- this packet abruptly ends all communication

---

• `The-three-way-handshake` - a process that establishes a connection between both devices that wish to communicate.It consists of the messages SYN,SYN/ACK and ACK(in order)

---

• `End of an TCP connection` - consists of the messages FIN,ACK,FIN,ACK(in order)

---

• I might use non-standard ports for development, testing, permissions, or running multiple apps ,i just need to add `:` for example https://example.com:1234 (using 1234 instead of the default port of https which is 443),if i were to use the standard one so i simply write https://example.com 

---

• `Ip` - internet protocol,belongs to the network layer.Its role is to identify a device on a network.Think of it like a home address — it says where to send the data.Used by: Routers, firewalls, and almost everything on the internet.

---

• `Port`- Identifies a specific application/service on a device.used in the transport layer.
Think of it like an apartment number in a building — it says which program on the computer should receive the data.Used by: TCP and UDP (transport protocols).

---

• `firewall` - a device or software within or between a network responsible for determining what traffic is allowed to enter and exit.
 It can be hardware (like a dedicated firewall appliance) or software (like Windows Firewall,snort).
It sits between networks (e.g., between your LAN and the Internet) or sometimes within a single network.
It checks packets using rules based on:IP addresses,Ports and protocols (meaning it operates on network and transport layers ).



• `stateless firewall` -(static) it looks at each packet individually.It doesn’t remember anything about previous packets.It makes decisions only based on static rules, like:Source IP
,Destination IP,Port number,Protocol (TCP/UDP).these firewalls are great when receiving large amounts of traffic from a set of hosts (such as a Distributed Denial-of-Service attack)



• `stateful firewall` - (dynamic) tracks the state of each connection (like TCP handshakes).It keeps a state table to remember active sessions.It understands:Which connections are new, established, or related. Also understands whether a packet belongs to an existing session.

---

• `VPN` - virtual private network.It's like a secure, private tunnel through the internet.Offers privacy and IP masking,allows networks in different geographical locations to be connected.
Encrypts your internet traffic,hides your IP address and location,lets you access region-locked content (like watching U.S. Netflix from Europe),protects your data on public Wi-Fi.example: DNS are usually unencrypted (even if i use https) but using a vpn encrypts the DNS.

---

• `PPP` - This technology is used by PPTP (explained below) to allow for authentication and provide encryption of data. VPNs work by using a private key and public certificate (similar to SSH). A private key & certificate must match for you to connect.This technology is not capable of leaving a network by itself (non-routable).

---

• `PPTP` - The Point-to-Point Tunneling Protocol is the technology that allows the data from PPP to travel and leave a network. PPTP is very easy to set up and is supported by most devices. It is, however, weakly encrypted in comparison to alternatives.

---

• `IPsec` - 	Internet Protocol Security encrypts data using the existing Internet Protocol framework.IPSec is difficult to set up in comparison to alternatives; however, if successful, it boasts strong encryption and is also supported on many devices.

---

• `IANA` - IANA.org is the website for the Internet Assigned Numbers Authority, the organization that manages IP addresses, port numbers, DNS root zones, and other core internet identifiers.

---

 • `Domanin hierarchy` -
 1. Top-Level Domain (TLD)-TLDs are the highest level in the domain name system. They come in two main types:
  
| Type        | Description                     | Examples       |
|-------------|----------------------------------|----------------|
| **gTLD**    | Generic domains by purpose       | `.com`, `.org`, `.edu`, `.gov` |
| **ccTLD**   | Country-specific domains         | `.ca` (Canada), `.co.uk` (UK) |


 3. Second-Level Domain (SLD) - This is the part that appears just before the TLD.  
    Example: In `tryhackme.com`, `tryhackme` is the SLD.

    Rules for SLDs:
    - Can include: `a–z`, `0–9`, and hyphens (`-`)
    - Cannot:
    - 1.Start or end with a hyphen
    - 2.Have two hyphens in a row
    - 3.Maximum length: **63 characters** (excluding the TLD)


 4. Subdomain - A subdomain appears before the SLD.  
    Example: In `admin.tryhackme.com`, `admin` is the subdomain.

    *subdomain rules:
    - Same character rules as SLD
    - You can chain multiple subdomains (e.g., `jupiter.servers.tryhackme.com`)
    - Entire domain (including subdomains) must be **253 characters or less**
    - No limit to how many subdomains can be created


---

 • `URL` -
A URL (Uniform Resource Locator) tells the browser how and where to access a resource on the internet. It can include the following parts:

| Part         | Description |
|--------------|-------------|
| **Scheme**   | Protocol used: `http`, `https` |
| **User Info**| Optional login: `user:pass@` |
| **Host**     | Domain name or IP address |
| **Port**     | Port number (e.g., `80`, `443`) |
| **Path**     | Location of a resource or file |
| **Query**    | Extra parameters (`?id=1`) |
| **Fragment** | Link to a section in the page (`#section1`) |

🔸note: not every URL includes all of these parts — only what's necessary for the request.

---

• `HTTP request` - 
##### ✏️example
    GET / HTTP/1.1    ➝request the home page with / and telling the web server we are using HTTP protocol version 1.1
    Host: google.com    ➝tell the web server we want the website google.com
    User-Agent: Mozilla/5.0 Firefox/87.0    ➝ we are using the Firefox version 87 Browser
    Referer: https://google.com/    ➝ the web page that referred us to this one is https://google.com 
                                    ➝empty line(a request always ends with one)
                                    
•http requests contain additional headers like Host(Specifies the domain name of the server the client wants to connect to),User-Agent(Identifies the client software making the request-usually the browser or tool),Content-Length,Accept-Encoding(Tells the server what compression methods the client supports (like gzip)),Cookie.

---


• `HTTP response` - 
##### ✏️example
     HTTP/1.1 200 OK    ➝which protocol i sused + status ( 200 stands for ok)    
    Server: nginx/1.15.8    ➝which server and version is used
    Date: Sat, 19 Apr 2021 12:34:03 GMT    ➝current date, time and timezone of the web server.
    Content-Type: text/html    ➝what kind of information is sent(HTML,TXT,jpg etc)
    Content-Length: 98    ➝how long is the data ( header that serves us to know that the data isn't incomplete)
                          ➝blank space  
    
    <html>
    <head>
        <title>Google</title>
    </head>
    <body>
        Welcome To Google.com
    </body>
    </html>    ➝    these 8 lines represent the information that was requested          

•http response contain additional headers like: set-Cookie,Content-Type,Content-Encoding

---

• `HTTP Status Codes ` :
 
| Code Range | Category       | Description                                     | Examples                                                  |
|------------|----------------|-------------------------------------------------|-----------------------------------------------------------|
| 200–299    | Success         | The request was successfully received and processed | 200 OK, 201 Created                                       |
| 300–399    | Redirection     | Further action is needed to complete the request | 301 Moved Permanently, 302 Found (Temporary Redirect)     |
| 400–499    | Client Error    | The client made a bad request                   | 400 Bad Request, 401 Unauthorized, 403 Forbidden, 404 Not Found, 405 Method Not Allowed |
| 500–599    | Server Error    | The server failed to fulfill a valid request    | 500 Internal Server Error, 503 Service Unavailable        |

---

• `Cookies` - Cookies are small pieces of data that a server sends to your browser, which the browser stores and sends back to the server with future requests to the same domain(used for session Management,Personalization , Tracking and  Analytics)

---

•` TTL` (Time To Live) - a value that defines how long it should be cached before it expires and must be refreshed.

| TTL Value | Effect                                      |
|-----------|---------------------------------------------|
| Low TTL   | More frequent updates, less caching         |
| High TTL  | Faster lookups, but may serve outdated data |



•  three ranges of private IP addresses (according to RFC 1918) :

    10.0.0.0 - 10.255.255.255 (10/8)
    172.16.0.0 - 172.31.255.255 (172.16/12)
    192.168.0.0 - 192.168.255.255 (192.168/16)

• Some routing algorithms-
1. `RIP (Routing Information Protocol)` - Routers talk to each other using RIP messages.Each router shares its routing table (list of networks it knows about) with its neighbors every 30 seconds.RIP uses hop count as the only “score” to decide the best path
2. `EIGRP ( Enhanced Interior Gateway Routing Protocol)` - Cisco proprietary routing protocol in which Routers exchange routing info using EIGRP messages only when things change.EIGRP considers bandwidth(maximum amount of data that can be sent over a network connection in a certain amount of time) and delay


---
•` VPN (Virtual Private Network)` - creates a secure, encrypted tunnel between my device and the internet. It hides my real IP address and location, making it harder for websites, hackers, or governments to track me.
Even with a VPN, leaks can happen, exposing my real identity or location. Common types include:
1. IP leaks: my real IP address is exposed.
2. DNS leaks: my device uses your ISP’s DNS instead of the VPN’s, revealing what sites I visit.
3. WebRTC leaks: browser features can expose my IP during video calls or peer-to-peer connections.
4. IPv6 leaks: some VPNs don’t handle IPv6 traffic properly, leaking data.


---



