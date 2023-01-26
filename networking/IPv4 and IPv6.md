## IPv4
IPv4 is a connectionless protocol used for packet-switched networks. It operates on a best effort delivery model, in which neither delivery is guaranteed, nor proper sequencing or avoidance of duplicate delivery is assured. Internet Protocol Version 4 (IPv4) is the fourth revision of the Internet Protocol and a widely used protocol in data communication over different kinds of networks. IPv4 is a connectionless protocol used in packet-switched layer networks, such as Ethernet. It provides a logical connection between network devices by providing identification for each device. There are many ways to configure IPv4 with all kinds of devices – including manual and automatic configurations – depending on the network type.

IPv4 is defined and specified in IETF publication RFC 791.  
IPv4 uses 32-bit addresses for Ethernet communication in five classes: A, B, C, D and E. Classes A, B and C have a different bit length for addressing the network host. Class D addresses are reserved for military purposes, while class E addresses are reserved for future use.

IPv4 uses 32-bit (4 byte) addressing, which gives 232 addresses. IPv4 addresses are written in the dot-decimal notation, which comprises of four octets of the address expressed individually in decimal and separated by periods, for instance, 192.168.1.5.


**IPv4 Datagram Header**  
Size of the header is 20 to 60 bytes.

_**VERSION:**_ Version of the IP protocol (4 bits), which is 4 for IPv4

_**HLEN:**_ IP header length (4 bits), which is the number of 32 bit words in the header. The minimum value for this field is 5 and the maximum is 15.

_**Type of service:**_ Low Delay, High Throughput, Reliability (8 bits)

_**Total Length:**_ Length of header + Data (16 bits), which has a minimum value 20 bytes and the maximum is 65,535 bytes.

_**Identification:**_ Unique Packet Id for identifying the group of fragments of a single IP datagram (16 bits)

_**Flags:**_ 3 flags of 1 bit each : reserved bit (must be zero), do not fragment flag, more fragments flag (same order)

_**Fragment Offset:**_ Represents the number of Data Bytes ahead of the particular fragment in the particular Datagram. Specified in terms of number of 8 bytes, which has the maximum value of 65,528 bytes.

_**Time to live:**_ Datagram’s lifetime (8 bits), It prevents the datagram to loop through the network by restricting the number of Hops taken by a Packet before delivering to the Destination.

_**Protocol:**_ Name of the protocol to which the data is to be passed (8 bits)

_**Header Checksum:**_ 16 bits header checksum for checking errors in the datagram header

_**Source IP address:**_ 32 bits IP address of the sender

_**Destination IP address:**_ 32 bits IP address of the receiver

_**Option:**_ Optional information such as source route, record route. Used by the Network administrator to check whether a path is working or not.

Due to the presence of options, the size of the datagram header can be of variable length (20 bytes to 60 bytes).

## IPv6
IP v6 was developed by Internet Engineering Task Force (IETF) to deal with the problem of IP v4 exhaustion. IP v6 is a 128-bits address having an address space of 2^128, which is way bigger than IPv4. In IPv6 we use Colon-Hexa representation. There are 8 groups and each group represents 2 Bytes.

In IPv6 representation, we have three addressing methods :
-   Unicast
-   Multicast
-   Anycast

**1. Unicast Address –**  
Unicast Address identifies a single network interface. A packet sent to a unicast address is delivered to the interface identified by that address. 

**2. Multicast Address –**  
Multicast Address is used by multiple hosts, called as Group, acquires a multicast destination address. These hosts need not be geographically together. If any packet is sent to this multicast address, it will be distributed to all interfaces corresponding to that multicast address. 

**3. Anycast Address –**  
Anycast Address is assigned to a group of interfaces. Any packet sent to an anycast address will be delivered to only one member interface (mostly nearest host possible). 

**Note:** Broadcast is not defined in IPv6. 

**Types of IPv6 address:**   
We have 128 bits in IPv6 address but by looking at the first few bits we can identify what type of address it is.

Prefix	Allocation	Fraction of Address Space
0000 0000	Reserved	1/256
0000 0001	Unassigned (UA)	1/256
0000 001	Reserved for NSAP	1/128
0000 01	UA	1/64
0000 1	UA	1/32
0001	UA	1/16
001	Global Unicast	1/8
010	UA	1/8
011	UA	1/8
100	UA	1/8
101	UA	1/8
110	UA	1/8
1110	UA	1/16
1111 0	UA	1/32
1111 10	UA	1/64
1111 110	UA	1/128
1111 1110 0	UA	1/512
1111 1110 10	Link-Local Unicast Addresses	1/1024
1111 1110 11	Site-Local Unicast Addresses	1/1024
1111 1111	Multicast Address	1/256

Note: In IPv6, all 0’s and all 1’s can be assigned to any host, there is not any restriction like IPv4. 

**Provider-based Unicast address :**   
These are used for global communication.

The First 3 bits identify it as of this type.   
**Registry Id (5-bits):** Registry Id identifies the region to which it belongs. Out of 32 (i.e. 2^5), only 4 registry IDs are being used.

**Provider Id:** Depending on the number of service providers that operate under a region, certain bits will be allocated to the Provider Id field. This field need not be fixed. Let’s say if Provider Id = 10 bits then Subscriber Id will be 56 – 10 = 46 bits.

**Subscriber Id:** After Provider Id is fixed, the remaining part can be used by ISP as a normal IP address.

**Intra Subscriber:** This part can be modified as per the need of the organization that is using the service. 

**Geography based Unicast address :**

**Global routing prefix:** Global routing prefix contains all the details of Latitude and Longitude. As of now, it is not being used. In Geography-based Unicast address routing will be based on location.

**Interface Id:** In IPv6, instead of using Host Id, we use the term Interface Id. 

**Some special addresses:**   
**Unspecified –**

**Loopback –**

**IPv4 Compatible –**

**IPv4 mapped –**

**Local Unicast Addresses :**   
There are two types of Local Unicast addresses defined- _Link-local_ and _Site-Local_. 

**Link-local address:**

A link-local address is used for addressing a single link. It can also be used to communicate with nodes on the same link. The link-local address always begins with 1111111010 (i.e. FE80). The router will not forward any packet with Link-local address. 

**Site local address:**

Site local addresses are equivalent to a private IP address in IPv4. Likely, some address space is reserved, which can only be routed within an organization. The first 10-bits are set to 1111111011, which is why Site local addresses always begin with FEC0. The following 32 bits are Subnet IDs, which can be used to create a subnet within the organization. The node address is used to uniquely identify the link; therefore, we use a 48-bits MAC address here.

## Internet Protocol version 6 (IPv6) Header

**Version (4-bits):** Indicates version of Internet Protocol which contains bit sequence 0110. 

**Traffic Class (8-bits):** The Traffic Class field indicates class or priority of IPv6 packet which is similar to _Service Field_ in IPv4 packet. It helps routers to handle the traffic based on the priority of the packet. If congestion occurs on the router then packets with the least priority will be discarded.   
As of now, only 4-bits are being used (and the remaining bits are under research), in which 0 to 7 are assigned to Congestion controlled traffic and 8 to 15 are assigned to Uncontrolled traffic. 

Priority assignment of Congestion controlled traffic :

Uncontrolled data traffic is mainly used for Audio/Video data. So we give higher priority to Uncontrolled data traffic.   
The source node is allowed to set the priorities but on the way, routers can change it. Therefore, the destination should not expect the same priority which was set by the source node. 

**Flow Label (20-bits):** Flow Label field is used by a source to label the packets belonging to the same flow in order to request special handling by intermediate IPv6 routers, such as non-default quality of service or real-time service. In order to distinguish the flow, an intermediate router can use the source address, a destination address, and flow label of the packets. Between a source and destination, multiple flows may exist because many processes might be running at the same time. Routers or Host that does not support the functionality of flow label field and for default router handling, flow label field is set to 0. While setting up the flow label, the source is also supposed to specify the lifetime of the flow. 

**Payload Length (16-bits):** It is a 16-bit (unsigned integer) field, indicates the total size of the payload which tells routers about the amount of information a particular packet contains in its payload. The payload Length field includes extension headers(if any) and an upper-layer packet. In case the length of the payload is greater than 65,535 bytes (payload up to 65,535 bytes can be indicated with 16-bits), then the payload length field will be set to 0 and the jumbo payload option is used in the Hop-by-Hop options extension header. 

**Next Header (8-bits):** Next Header indicates the type of extension header(if present) immediately following the IPv6 header. Whereas In some cases it indicates the protocols contained within upper-layer packets, such as TCP, UDP. 

**Hop Limit (8-bits):** Hop Limit field is the same as TTL in IPv4 packets. It indicates the maximum number of intermediate nodes IPv6 packet is allowed to travel. Its value gets decremented by one, by each node that forwards the packet and the packet is discarded if the value decrements to 0. This is used to discard the packets that are stuck in an infinite loop because of some routing error.

**Source Address (128-bits):** Source Address is the 128-bit IPv6 address of the original source of the packet. 

**Destination Address (128-bits):** The destination Address field indicates the IPv6 address of the final destination(in most cases). All the intermediate nodes can use this information in order to correctly route the packet. 

**Extension Headers:** In order to rectify the limitations of the _IPv4 Option Field_, Extension Headers are introduced in IP version 6. The extension header mechanism is a very important part of the IPv6 architecture. The next Header field of IPv6 fixed header points to the first Extension Header and this first extension header points to the second extension header and so on.

IPv6 packet may contain zero, one or more extension headers but these should be present in their recommended order:

**Rule:** Hop-by-Hop options header(if present) should always be placed after the IPv6 base header.   

**Conventions :** 

1.  Any extension header can appear at most once except Destination Header because Destination Header is present two times in the above list itself.
2.  If Destination Header is present before Routing Header then it will be examined by all intermediate nodes specified in the routing header.
3.  If Destination Header is present just above the Upper layer then it will be examined only by the Destination node.

Given order in which all extension header should be chained in IPv6 packet and working of each extension header :


## Differences between IPv4 and IPv6

IPv4 and IPv6 are internet protocol version 4 and internet protocol version 6, IP version 6 is the new version of Internet Protocol, which is way better than IP version 4 in terms of complexity and efficiency. 

Difference Between IPv4 and IPv6: 
 |IPv4|IPv6|
|--- |--- |
|IPv4 has a 32-bit address length|IPv6 has a 128-bit address length|
|It Supports Manual and DHCP address configuration|It supports Auto and renumbering address configuration|
|In IPv4 end to end, connection integrity is Unachievable|In IPv6 end to end, connection integrity is Achievable|
|It can generate 4.29×109 address space|Address space of IPv6 is quite large it can produce 3.4×1038 address space|
|The Security feature is dependent on application|IPSEC is an inbuilt security feature in the IPv6 protocol|
|Address representation of IPv4 is in decimal|Address Representation of IPv6 is in hexadecimal|
|Fragmentation performed by Sender and forwarding routers|In IPv6 fragmentation performed only by the sender|
|In IPv4 Packet flow identification is not available|In IPv6 packet flow identification are Available and uses the flow label field in the header|
|In IPv4 checksum field is available|In IPv6 checksum field is not available|
|It has broadcast Message Transmission Scheme|In IPv6 multicast and anycast message transmission scheme is available|
|In IPv4 Encryption and Authentication facility not provided|In IPv6 Encryption and Authentication are provided|
|IPv4 has a header of 20-60 bytes.|IPv6 has header of 40 bytes fixed|
|IPv4 consist of 4 fields which are separated by dot (.)|IPv6 consist of 8 fields, which are separated by colon (:)|
|IPv4’s  IP addresses are divided into five different classes. Class A , Class B, Class C , Class D , Class E.|IPv6 does not have any classes of IP address.|
|IPv4 supports VLSM(Variable Length subnet mask).|IPv6 does not support VLSM.|
|Example of IPv4:  66.94.29.13|Example of IPv6: 2001:0000:3238:DFE1:0063:0000:0000:FEFB|

