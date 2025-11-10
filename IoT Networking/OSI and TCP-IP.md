By: Cisco Networking Academy
#Networking #NetworkingBasics
##### *Networking Basics*
---
##### The OSI Reference Model
|**Layer**|**Name**|**Function**|**PDU (Data Unit)**|
|---|---|---|---|
|**7**|**Application**|Provides the interface between user applications and network services (e.g., protocols like **HTTP, SMTP, FTP**).|Data|
|**6**|**Presentation**|Handles **formatting**, **encryption**, and **compression** of data to ensure readability for the receiving application.|Data|
|**5**|**Session**|**Establishes, manages, and terminates** connections (sessions) between two communicating applications.|Data|
|**4**|**Transport**|Provides **end-to-end data delivery** between application processes. Manages segmentation, flow control, and reliability (**TCP** or **UDP**).|Segments/Datagrams|
|**3**|**Network**|Handles **logical addressing** (**IP**) and **routing** of packets across different networks (inter-networking).|Packets|
|**2**|**Data Link**|Provides **node-to-node data transfer** over the same network segment. Manages physical addressing (**MAC addresses**) and error detection.|Frames|
|**1**|**Physical**|Transmits raw **bits** over the physical medium (cables, radio waves). Defines electrical, mechanical, and timing specifications.|Bits|
##### TCP/IP Protocol
| **Layer** | **Name**           | **Primary Functions**                                                                                                                           | **Equivalent OSI Layers** | **Core Protocols**       |
| --------- | ------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------- | ------------------------ |
| **4**     | **Application**    | Combines the top three OSI layers (Application, Presentation, Session). Provides user-facing services and data handling.                        | 7, 6, 5                   | **HTTP, SMTP, DNS, FTP** |
| **3**     | **Transport**      | Identical to OSI Transport. Handles end-to-end communication and ensures data integrity (reliability) using protocols.                          | 4                         | **TCP, UDP**             |
| **2**     | **Internet**       | Responsible for **logical addressing** and **routing** of data across a network of networks.                                                    | 3                         | **IP, ICMP, ARP**        |
| **1**     | **Network Access** | Combines the OSI Data Link and Physical layers. Deals with the physical transmission medium and local network technology (**Ethernet, Wi-Fi**). | 2, 1                      | **Ethernet, Wi-Fi, MAC** |
##### Comparison
|**Feature**|**OSI Model (7-Layer)**|**TCP/IP Model (4-Layer)**|
|---|---|---|
|**Nature**|A **conceptual/reference model** (theoretical).|An **implementation model** (practical standard).|
|**Basis**|**Protocol-independent**. Developed before specific protocols.|**Protocol-dependent**. The protocols were developed first, and the model was derived from them.|
|**Layers**|**Seven** layers, with a clean separation of functions.|**Four** layers, with some functions combined.|
|**Reliability**|Handled by both the **Data Link** (Layer 2, node-to-node) and **Transport** (Layer 4, end-to-end) layers.|Primarily handled by the **Transport** layer (**TCP**).|
|**Adoption**|Used for **education** and **troubleshooting** today.|The **foundation of the modern internet** and all real-world networking.|