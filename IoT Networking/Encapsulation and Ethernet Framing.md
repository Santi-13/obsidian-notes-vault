By: Cisco Networking Academy
#Networking #NetworkingBasics
##### *Networking Basics*
---


##### Key fields
|**Field**|**Size (Bytes)**|**Role and Function**|
|---|---|---|
|**Preamble**|7|Alternating sequence of 1s and 0s to help the receiving NIC synchronize its clock with the incoming bit stream.|
|**Start Frame Delimiter**|1|Marks the end of the Preamble and the beginning of the actual frame.|
|**Destination MAC Addr.**|6|The **physical address** of the next device that should receive this frame (e.g., another switch, a router, or the final host).|
|**Source MAC Addr.**|6|The **physical address** of the device that is sending the frame.|
|**Length / Type**|2|Indicates either the **length** of the data field, or more commonly, the **type of protocol** contained in the Data field (e.g., $0x0800$ for IPv4, $0x0806$ for ARP).|
|**Data (Payload)**|46–1500|This is the encapsulated data from the upper layers (**the Layer 3 Packet**). The minimum size ensures collision detection works correctly.|
|**Frame Check Sequence (FCS)**|4|A trailer containing a **CRC (Cyclic Redundancy Check)** value, which is a mathematical checksum used for error detection. If the receiver calculates a different value, the frame is considered corrupt and is dropped.|