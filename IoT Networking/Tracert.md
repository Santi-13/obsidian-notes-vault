By: Cisco Networking Academy

---
In **Windows**, `tracert` is a command that is used to track the path a *packet* follows when *travelling* to its destination. It works by manipulating a specific field in an IP packet's header called **Time To Live (TTL)**.

**Time To Live (TTL):** Despite its name, this is **not a measure of time**. It is a _hop counter_. An 8-bit field (a number from 0-255) is set by the sending computer. Every single router that receives and forwards the packet **must decrement this TTL value by 1**. 

If a router reduces the **TTL value** to 0, by protocol rules, the router must **discard the packet** and send an **ICMP "Time Exceeded" (Type 11, Code 0)** message back to the original sender.

It works by sending three **ICMP** *(Internet Control Message Protocol)* **Echo Requests** to the final destination, but each time it sends them, the **TTL value** grows, so as to eventually hit all intermediate nodes between the host and the destination. `tracert` receives these 3 replies. It records the source IP of the replies (that's the router's IP!) and the Round-Trip Time (RTT) for each.
 
```
C:\>tracert www.cisco.com

	Tracing route to e2867.dsca.akamaiedge.net [23.205.37.25]
	over a maximum of 30 hops:
	
	  1     1 ms     1 ms    <1 ms  192.168.0.1
	  2     2 ms     1 ms     1 ms  192.168.15.1
	  3     4 ms     4 ms     3 ms  10.70.128.1
	  4     3 ms     3 ms     4 ms  10.180.25.105
	  5     4 ms     4 ms     3 ms  10.180.25.107
	  6     5 ms     4 ms     6 ms  10.180.25.81
	  7     *        9 ms     *     fixed-187-188-50-29.totalplay.net [187.188.50.29]
	  8    96 ms   167 ms   196 ms  fixed-189-203-67-253.totalplay.net [189.203.67.253]
	  9     9 ms     9 ms    11 ms  a23-205-37-25.deploy.static.akamaitechnologies.com [23.205.37.25]
```

The **first column** corresponds to the **TTL value**, **second, third, and fourth columns** are the RTTs of each of the three sent packets (where an * symbolizes a *timed out* packet) and, finally, the **last column** represents the **identifying information** of the router at that hop.

Using tools such as [***WhoIs***](http://whois.domaintools.com/) from ***Domain Tools***, you can search up information of either a *domain name* or a site's *IP address*. From here, you can see information about the site's ownership, managed by **ARIN**.
