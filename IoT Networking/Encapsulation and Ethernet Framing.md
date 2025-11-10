By: Cisco Networking Academy
#Networking #NetworkingBasics
##### *Networking Basics*
---
**Encapsulation** is the core concept of how data is prepared for transmission across a network. It's the sequential process of adding protocol control information (headers and trailers) to data as it moves **down** the layers of the [[OSI and TCP-IP|OSI or TCP/IP model]].

##### Analogy: Sending a Letter
Think of encapsulation as mailing a letter with several envelopes and instructions:

1. **Application Data (Layer 7):** This is the original **Letter** (your data, e.g., "GET" request).

2. **Transport Layer (Layer 4) Header:** The letter is placed in an envelope that specifies the **Port Numbers** (Source/Destination). This ensures the letter reaches the correct _application process_ on the destination computer.

3. **Network Layer (Layer 3) Header:** That envelope is placed inside a larger package that specifies the **IP Addresses** (Source/Destination). This package ensures the letter reaches the correct _computer_ across the internet.

4. **Data Link Layer (Layer 2) Header and Trailer (Ethernet Frame):** The IP package is then placed into a shipping crate, which is the **Ethernet Frame**. This crate has the **MAC Addresses** (Source/Destination) for the _next device_ (e.g., the router). It also includes a **Frame Check Sequence (FCS)** for error detection.

Each piece of control information (the header or trailer) is necessary for the corresponding layer on the receiving machine to process and forward the data correctly.

The reverse process, where the receiving host removes the headers layer by layer until the original application data is revealed, is called **De-encapsulation**.

The **Ethernet Frame** is the final data structure created by the **Data Link Layer (Layer 2)** before the bits are handed over to the Physical Layer (Layer 1) for transmission. It acts as the local transport vehicle for the IP packet (or PDU from Layer 3) across a single link or local network segment.
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