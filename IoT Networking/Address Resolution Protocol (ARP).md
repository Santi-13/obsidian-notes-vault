By: Cisco Networking Academy
#Networking #NetworkingBasics
##### *Networking Basics*
---
The ***Address Resolution Protocol*** solves a very specific issue when sending packages from one network to another: How can I know the destination's **MAC address** when I only know its **IP address**?

Well, for that we need to remember the differences between this addresses:
- **Physical address (the MAC address)** – Used for NIC-to-NIC communications on the same Ethernet network.
- **Logical address (the IP address)** – Used to send the packet from the source device to the destination device. The destination IP address may be on the same IP network as the source, or it may be on a remote network.

Basically, when on the same network (Layer 2), the source uses the **MAC address**, although the package does include the destination IP as well.

![[Pasted image 20260107142636.png]]

When the destination's **IP address** is on a different network, the destination **MAC address** becomes that one of the host's **default gateway**.

![[Pasted image 20260107142756.png]]

From here on out, the **router** utilizes the destination **IP address** to determine the best path to the device. It de-encapsulates the Layer 2 information and encapsulates a new frame, until it reaches the end device.

![[Pasted image 20260107142936.png]]

![[Pasted image 20260107142946.png]]

How are the IP addresses of the IP packets in a data flow associated with the MAC addresses on each link along the path to the destination? For IPv4 packets, this is done through a process called **Address Resolution Protocol (ARP**). For IPv6 packets, the process is **ICMPv6 Neighbor Discovery (ND)**.