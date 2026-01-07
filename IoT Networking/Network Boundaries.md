By: Cisco Networking Academy
#Networking #NetworkingBasics
##### *Networking Basics*
---
***Routers*** typically can have multiple **interfaces** which are connected to different **networks**. This interfaces are called ***default gateways*** and are assigned an IP address and a subnet mask which will allow *hosts* in that same **subnet** to communicate with devices on different networks.

When a wireless router is configured as a DHCP server, it provides its own internal IPv4 address as the default gateway to DHCP clients. It also provides them with their respective IPv4 address and subnet mask, as shown in the figure.

![[Pasted image 20260107135735.png]]

A ***wireless router*** often times acts as a ***DHCP server*** for all *hosts* in the local network; And are normally configured to assign **private** **addresses** to hosts on the network, instead of **public** internet routable **addresses** so that, by default, the internal network is not accessible from the **internet**. The router also tends to take the first available host address on the network by default.

In contrast, many ISPs take on the role of a ***DHCP server*** to provide **IPv4 addresses** to the **internet** side of a router, making the router act as a ***DHCP client*** for the internet interface.

