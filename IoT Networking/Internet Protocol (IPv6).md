By: Cisco Networking Academy
#Networking #NetworkingBasics
##### *Networking Basics*
---
### IPv4 Address
The ***IPv4 address*** is a 32-bit logical network address that identifies a particular *host*. It must be properly configured and unique within the LAN, for local communication. It must also be properly configured and unique in the world, for **remote communication**. This is how a host is able to communicate with other devices on the *internet*.

The ***IPv4 address*** is normally assigned to the **Network Interface Card (NIC)** installed in the device, devices with more than one **NIC** naturally have an IP address for each one. Every **packet** sent across the *internet* must have a source and destination ***IPv4 address***.

The **32-bits** of the address are grouped into four **8-bit bytes** called **octets**:
$$
11010001.10100101.11001000.00000001
$$
For readability purposes, we then convert this to its decimal representation:
$$
209.165.200.1
$$
For communication purposes, we need to define the amount of octets dedicated to the *network* and *host* portions of the address, normally identifiable by a multiple of 8 followed by the IP address. For example:
$$
209.165.200.1/24
$$
Means that the *network* address is composed of the first three octets, and the host is the last one.

### Packet Transmission
##### Unicast
Single one-to-one communication inside a network, a source packet can only originate from a single source *host* and must be directed to a single recipient address.
##### Broadcast
A packet-type that sends a message to all devices on a network by sending a package with a destination IP address of all 1s in the host portion. Broadcasts may be **directed**, that is, specified to broadcast a package to all devices inside the same network segment.
$$
\underbrace{ 172.16.4.0/24 }_{ \text{Source} } \to \underbrace{ 172.16.4.255 }_{ \text{Destination} }
$$
While a **limited** broadcast is sent to $255.255.255.255$. By default, routers do not forward broadcasts.
##### Multicast
This transmission type allows to reduce traffic by allowing a single *source* to send a package to multiple destinations that *subscribed* to a **multicast group**.

A **multicast packet** is a packet with a **multicast IP address** as a destination. **IPv4** has reserved the 224.0.0.0 to 239.255.255.255 addresses as multicast range.

### Types of IPv4 Addresses
Not all IPv4 addresses are created equally, with the introduction of the **World Wide Web (WWW)** in the 1990s, *blocks* of addresses were created to segment the different types of addresses.

A **public IPv4 address** are those which are globally routed between Internet Service Provider (ISP) routers, and are needed to access remote devices through the internet. While **private IPv4 addresses** are used internally by most organizations so assign IPv4 addresses to internal hosts.

| Network Address and Prefix | RFC 1918 Private Address Range |
| -------------------------- | ------------------------------ |
| 10.0.0.0/8                 | 10.0.0.0 - 10.255.255.255      |
| 172.16.0.0/12              | 172.16.0.0 - 172.31.255.255    |
| 192.168.0.0/16             | 192.168.0.0 - 192.168.255.255  |
When transmitting packages to a remote recipient, the package being forwarded to the ISP must contain a public IPv4 address for both the source and destination. Whenever a package is received that has a public destination but also a private source address, the private address must be filtered (or discarded) or transformed to a public address using **Network Address Translation (NAT)**.

### Special Use Addresses
Some addresses cannot be assigned to hosts, or restrict how these hosts can interact with the network.
##### Loopback addresses
Loopback addresses (127.0.0.0 /8 or 127.0.0.1 to 127.255.255.254) are more commonly identified as only 127.0.0.1. These are special addresses used by a host to direct traffic to itself. For example, the **ping** command is commonly used to test connections to other hosts. But you can also use the **ping** command to test if the IP configuration on your own device, as shown in the figure.
##### Link-Local addresses
Link-local addresses (169.254.0.0 /16 or 169.254.0.1 to 169.254.255.254) are more commonly known as the Automatic Private IP Addressing (APIPA) addresses or self-assigned addresses. They are used by a Windows client to self-configure in the event that the client cannot obtain an IP addressing through other methods. Link-local addresses can be used in a peer-to-peer connection but are not commonly used for this purpose.

### IP Addresses Assignment
As **public IPv4 address** *need* to be *unique*, there was a need to create the **Internet Assigned Numbers Authority (IANA)**, in charge of managing and allocating blocks of IP addresses to each of the five existing **Regional Internet Registries (RIR)**, each in charge of allocating IP addresses directly to ISPs.
- **AfriNIC** (African Network Information Centre) - Africa Region
- **APNIC** (Asia Pacific Network Information Centre) - Asia/Pacific Region
- **ARIN** (American Registry for Internet Numbers) - North America Region
- **LACNIC** (Regional Latin-American and Caribbean IP Address Registry) - Latin America and some Caribbean Islands
- **RIPE NCC** (Réseaux IP Européens Network Coordination Centre) - Europe, the Middle East, and Central Asia

### Network Segmentation
In an Ethernet LAN, devices use broadcasts and the Address Resolution Protocol (ARP) to locate other devices. ARP sends Layer 2, that is, internal network, broadcasts to a known IPv4 address on the local network to discover the associated MAC address. Devices on Ethernet LANs also locate other devices using services. A host typically acquires its IPv4 address configuration using the Dynamic Host Configuration Protocol (DHCP) which sends broadcasts on the local network to locate a DHCP server.

A large broadcast domain is a network that connects many hosts. A problem with a large broadcast domain is that these hosts can generate excessive broadcasts and negatively affect the network. In the figure, LAN 1 connects 400 users that could generate an excess amount of broadcast traffic. This results in slow network operations due to the significant amount of traffic it can cause, and slow device operations because a device must accept and process each broadcast packet.

Subnetting reduces overall network traffic and improves network performance. It also enables an administrator to implement security policies such as which subnets are allowed or not allowed to communicate together. Another reason is that it reduces the number of devices affected by abnormal broadcast traffic due to misconfigurations, hardware/software problems, or malicious intent.