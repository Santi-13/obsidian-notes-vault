By: Cisco Networking Academy
#Networking #NetworkingBasics
##### *Networking Basics*
---
***Layer 3 NAT*** is basically a way in which we use a *single* (or a few) **public IPv4 addresses** for multiple devices with **private addresses**.  It translates private IP addresses into public IP addresses and vice versa, conserving IPv4 space and adding a layer of security by hiding internal addresses.

**Step-by-step process:**
- **Outbound Request –** A device in a private network sends a packet to an external server. The packet has the device’s private IP as the source.
- **Translation at Router –** The NAT-enabled router replaces the private IP with its public IP and assigns a unique source port number. This mapping is stored in the NAT table.
- **Forward to Internet –** The modified packet is sent to the destination server.
- **Inbound Response –** The server replies to the router’s public IP and port.
- **Reverse Translation –** The router looks up the NAT table, replaces the public IP and port with the original private IP, and forwards the packet to the correct internal device.

