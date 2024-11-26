# Network+  Notes

## Network Fundaments
- Networks: Encompass a diverse range of connections extending to both wireless and wired connections
- High availability and uptime are important for networks
- Five 9s of availability: 99.999% => 5 mins of downtime per year

### Network Components
- Clients: devices user access the network with
- Servers: provide resources to the network (email, web, etc.)
- Hubs: (Older tech not used in modern networks) Connect other devices over a LAN
    - Have increased errors due to broadcasting nature
    - evolved into bridges and then switches
- Switches: Smarter hubs that provide more security and efficient bandwidth usage
    - forward traffic to specific ports to avoid unnecessary broadcasting
- Wireless Access Points (WAP, AP): Allow wireless devices to connect to a wired network
- Routers: Used to connect different networks together
    - modern routers us the Internet Protocol to route traffic across the network
- Firewalls: Security barrier between internal and external networks
- Load Balancers: Distribute network and / or application traffic over multiple servers.
    - Prevents one severs from overloading and becoming a bottleneck

*Both Firewalls and Load Balancers can be hardware or software based*

- Proxy: Acts as an intermediary between a user's device and the internet
    - Can use Web filtering, Data caching, and shared network connections to improve performance
    - can also be used for "privacy" and security as it hides your real IP address
- Intrusion Detection Systems (IDS): Detect unauthorized access or anomalies and alert admins
- Intrusion Prevention Systems (IPS): Not only detect threats and also take action to prevent intrusion
- Controllers: In software defined networking context, central units that manage flow control to networking devices
- NAS: dedicated file storage that provides data access to a heterogenous group of clients
- Storage Area Networks: High-speed network that provides access to consolidated block-level data storage
- Media: In networking, refers to physical material that transmits data (copper, fiber, wireless signals)
- WAN Link: Used to connect networks over large geographical areas

### Network Resources

#### Client / Server Model
- Uses a dedicated server to provide access to network resources
- Admin and backup is easier (centralized)
- Better scalability
- Costs more due to software and hardware
- Leading model

#### Peer-to-peer Model
- All files located on different machines
- Admin and backup is more difficult
- More difficult to scale
- Lower cost since everyone uses their own devices (no dedicated resources)
- Decentralized management (inefficient for large networks)

### Network Geography

#### Personal Area Network (PAN)
- Smallest type of network (wired or wireless)
- Usually covers around 3m (10 ft) or less
- E.g. Bluetooth, USB

#### Local Area Network (LAN)
- Connects components in a limited distance, up to 100m (300 ft)
- WiFi (IEEE 802.11) or Ethernet (IEEE 802.3)

#### Campus Area Network (CAN)
- A building-centric LAN that spreads across numerous buildings in a certain area
#### Metropolitan Area Network (MAN)
- Connects locations that are scattered across a city
- Police department
#### Wide Area Network (WAN)
- Connect geographical disparate internal networks
- lease lines or VPNs
- The internet
- Don't need to be public (i.e. large company intranet)

*Network Topology is the arrangement of elements that make up a network*

### Wired Network Topology
- Physical Topology: Where devices and components are actually put in the building
- Logical Topology: How the traffic flows through the network not the real world location

#### Topologies:
##### Point-to-point:
- Simplest topology that involves direct connection between two devices

##### Ring:
- Each device is connected to two other devices creating a ring
- Data flows CW or CCW
- Prevents data collisions
- If one node fails, the network goes down (unless there is redundant connections)
- Used in Fiber Distributed Data Interface (FDDI)
    - Operates on a dual ring structure

##### Bus:
- All of the network devices are connected to a single cable called the backbone or bus
- Easy to install
- Performance decreases as devices are added
- Network falls with the backbone
- Not commonly used in modern networks

##### Star:
- Each node is connected to a central connection point (switch)
- Considered robust, but depends on the switch
- Most common layout
- Used in home networks etc.

##### Hub-and-spoke:
- Variation of Star where central hub is connected to multiple spokes
- Used in telecommunication networks or airlines

##### Mesh:
- Features point-to-point connections between every device on the network
- Very robust and redundant
- Two types:
    - Full Mesh: Every node is connected to every other node (very expensive, need n(n-1)/2 connections 6 nodes = 15 connections)
    - Partial Mesh: Some nodes are in full mesh, while others are only connected to one or two devices on the network

### Wireless Network Topology
- Logical topologies also apply to wireless networks
- Infrastructure Mode:
    - Most common 
    - wireless access point as a centralized point (star topology)
- Ad Hoc Mode:
    - Decentralized wireless network connecting peer-to-peer
- Wireless Mesh:
    - An interaction of different types of nodes, devices, and radios to make a mesh
    - Used in disaster zones

### Datacenter Topology
- Any facility that businesses or organizations use to store, process, and disseminate large amounts of data

#### Three-tiered Hierarchy:
- Core
    - Backbone of the network
    - At least two routers
- Distribution / Aggregations
    - Access lists and filters
    - Policy layer
- Edge
    - Connect endpoint devices (user devices, servers, WAPs, etc.)
- This hierarchy gives better performance, scalability, management, and redundancy

#### Collapsed Core
- Core and Distribution layers are emerged into one layer
- Simpler with less scalability

#### Spine and Leaf Architecture
- Alternative type of network that focuses on the communication within the datacenter itself
- Spine: Connects switches in a full mesh topology
- Leaf: Consists of all access switches
- Gives faster speeds and lower latency compared to 3-tiered
- Best with software defined networks
- Spine and leaf can be used with the 3-tiered hierarchy
    - Spine connects to core layer of 3-t

#### Traffic Flows:
- North-South: traffic that enters or leaves a data center
    - North: Leaving datacenter
    - South: Entering datacenter
- East-West: data flow within the datacenter

## OSI (Open Systems Interconnection) Model
- Developed in 1977 by ISO (ISO 7498)
- Made of 7 layers
- Useful for troubleshooting
- Reference Model
    - Works for many devices and networks

### Layers
- Lowest level to highest level: 
    1. [Physical](#layer-1-physical-layer)
    2. [Data Link](#layer-2-data-link)
    3. [Network](#layer-3-network)
    4. [Transport](#layer-4-transport)
    5. [Session](#layer-5-session)
    6. [Presentation](#layer-6-presentation)
    7. [Application](#layer-7-application)

From bottom to top nemonic:
*Please Do Not Throw Sausage Pizza Away*

#### Data
- Data is know by different names in different layers
- layer 5-7: data
- layer 4: segment / datagram
- layer 3: packet
- layer 2: frame
- layer 1: bits

*Do Some People Fear Birthdays*

#### Layer 1: Physical Layer
- Where bits are transmitted across the network
- Includes physical and electrical network characteristics
    - eg. ethernet, fiber or copper, cat5 vs. cat6, radio freq. (WiFi), etc.
- Transition modulation: If it changes during a clock cycle, then 1 is represented, otherwise 0 is represented
    - For copper: 0V off, $\pm$5V on
- Two RJ45 wiring standards: 
    - TIA/EIA-568A
    - TIA/EIA-568B
- Layer 1 devices view networks from a physical topology perspective
- Two ways to transmit:
    - Asynchronous
        - Uses a start and stop bit to indicate when transmissions occur
    - Synchronous
        - Uses a reference cloak to coordinate transmissions
- Two ways to use cable bandwidth
    - Broadband
        - divides cable into multiple channels
    - Baseband
        - use all of the cable, all the time
        - reference clock
        - ethernet network
        - Multiplexing
            - Optimizing use of limited amount of resources
            - Allows multiple users to use baseband at the same time
            - Time Division Multiplexing (TDM)
                - each session takes a turn using time slots to share the connection
            - Statistical Time-Division Multiplexing (StatTDM)
                - Dynamically allocates the time slots as-needed
            - Frequency-Division Multiplexing (FDM)
                - Divides into "channels" based on frequencies and sessions are transmitted over different "channels"
- Devices:
    - Cable (Fiber, Ethernet, Coax)
    - Wireless (WiFi, Bluetooth, NFC)
    - Hubs, APs, Media Converters (act at bit layer)
    - "Whatever comes in must go out. No Logic"

#### Layer 2: Data Link
- Packages data into frames and transmits on the network
- Media Control Address (MAC): Physical addressing system of a device which operates on logical topology
    - Unique 48-bit physical address system assigned to every network interface card (NIC)
    - Written in hex
    - Normally first 24-bits are unique to manufacturer
    - Second half is unique value for each machine
- Logical Link Control (LLC) provides connection services and allows acknowledgement of message receipt
    - Most basic form of flow control
    - Basic error control functions (using checksum)
- Synchronized according to three different schemes:
    - Isochronous: Network devices use common reference clock source and create time slots for transmission
        - Less overhead
    - Synchronous: Network devices agree on clocking method that indicated beginning and end of frame and uses control characters
        - Can only communicate ate frequencies specified by the clock cycles
        - Little unused gap time (drawback)
    - Asynchronous: Allows devices to reference internal clocks and use start and stop bits for synchronization.
        - No real control over when the devices communicate
    - Examples:
        - NICs
        - Bridges
        - Switches

#### Layer 3: Network
- Focused on routing and logical addresses
- Switching (layer 3) = routing
- Logical Addresses
    - 80s and 90s: Apple used Appletalk and Windows used IPX
    - IP killed them off
        - IPv4 and IPv6
- Three main switching "ways":
    - Packet Switching: Data is divided into packets and then forwarded
        - Most common
        - E.g. Envelope to house address
        - Different paths allowed
    - Circuit Switching: Dedicated communication link is established between two devices
        - Same path for entire session
        - E.g. phone call
    - Message Switching: Data is divided into messages which may be stored and then forwarded
        - More like email
- Route Discovery and Selection
    - Static route configured manually or dynamically through routing protocol
        - Dynamical protocols like: RIP, OSPF, EIGRP
- Connection Services: Augment Layer 2 services to improve reliability
    - Flow control
    - Packet reordering
        - Ensures that all data reaches the receiver correctly at the destination
        - Put packets back into correct order after transmission
- [Internet Control Message Protocol (ICMP)](#internet-control-message-protocol-icmp)
    - Sends error messages and operational info to an IP destination
    - Most common tools are ping and traceroute
- Examples:
    - Router
    - Multilayer switches

#### Layer 4: Transport
- Dividing line between upper and lower layers of OSI model
- Deals with segments (TCP) and datagrams (UDP)
- Two protocols
    - [Transmission Control Protocol (TCP)](#tcp)
        - Connection-oriented protocol that is a reliable way to transport segments across a network
        - Called connection-full protocol since it verifies destination received all information
        - Three way handshake:
            - SYN: Synchronization packet
            - SYN-ACK: Sync Acknowledgement packet
            - ACK: Acknowledgement packet
    - [User Diagram Protocol (UDP)](#udp)
        - Connectionless protocol that is an unreliable way to transport segments across a network
        - Increased performance since dropped packets are not retransmitted
        - No sequencing, windowing, or acknowledgements
        - Great for audio and visual data transmission
- Windowing: Allows clients to adjust the amount of data in each segment
    - Open and close the window to maximize throughput
    - Window decreases as the number of retransmissions increases
- Buffering: Occurs when devices allocate memory to store segments if bandwidth is not available
- Examples:
    - WAN accelerators
    - Load balancers
    - Firewalls

#### Layer 5: Session
- The session layer keeps conversations separate to prevent intermingling of data
- Set Up Session:
    - Checking of user credentials and assigning numbers to sessions for identification
    - I.e. starting a conversation with someone
- Maintaining the Session:
    - Where data transfers back and forth across the network
    - Reestablish broken connections
    - Acknowledge receipt
- Tear Down Session:
    - End of a session after transfer is done, of other party disconnects
- Examples:
    - H.323
        - Used to set up, maintain, and tear down voice and video connections
        - Operates over Real-time transport Protocol (RTP)
            - Streaming audio or video in two-way (i.e. phone of video call)
    - NetBIOS
        - Used to share files over a network

#### Layer 6: Presentation
- Formats the data to be exchanged and secures data with encryption
- Data Formatting:
    - Formatted by computer for compatibility between different devices
    - ASCII: Text
    - GIFs
    - JPG
    - PNG
- Encryption:
    - Scrambles data in transit to secure from prying eyes
    - Transport Layer Security (TLS)
        - Used in HTTPS
        - Creates and encrypted tunnel
- Examples:
    - Scripting languages
        - HTML
        - XML
        - PHP
        - JS
    - Standard Text
        - ASCII
        - Unicode
    - Pictures
        - jpg
        - png
    - Movies
        - mp4
        - mov
    - Encryption Algorithms
        - TLS
        - SSL

#### Layer 7: Application
- Provides all application-level services where users communicate with the computer
    - Lower level applications like file or network transfer
- Application services
    - Unites communicating components from multiple network applications
        - File transfer, email (POP3, SMTP, IMAP), remote access, etc.
- Service advertisements
    - Sending out announcements to other devices on the network to state the services devices offer
        - I.e. printer or file server announcing itself
- Examples:
    - Email ([IMAP](#imap), [SMTP](#smtp), [POP3](#pop3))
    - Web browsing ([HTTP](#http), [HTTPS](#https))
    - [Domain Name Service](#dns)
    - File Transfer Protocol ([FTP](#ftp), [SFTP](#sftp), [SMB](#smb))
    - Remote access ([Telnet](#telnet), [SSH](#ssh))


### Encapsulation and Decapsulation
- Encapsulation: Process of putting headers and trailers around some data
- Decapsulation: Process of removing headers and trailers around some data
- Moving down layers => encapsulation
- Moving up layers => decapsulation
- Protocol Data Unit (PDU)
    - Single unit of information transmitted in a network
    - Called L "Layer #" PDU so for layer 7 => L7 PDU
        - Layers 1-4 have "special names"
            1. Bits
            2. Frames
            3. Packets
            4. Segments / Datagrams
- Layer 4 [TCP](#tcp) Header:
    - 20 bytes of data
    - 10 Mandatory fields:
    *(Important marked with *)*
        1. Source Port *
        2. Destination Port *
        3. Sequence Number *
        4. Acknowledgement Number *
        5. TCP Data Offset
        6. Reserve Data (set to 0 as its not really used)
        7. TCP Control Flags *
            - 6 Flags: 
                - SYN: Used to synchronize connection during three-way handshake
                - ACK: Used to acknowledge successful receipt of packets and in 3-way handshake
                - FIN (Finished): Used to tear down virtual connection created in 3-way handshake and SYN flag
                - RST (Reset): Used when client or server receives a packet it wasn't expecting
                - PSH (Push): Used to ensure data has priority and is processed at sending and receiving
                - URG (Urgent): Similar to PSH and identifies incoming data as urgent
        8. Window Size
        9. Checksum
        10. Urgent Pointer
        11. mTCP (Optional) Data
- Layer 4 [UDP](#udp) Header:
    - 8 bytes of data
    - 4 Mandatory fields:
        1. Source Port
        2. Destination Port
        3. Length (Total packet length)
        4. Checksum
- Layer 3 IP Header:
    - Several Fields:
        1. Version
        2. Length
        3. Type of Service (not really used)
        4. Total Length (packet + header)
        5. Identifier
        6. Flags
        7. Fragmented Offset
        8. Time to Live
        9. Protocol
        10. Header Checksum
        11. Source IP Address
        12. Destination IP Address
        13. Options and Padding
- Layer 2 Ethernet Header:
    - 5 Fields:
        1. Destination MAC Address
        2. Source MAC Address
        3. EtherType
            - Used to indicate which protocol is encapsulated in the payload of the frame (IPv4, IPv6)
        4. VLAN Tag (Optional)
- MAC Address: Physical address that is used to identify a network card on a LAN
- Layer 2 Ethernet Payload:
    - Min 42 bytes using VLANs
    - Min 46 bytes with no VLANs
    - By default ethernet uses an MTU (Maximum Transmission Unit) of 1500 bytes
    - For larger MTU, switch need to be reconfigured to allow for jumbo frames

## Ports and Protocols

### Ports
- Port: Virtual entry / exit point for communication used by software to exchange info
- A port is also a logical opening in a computer that represents a service or application
- Ports range from 0 to 65,535 in three common sub-ranges (groups)
    1. Well known ports (0...1023)
    2. Reserved (Registered) ports (1024...49,151)
    - *Both Well known and reserved ports are registered with Internet Assigned Numbers Authority (IANA)*
    3. Ephemeral Ports (Dynamic or Private) Ports (49,152...65,535)
        - Short-lived temp ports which are opened for a small period of time

| Common Port | Service |
| ----------- | ------- |
| 20 | [FTP](#ftp) |
| 21 | [FTP](#ftp) |
| 22 | [SSH](#ssh), [SFTP](#sftp) |
| 23 | [Telnet](#telnet) |
| 25 | [SMTP](#smtp) |
| 53 | [DNS](#dns) |
| 67 | [DHCP](#dhcp) |
| 68 | [DHCP](#dhcp) |
| 69 | [TFTP](#tftp) |
| 80 | [HTTP](#http) |
| 110 | [POP3](#pop3) |
| 123 | [NTP](#ntp) |
| 143 | [IMAP](#imap) |
| 161 | [SNMP](#snmp) |
| 162 | [SNMP](#snmp) |
| 389 | [LDAP](#ldap) |
| 443 | [HTTPs](#https) |
| 445 | [SMB](#smb) |
| 465 | [SMTPs](#smtp) |
| 514 | [SNMP](#snmp) |
| 587 | [SMTPs](#smtp) |
| 636 | [LDAPs](#ldap) |
| 993 | [IMAPs](#imap) |
| 995 | [POP3s](#pop3) |
| 3389 | [RDP](#rdp) |
| 5060 | [SIP](#sip) |
| 5061 | [SIP](#sip) |

### Protocols
- Protocols: Set of rules and conventions for data exchange between network devices

#### TCP
- Ensures reliable transmission of data by breaking down large messages into small packets, sending them, and then rebuilding on the other side
- Uses the three way handshake
- Uses sequence numbers and ack messages to assure data is received correctly
- Employs flow control using [windowing](#layer-4-transport)
- Uses ports to distinguish different services on the same computer (HTTP & HTTPs)
- [*Uses headers to store all this information*](#encapsulation-and-decapsulation)

#### UDP
- Communication protocol used in time-sensitive transmission where some packets can be lost
- Much smaller packets compared to TCP since there is no error correction or connection
- Stateless nature (fire and forget) => faster data transfer but less reliable
- Used in live-broadcast, gaming, streaming, et c.
- Also used in DNS and other request-response services
- Uses ports to distinguish different services on the same computer 
- [*Uses headers to store all this information*](#encapsulation-and-decapsulation)

#### Internet Control Message Protocol (ICMP)
- Not used for sending data between systems
- Used for diagnosing problems
- Operates in the [Network Layer](#layer-3-network) and encapsulated in the IP packets
- Lacks reliability mechanisms of TCP
- Prioritizes speed over security and integrity
- Indicates:
    - When a service or host is unreachable
    - When a packet's time-to-live has expired
    - When a router cannot forward packets due to its buffer being full
- Utilities:
    - ping
    - traceroute
- Header (4bytes):
    - Type
    - Code
    - Checksum
- Data is different depending on the type and code
- ICMP flood attack: overwhelms a target with a large number of ICMP echo request packets (ping packets)
    - Leads to DoS (Denial of Service)
    - These days DDoS (distributed Denial of Service) Attacks are more common
        - Using botnet or network of computers to generate significant amounts of traffic
- Ping of Death
    - Older vulnerability
    - Attack that sends malformed or oversized packets using ICMP
    - Max IP Packet size traditionally: 65,535 bytes

#### HTTP
- HyperText Transfer Protocol
- Foundation of web data communication
- An [application layer](#layer-7-application) protocol 
- Enables plain text communications between clients and servers
- Not secure

#### HTTPs
- HyperText Transfer Protocol Secure
- Same as HTTP but through an SSL or TLS tunnel
- Uses encryption to secure the data being transmitted
- Many webpages have auto-redirect to HTTPs versions

##### HTTP vs. HTTPs
- HTTPs with SSL/TLS provides more security
- Over 95% of web traffic uses port 443 with HTTPs
- HTTPs gets ranked higher in search engines

#### Email Protocols
- SMTP/SMTPs for sending emails
- POP3/POP3s/IMAP/IMAPs for receiving emails

##### SMTP
- Simple Mail Transfer Protocol
- Standard used for sending mail across the internet
- Used for sending emails, not receiving
- Sends in plaintext
- SMTPs is the secure variant which uses SSL/TLS

##### POP3
- Post Office Protocol version 3
- Retrieves emails from a remote server to a local client
- Removed emails from server after download
    - Option to keep emails on server was added
    - Read and delete status is not synced
- Transmits in plaintext
- POP3s (POP3 Secure) is a secure variant using SSL/TLS

##### IMAP
- Internet Message Access Protocol
- Allows users to manage emails directly on the email server
    - Access and sync across devices
- Transmits in plaintext
- IMAPs (IMAP secure) is a secure variant using SSL/TLS

#### File Transfer
- Specialized rules and procedures used for transmission of files across networks
- Act as doorways for data transfer activities

##### FTP
- File Transfer Protocol
- Used for transferring files between a client and a server over a network
- Oldest protocol
- Uses port 20 for data transfer
- Uses port 21 for control commands
    - Upload / Download
- Simple, but not secure (plaintext)

##### SFTP
- Secure File Transfer Protocol / SSH File Transfer Protocol
- Created to address the security concerns of FTP
- SFTP is tunneling FTP through a SSH connection since SSH is encrypted

##### TFTP
- Trivial File Transfer Protocol
- Simpler and more basic version of FTP
- Designed for minimal security file sending

##### SMB
- Server Message Block
- Allows applications to read and write to files and request services from a server
- Used for Windows file sharing
    - Cross platform version (samba)
- Used in a LAN, not a protocol to send across the internet

#### Remote Access
- Manage systems and networks from across the network

##### SSH
- Secure Shell
- Creates a secure encrypted tunnel that can execute text-based commands on a remote server

##### Telnet
- Earliest remote login protocols
- Also text-based
- Allow a user to login to another computer remotely
- Designed for LANs only
- Transfers in plaintext
- NEVER use Telnet unless absolutely necessary

##### RDP
- Remote Desktop Protocol
- *Proprietary protocol from Microsoft*
- Provides users with a GUI to connect to another computer over a network
- Allows for data encryption
- Also allows smart card auth and bandwidth reductions
- Uses TCP

#### Network Services
- Different services that ensure network devices can discover each other, communicate efficiently, and relay important system information to each other

##### DNS
- Domain Name System
- Translates domain names (www.example.com) to IP addresses (123.45.68.71)
- Uses both TCP and UDP
    - Small messages: UDP
    - Large messages: TCP

##### DHCP
- Dynamic Host Configuration Protocol
- Automates the assignment of IP addresses, subnets, masks, gateways, and other networking parameters to a client device
- Server listens for requests on port 67 and client receives responses on port 68
- Uses UDP

##### SQL Services
- Protocols used by database servers to manage queries and control ops from the client app
- No standard port
    - Microsoft SQL: 1433
    - MySQL: 3306

##### SNMP
- Simple Network Management Protocol
- Used for collecting information from and configuring network devices over an IP network
    - E.g. servers, printers, hubs, switches, and routers
- Uses UDP
- Port 161 is used by SNMP managers
- Port 162 is used by SNMP agents

##### Syslog
- System Logging
- Standard for message logging allowing devices to send event messages across IP networks
- Messages are sent to an event message collector known as a Syslog server
- Uses UDP of TCP depending on use case (default is UDP)

#### Others

##### NTP
- Network Time Protocol
- Synchronizes clocks of a computer over a given network
- Uses UDP

##### SIP
- Session Initiation Protocol
- Used for initiating, maintaining, and terminating real-time sessions that involve voice, video, and other communication services
- Used in VoIP
- Uses both TCP and UDP on 5060
- Uses TCP with TLS on 5061 for encrypted transmission

##### LDAP
- Lightweight Directory Access Protocol
- Accesses and maintains distributed directory information services over an IP network
- E.g. finding email and phone number in a company
- Uses both TCP and UDP
- Insecure
- LDAPs (LDAP over SSL) is an encrypted variant
    - Newer versions use TLS for increased security
    - Uses TCP

## Media and Cabling
- Media: Physical material to transmit data between devices
    - Copper
    - Fiber
    - Radio waves

### Copper Media
- IEEE 802.3 Standard: defines the physical layer and data link layer's MAC for wired Ethernet networks
- Most common is twisted pair cables
- Twisted Pair: A type of wiring where two conductors of a single circuit are twisted together
    - Help limit noise
    - Two types: 
        - Unshielded Twisted Pair (UTP)
            - pairs of wires twisted together without additional shielding added to cable
            - lightweight
            - flexible
            - cost-effective
            - generally thinner
        - Shielded Twisted Pair (STP)
            - layer of insulation or shielding added to cable
            - used where there is lots of EMI
            - bulkier, more expensive, harder to install
    - Categories:
        - CAT 5: Oldest used today
            - 100 Mbps
            - 100m maximum
            - 100 MHz
            - 100 Base-T (fast ethernet)
        - CAT 5e: more twists than CAT 5
            - 1000 Mbps
            - 100m maximum
            - 100 MHz
            - 1000 Base-T (Gigabit ethernet)
        - CAT 6
            - 1 Gbps or 10 Gbps
            - 100m max or 55 m max
            - 250 MHz
            - 1000 Base-T or 10G Base-T (10-Gigabit ethernet)
        - CAT 6a
            - 10 Gbps
            - 100m max
            - 500 MHz
            - 10G Base-T
        - CAT 7
            - 10 Gbps
            - 100m max
            - 600 MHz
            - 10G Base-T
        - CAT 8
            - Up to 40 Gbps
            - 30m max
            - 2 GHz
            - For use in crucial high-speed data transfer and short distances
- Coaxial Cables: Single conductor at the core, with an insulating layer and conductive shield covering
    - Originally used in cable TVs
    - RG-6: Used for faster internet speeds when using a cable modem
        - Most cables can do 1 Gbps up to 300m
    - RG-59: Older cable only used in analog video and CCTV
- Direct Attach Copper (DAC) Cable
    - Fixed assembly copper cable used to connect switches to routers or servers
    - Primarily used in data center server racks
    - Supports 100 Gbps at short distances (15m or less for active cables and 7m or less for passive cables)
- Twin Axial Cables
    - Often a component of DAC assembly
    - Considered as another specialized form of cabling
    - Two insulated copper conductors
    - Used in SFP+ and QSFP applications between routers and switches
    - Less impacted by EMI
    - Supports 10 Gbps (100m) to 100 Gbps (7m)
- Plenum vs. Non-Plenum Cables
    - Plenum – Fire-retardant, suitable for air circulation spaces
        - Meets strict fire safety standards of NFPA and NEC
        - Made with PVC or FEP
    - Non-Plenum – Less fire-resistant, used where fire risk is lower
        - Cheaper, but can be toxic when interacting with fire

#### Speeds and Distances

| Cable | Speed | Max Distance |
| ------ | -------- | ---------- |
| CAT 5 | 100 Mbps | 100 m |
| CAT 5e | 1 Gbps | 100 m |
| CAT 6 | 1 Gbps / 10 Gbps | 100 m / 55 m |
| CAT 6a | 10 Gbps | 100 m |
| CAT7 | 10 Gbps | 100m |
| CAT8 | 10-25 or 40 Gbps | 30m |
| RG-6 | 1 Gbps | 300 m |
| Twin-axial | 10 Gbps or more | 10 m |
| DAC | 100 Gbps | 15 m (active cables), 7 meters (passive cables) |

### Copper Network Connections
- RJ-X: Registered Jack
    - Standardized telecom network interface connecting voice and data equipment to a service provided by local exchange or long-distance carrier
    - RJ-11 and RJ-45 use twisted pair cables for voice and data networks
- RG-X: Radio Guide
    - Used with coax cables for high-speed internet, TV, and radio communications
    - RG-6 is common in cable TV
        - Standard for coax cable in residential and commercial settings
        - Better shielding and heavier gauge
    - RG-59
        - Older spec for coax cables
        - Largely replaced with RG-6
- RJ-11: Standard for telephone wiring
    - 6 position, 2 conductor configuration
    - Small in size
    - Not suitable for high-speed connections
- RJ-45: Standard for data networks
    - 8 position, 8 conductor configuration
    - Used in LANs to connect devices
    - Supports high-speed data transmission
    - Used with CAT 5, 5e, 6, 6a, 7, and 8
- F-Type Connector
    - Screw on connector used in cable TV, cable internet, and satellite connections
    - Used with RG-6 and RG-59
- Bayonet Neill-Concelman (BNC) Connector
    - Coaxial connector with a secure bayonet locking mechanism
    - Push and twist connector used in professional video connections
    - Quick, secure, reliable, and stable
    - Used with RG-6 and RG-59
    - *Not the British Naval Connector as it is sometimes called*

### Cable Demonstration

### Fiber Media
- Transmits data using light, not electrical impulses
- Advantages of Fiber Media
    - Light-based transmission is not affected by electromagnetic interference (EMI)
        - Doesn’t require shielding like copper cables
    - Longer transmission distances with minimal signal loss
    - Suitable for local and transcontinental data transmission
    - Higher data transfer speeds
        - Can reach speeds beyond 10 Gbps
- Drawbacks
    - Cost
        - Fiber media is more expensive than copper 
    - Complexity
        - Requires specialized tools and training for installation and repair
- Two types of fiber optic cables:
    - Single-Mode Fiber (SMF)
        - Designed for long-distance communication
        - Small glass core allows light to travel in a single path without dispersion
            - 8.3 to 10 microns in diameter
        - Preferred for backbone installations and connections over vast areas
        - Yellow sheath
        - For long-range transmissions with higher bandwidth
    - Multi-Mode Fiber (MMF)
        - Tailored for shorter distances 
            - 2 kilometers to 1 mile
        - Larger fiber core size allows light to travel in multiple paths 
            - 50 to 100 microns
        - Suitable for connecting servers to switches within buildings or campuses
        - Aqua blue or orange sheath
        - For internal network infrastructures, offering cost-effectiveness and ease of installation

### Fiber Network Connections
- Created by connecting a fiber optic cable to two different devices
- Two different sets of connectors on the cable:
    - For transmission side
    - For receive side
- Types:
    - SC Connector (Subscriber Connector)
        - Square shape with push-pull design
            - "stick and click" connector
        - Widely used in single-mode fibers
        - Common in telecommunications and data networking
        - Used in FTTH (Fiber To The Home) deployments for reliability and ease of use
    - LC Connector (Lucent Connector)
        - Compact size with push-pull mechanism
            - "love connector" since they are often shipped as paired cables for transmit and receive sides
        - Best in high-density applications like data centers
        - High-precision alignment ensures efficient data transmission and minimizes potential data loss
    - ST Connector (Straight Tip Connector)
        - Round shape with twist-lock mechanism
            - "stick and twist" connector
            - Critical in any environment where movement or vibrations might occur
        - Reliable connection commonly used in multi-mode fibers
        - Well-suited for outdoor applications due to its durability
    - MTRJ Connector (Mechanical Transfer-Registered Jack)
        - Small rectangular design with both transmit and receive fibers
            - Similar to RJ-45 but with two fiber "prongs"
        - Suitable for space-constrained applications like office LANs
        - High-density capabilities with an RJ-style latch mechanism
        - Cost-effective solution for dense network environments
    - MPO Connector (Multi-fiber Push On Connector)
        - Multiple fibers in a single connector
        - High-density applications such as data centers and high-speed networks
        - Quick and efficient connections
        - Crucial for rapid scalability
    - Each type of connector can be polished or shaped
- Back reflection occurs when some of transmitted light in a fiber optic cable reflects back, potentially degrading the signal
    - Minimizing back reflection is crucial for maintaining signal integrity and optimizing data transmission
- Polish Types:
    - PC (Physical Contact) Style
        - Slight curvature in the fiber face to lower back reflection over standard straight-cut fiber
        - Least effective reduction in back reflection
        - Best for short-distance or lower-speed data transmissions
    - UPC (Ultra Physical Contact) Style
        - Dome-shaped end-face for better core alignment
        - Lower back reflection than PC style
        - Suitable for general broadband applications
    - APC (Angled Physical Contact) Style
        - 8-degree angled polish to greatly reduce back reflection
        - Lowest amount of back reflection
        - Best for high bandwidth and long-distance applications
            - E.g. undersea cable networks
- *Regular updates on connectors and standards are essential for efficient network design and maintenance*

### Transceiver
- Device capable of both transmitting and receiving data
- Blend of "transmitter" and "receiver"
- Utilizes specific protocols for data transmission and reception
- Main protocols:
    - Ethernet
        - Family of networking technologies for LANs, MANs, and WANs
        - Facilitates communication and data transfer
        - Defines physical standards, electrical standards, and data formats
        - Supports various data rates and media types
    - Fibre Channel (FC)
        - High-speed network technology connecting data storage to servers inside storage area networks
        - Handles large data volumes quickly and reliably
        - Supports optical fiber and copper-based media
        - Key features: high throughput, how latency, and advanced data integrity
- Functions
    - Convert data between different protocols and / or media types in Layer 1 
        - E.g. Ethernet to Fiber Channel
        - E.g. fiber to copper or copper to fiber
    - Enables communication between Ethernet and Fibre Channel networks
- Form factors:
    - SFP (Small Form Factor Pluggable)
        - Compact hot pluggable optical module
        - Can be plugged in or pulled out without turning off the router or switch
        - Up to 4.25 Gbps
    - SFP+
        - Faster version of SFP
        - Up to 16 Gbps
    - QSFP (Quad Small Form Factor Pluggable)
        - Compact hot pluggable optical module
        - Up to 40 Gbps
    - QSFP+
        - Slightly faster version of QSFP
        - Up to 41.2 Gbps 
    - QSFP28
        - Up to 100 Gbps 
    - QSFP56
        - Up to 200 Gbps

## Distribution Systems
- Organized system connecting network backbone to end users via distribution frames
- Design should be hierarchical for logical and functional placement within buildings

### Cable Distribution Systems
- Organized system to connect the network's backbone in the [MDF](#main-distribution-frame) to the [IDF]() and the end user

#### Demarcation Point
- Where the ISP's connection ends and the network infrastructure begins

#### Main Distribution Frame 
- Main starting point for all interior cabling throughout the facility
- I.e. The trunk of a tree
- MDF will contain the backbone switch

#### Cable Tray
- Unit or assembly that forms a rigid structure to secure cables and raceways as they go across the building
- Horizontal runs will be in the drop ceiling or under raised floor
- Vertical runs will use cross-connects

#### Racks
- Hold various devices like routers, switches, patch panels, and servers for efficient storage and easy access
- four common types:
    - 2-post:
        - Two vertical posts used for lighter equipment or for patch panels and cabling
    - 4-post
        - Four posts used for heavier equipment like servers, UPSs, and large network hardware
        - Better stability
    - Wall-mounted
        - Space-saving solution used for smaller hardware where floor space is limited
        - Also used for housing peripheral network components
    - Rack enclosures
        - Full cabinet
        - Fully enclosed with sides and doors offering a protected environment for high-value equipment
        - Can also be locks to provide security

#### Patch Panel
- Device featuring many jacks to connect and route circuits
- Used for monitoring, interconnecting, and testing in a convenient manner
- Cheap
- Two sides
    - Front: 
        - Network Jacks (RJ-45 for copper cabling)
    - Back:
        - 110 Punchdown block
            - Type of punchdown block for voice and data that relies on CAT 5 or newer copper networks
            - Use a punchdown tool to install in the punchdown block
            - Best practice: connect the wall jack to a patch panel

