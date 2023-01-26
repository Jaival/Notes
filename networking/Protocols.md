A protocol is the set of rules or algorithms which define the way how two entities can communicate across the network 

Protocols make these networking functions possible.

There exists different protocol defined at each layer of the OSI model. Few of such protocols are TCP, IP, UDP, ARP, DHCP, FTP and so on.

+ **ARP**
	+ ARP stands for **Address Resolution Protocol**.   
	+ It is used to convert an IP address to its corresponding physical address(i.e., MAC Address).   
	+ ARP is used by the Data Link Layer to identify the MAC address of the Receiver’s machine. 
	
+ **RARP**
	+ RARP stands for **Reverse Address Resolution Protocol**.   
	+ As the name suggests, it provides the IP address of the device given a physical address as input. But RARP has become obsolete since the time DHCP has come into the picture.

+ [[DHCP]]
	+ DHCP stands for **Dynamic Host Configuration Protocol.   
	+ It is a client/server protocol that automatically provides an **Internet Protocol (IP)** host with its IP address and other related configuration information such as the subnet mask and default gateway.
	
+ [[TCP]]
	+ TCP(**Transmission Control Protocol**) is used for **organizing data in a way that ensures the secure transmission between the server and client**. 
	+ It guarantees the integrity of data sent over the network, regardless of the amount. For this reason, it is used to transmit data from other higher-level protocols that require all transmitted data to arrive.
	
+ [[UDP]]
	+ UDP **User Datagram Protocol** is commonly used for **applications that are “lossy” (can handle some packet loss), such as streaming audio and video**. It is also used for query-response applications, such as DNS queries.
	
+ **FTP**
	+ FTP (File Transfer Protocol) is a network protocol for transmitting files between computers over Transmission Control Protocol/Internet Protocol (TCP/IP) connections. Within the TCP/IP suite, FTP is considered an application layer protocol.
	
+ IP is a network layer protocol responsible for routing. But it is not the only network layer protocol.

+ **IPsec**
	+ Internet Protocol Security (IPsec) sets up encrypted, authenticated IP connections over a virtual private network (VPN). Technically IPsec is not a protocol, but rather a collection of protocols that includes the Encapsulating Security Protocol (ESP), Authentication Header (AH), and Security Associations (SA).

+ **ICMP** 
	+ The Internet Control Message Protocol (ICMP) reports errors and provides status updates. For example, if a router is unable to deliver a packet, it will send an ICMP message back to the packet's source.

+ **IGMP**
	+ The Internet Group Management Protocol (IGMP) sets up one-to-many network connections. IGMP helps set up multicasting, meaning multiple computers can receive data packets directed at one IP address.


Some of the most important protocols to know are:

+ **HTTP** 
	+ The Hypertext Transfer Protocol (HTTP) is the foundation of the World Wide Web, the Internet that most users interact with. It is used for transferring data between devices. HTTP belongs to the application layer (layer 7), because it puts data into a format that applications (e.g. a browser) can use directly, without further interpretation. The lower layers of the OSI model are handled by a computer's operating system, not applications.

+ **HTTPS** 
	+ The problem with HTTP is that it is not encrypted — any attacker who intercepts an HTTP message can read it. HTTPS (HTTP Secure) corrects this by encrypting HTTP messages.

+ **TLS/SSL** 
	+ Transport Layer Security (TLS) is the protocol HTTPS uses for encryption. TLS used to be called Secure Sockets Layer (SSL).


Network routers use certain protocols to discover the most efficient network paths to other routers. These protocols are not used for transferring user data. Important network routing protocols include:

+ **BGP**
	+ The Border Gateway Protocol (BGP) is an application layer protocol networks use to broadcast which IP addresses they control. This information allows routers to decide which networks data packets should pass through on the way to their destinations.

+ **EIGRP**
	+ The Enhanced Interior Gateway Routing Protocol (EIGRP) identifies distances between routers. EIGRP automatically updates each router's record of the best routes (called a routing table) and broadcasts those updates to other routers within the network.

+ **OSPF**
	+ The Open Shortest Path First (OSPF) protocol calculates the most efficient network routes based on a variety of factors, including distance and bandwidth.

+ **RIP** 
	+ The Routing Information Protocol (RIP) is an older routing protocol that identifies distances between routers. RIP is an application layer protocol.