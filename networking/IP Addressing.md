## Introduction of Classful IP Addressing
+ IP address is an address having information about how to reach a specific host, especially outside the LAN. An IP address is a 32 bit unique address having an address space of 232.  
+ Generally, there are two notations in which IP address is written, dotted decimal notation and hexadecimal notation.

Dotted Decimal Notation:
128 .    11 .     3 .      31
10000000 00001011 00000011 00011111

Some points to be noted about dotted decimal notation:

1.  The value of any segment (byte) is between 0 and 255 (both included).
2.  There are no zeroes preceding the value in any segment (054 is wrong, 54 is correct).

**Classful Addressing**  
The 32 bit IP address is divided into five sub-classes. These are:

-   Class A = 8
-   Class B = 16
-   Class C = 24
-   Class D = 32
-   Class E = 32

Each of these classes has a valid range of IP addresses. Classes D and E are reserved for multicast and experimental purposes respectively. The order of bits in the first octet determine the classes of IP address.  
IPv4 address is divided into two parts:

-   **Network ID**
-   **Host ID**

The class of IP address is used to determine the bits used for network ID and host ID and the number of total networks and hosts possible in that particular class. Each ISP or network administrator assigns IP address to each device that is connected to its network.

**Note:** IP addresses are globally managed by Internet Assigned Numbers Authority(IANA) and regional Internet registries(RIR).

**Note:** While finding the total number of host IP addresses, 2 IP addresses are not counted and are therefore, decreased from the total count because the first IP address of any network is the network number and whereas the last IP address is reserved for broadcast IP.

**Class A:**

IP address belonging to class A are assigned to the networks that contain a large number of hosts.

-   The network ID is 8 bits long.
-   The host ID is 24 bits long.

The higher order bit of the first octet in class A is always set to 0. The remaining 7 bits in first octet are used to determine network ID. The 24 bits of host ID are used to determine the host in any network. The default subnet mask for class A is 255.x.x.x. Therefore, class A has a total of:

-   2^7-2= 126 network ID(Here 2 address is subtracted because 0.0.0.0 and 127.x.y.z are special address. )
-   2^24 – 2 = 16,777,214 host ID

IP addresses belonging to class A ranges from 1.x.x.x – 126.x.x.x

**Class B:**

IP address belonging to class B are assigned to the networks that ranges from medium-sized to large-sized networks.

-   The network ID is 16 bits long.
-   The host ID is 16 bits long.

The higher order bits of the first octet of IP addresses of class B are always set to 10. The remaining 14 bits are used to determine network ID. The 16 bits of host ID is used to determine the host in any network. The default sub-net mask for class B is 255.255.x.x. Class B has a total of:

-   2^14 = 16384 network address
-   2^16 – 2 = 65534 host address

IP addresses belonging to class B ranges from 128.0.x.x – 191.255.x.x.

**Class C:**

IP address belonging to class C are assigned to small-sized networks.

-   The network ID is 24 bits long.
-   The host ID is 8 bits long.

The higher order bits of the first octet of IP addresses of class C are always set to 110. The remaining 21 bits are used to determine network ID. The 8 bits of host ID is used to determine the host in any network. The default sub-net mask for class C is 255.255.255.x. Class C has a total of:

-   2^21 = 2097152 network address
-   2^8 – 2 = 254 host address

IP addresses belonging to class C ranges from 192.0.0.x – 223.255.255.x.

**Class D:**

IP address belonging to class D are reserved for multi-casting. The higher order bits of the first octet of IP addresses belonging to class D are always set to 1110. The remaining bits are for the address that interested hosts recognize.

Class D does not posses any sub-net mask. IP addresses belonging to class D ranges from 224.0.0.0 – 239.255.255.255.

**Class E:**

IP addresses belonging to class E are reserved for experimental and research purposes. IP addresses of class E ranges from 240.0.0.0 – 255.255.255.254. This class doesn’t have any sub-net mask. The higher order bits of first octet of class E are always set to 1111.

**Rules for assigning Host ID:**

Host ID’s are used to identify a host within a network. The host ID are assigned based on the following rules:

-   Within any network, the host ID must be unique to that network.
-   Host ID in which all bits are set to 0 cannot be assigned because this host ID is used to represent the network ID of the IP address.
-   Host ID in which all bits are set to 1 cannot be assigned because this host ID is reserved as a broadcast address to send packets to all the hosts present on that particular network.

**Rules for assigning Network ID:**

Hosts that are located on the same physical network are identified by the network ID, as all host on the same physical network is assigned the same network ID. The network ID is assigned based on the following rules:

-   The network ID cannot start with 127 because 127 belongs to class A address and is reserved for internal loop-back functions.
-   All bits of network ID set to 1 are reserved for use as an IP broadcast address and therefore, cannot be used.
-   All bits of network ID set to 0 are used to denote a specific host on the local network and are not routed and therefore, aren’t used.

**Problems with Classful Addressing:**

The problem with this classful addressing method is that millions of class A address are wasted, many of the class B address are wasted, whereas, number of addresses available in class C is so small that it cannot cater the needs of organizations. Class D addresses are used for multicast routing and are therefore available as a single block only. Class E addresses are reserved.

Since there are these problems, Classful networking was replaced by Classless Inter-Domain Routing (CIDR) in 1993.

## IP Addressing | Classless Addressing

**Network Address and Mask**

Network address – It identifies a network on internet.  Using this, we can find range of addresses in the network and total possible number of hosts in the network.

Mask – It is a 32-bit binary number that gives the network address in the address block when AND operation is bitwise applied on the mask and any IP address of the block.

The default mask in different classes are :

Class A – 255.0.0.0

Class B – 255.255.0.0

Class C – 255.255.255.0

Example : Given IP address 132.6.17.85 and default class B mask, find the beginning address (network address).

Solution : The default mask is 255.255.0.0, which means that the only the first 2 bytes are preserved and the other 2 bytes are set to 0. Therefore, the network address is 132.6.0.0.

**Subnetting:**  Dividing a large block of addresses into several contiguous sub-blocks and assigning these sub-blocks to different smaller networks is called subnetting. It is a practice that is widely used when classless addressing is done.

**Classless Addressing**

To reduce the wastage of IP addresses in a block, we use sub-netting. What we do is that we use host id bits as net id bits of a classful IP address. We give the IP address and define the number of bits for mask along with it (usually followed by a ‘/’ symbol), like, 192.168.1.1/28. Here, subnet mask is found by putting the given number of bits out of 32 as 1, like, in the given address, we need to put 28 out of 32 bits as 1 and the rest as 0, and so, the subnet mask would be 255.255.255.240.

**Some values calculated in subnetting :**

1. Number of subnets : 2^(Given bits for mask – No. of bits in default mask\[A,B,C])

2. Subnet address : **AND** result of subnet mask and the given IP address

3. Broadcast address : By putting the host bits as 1 and retaining the network bits as in the IP address

4. Number of hosts per subnet : 2^(32 – Given bits for mask) – 2

5. First Host ID : Subnet address + 1 (adding one to the binary representation of the subnet address)

6. Last Host ID : Subnet address + Number of Hosts

**Example :** Given IP Address – 172.16.0.0/25, find the number of subnets and the number of hosts per subnet. Also, for the first subnet block, find the subnet address, first host ID, last host ID and broadcast address.

**Solution** : This is a class B address. So, no. of subnets = 2^(25-16) = 29 = 512.

No. of hosts per subnet = 2(32-25) – 2 = 2^7 – 2 = 128 – 2 = 126

For the first subnet block, we have subnet address = 0.0, first host id = 0.1, last host id = 0.126 and broadcast address = 0.127

## Supernetting in Network Layer

**Supernetting** is the opposite of Subnetting. In subnetting, a single big network is divided into multiple smaller subnetworks. In Supernetting, multiple networks are combined into a bigger network termed as a Supernetwork or Supernet. 

Supernetting is mainly used in Route Summarization, where routes to multiple networks with similar network prefixes are combined into a single routing entry, with the routing entry pointing to a Super network, encompassing all the networks. This in turn significantly reduces the size of routing tables and also the size of routing updates exchanged by routing protocols. 

More specifically,
-   When multiple networks are combined to form a bigger network, it is termed super-netting   
-   Super netting is used in route aggregation to reduce the size of routing tables and routing table updates   

There are some points which should be kept in mind while supernetting:   

1.  All the Networks should be contiguous.   
2.  The block size of every network should be equal and must be in form of 2n.
3.  First Network id should be exactly divisible by whole size of supernet.   

**Example –** Suppose 4 small networks of class C:   

200.1.0.0, 
200.1.1.0,
200.1.2.0,
200.1.3.0

Build a bigger network that has a single Network Id. 

**Explanation –** Before Supernetting routing table will look like as:

|  Network Id | Subnet Mask  | Interface  |
|---|---|---|
| 200.1.0.0  | 255.255.255.0  |  A |
| 200.1.1.0  | 255.255.255.0  | B  |
|  200.1.2.0 | 255.255.255.0  | C |
| 200.1.3.0  | 255.255.255.0  | D  |


First, let’s check whether three conditions are satisfied or not: 

1.  **Contiguous:** 
	You can easily see that all networks are contiguous all having size 256 hosts.   
	Range of first Network from 200.1.0.0 to 200.1.0.255. If you add 1 in last IP address of first network that is 200.1.0.255 + 0.0.0.1, you will get the next network id which is 200.1.1.0. Similarly, check that all network are contiguous. 
    
2.  **Equal size of all network:** 
	As all networks are of class C, so all of them have a size of 256 which is in turn equal to 2^8. 
    
3.  **First IP address exactly divisible by total size:** 
	When a binary number is divided by 2n then last n bits are the remainder. Hence in order to prove that first IP address is exactly divisible by while size of Supernet Network. You can check that if last n v=bits are 0 or not. 
    
    In the given example first IP is 200.1.0.0 and whole size of supernet is 4\*2^8 = 210. If last 10 bits of first IP address are zero then IP will be divisible.
    ![[11001000-1.jpg]]
Last 10 bits of first IP address are zero (highlighted by green color). So 3rd condition is also satisfied. 

1.  Control and reduce network traffic.
2.  Helpful to solve the problem of lacking IP addresses.
3.  Minimizes the routing table 
    -   It cannot cover a different area of the network when combined.
    -   All the networks should be in the same class and all IP should be contiguous.

## IPv4 Classless Subnet equation

**Problem –** How to calculate IP address subnet information (Network, Broadcast, First IP, Last IP)?  
It’s too simple equation to calculate IPv4 Subnet Network ID.

*Used and Tested with Class C Subnets.

First Of All, Keep this Subnet Hosts Map in mind (Number of Hosts per Prefix):
Network Prefix:  Number of IPs
24            :      256 IPs
25            :      128 IPs
26            :      64 IPs
27            :      32 IPs
28            :      16 IPs
29            :      8 IPs
30            :      4 IPs

Network ID: floor(Host Address/Subnet Number of Hosts) * Subnet Number of Hosts
Broadcast ID: (Host ID + (Subnet Number of Hosts-1))
First Host: Network ID + 1
Last Host: Broadcast ID - 1

**Ex1: 192.168.1.65/28:**

65/16 = 4.0625
Network ID: 4\*16 = 64           (192.168.1.64)
Broadcast ID: 64+(16-1) = 79    (192.168.1.79)
First Host ID: 64 + 1 = 65      (192.168.1.65)
Last Host ID: 79 - 1 = 78       (192.168.1.78)

**Ex2: 192.168.20.166/25:**

166/128 = 1.296875
Network ID: 1\*128 = 128         (192.168.20.128)
Broadcast ID: 128+(128-1) = 255 (192.168.20.255)
First Host ID: 128 + 1 = 129    (192.168.20.129)
Last Host ID: 255 - 1 = 254     (192.168.20.254)

**Ex3: 192.168.30.14/29:**

14/8 = 1.75
Network ID: 1\*8 = 8             (192.168.30.8)
Broadcast ID: 8+(8-1) = 15      (192.168.30.15)
First Host ID: 8 + 1 = 9        (192.168.30.9)
Last Host ID: 15 - 1 = 14       (192.168.30.14)

**Ex4: 192.168.20.86/30:**

86/4 = 21.5
Network ID: 21\*4 = 84           (192.168.20.84)
Broadcast ID: 84+(4-1) = 87     (192.168.20.87)
First Host ID: 84 + 1 = 85      (192.168.20.85)
Last Host ID: 87 - 1 = 86       (192.168.20.86)

%%# IPv4 Datagram Fragmentation and Delays%%