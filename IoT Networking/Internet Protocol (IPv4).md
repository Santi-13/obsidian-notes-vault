By: Cisco Networking Academy
#Networking #NetworkingBasics
##### *Networking Basics*
---
### IPv4 Address
The ***IPv4 address*** is a 32-bit logical network address that identifies a particular *host*. It must be properly configured and unique within the LAN, for local communication. It must also be properly configured and unique in the world, for **remote communication**. This is how a host is able to communicate with other devices on the *internet*.

The ***IPv4 address*** is normally assigned by the **Network Interface Card (NIC)** installed in the device, devices with more than one **NIC** naturally have an IP address for each one. Every **packet** sent across the *internet* must have a source and destination ***IPv4 address***.

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
Not all IPv4 addresses are created equally, with the introduction of the ****