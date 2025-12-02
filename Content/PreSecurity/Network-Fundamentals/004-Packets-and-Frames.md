# Packets & Frames

## 🧩 Packets vs. Frames

- **Frame (Layer 2 – Data Link Layer):**
    - Contains no IP information.
    - Exists within a packet — like an envelope inside another.
    - Represents the data once higher-layer encapsulation is stripped.
- **Packet (Layer 3 – Network Layer):**
    - Contains IP addresses and other network routing info.
    - Efficient for transmitting data in small chunks (reduces bottlenecks).
    - Example: an image sent as multiple packets, reassembled on arrival.
- **Encapsulation:** Adding headers as data passes through OSI layers.
    
    **Decapsulation:** Removing headers as data ascends back up the layers.
    

### Common IP Packet Headers

| Header | Purpose |
| --- | --- |
| **Time to Live (TTL)** | Prevents endless circulation; expires undelivered packets. |
| **Checksum** | Verifies data integrity. |
| **Source Address** | Sender’s IP address. |
| **Destination Address** | Recipient’s IP address. |

## 🌐 TCP/IP Model

- 4 Layers: **Application → Transport → Internet → Network Interface**
- Simplified version of the OSI model.
- Uses **encapsulation** (data wrapped with headers) and **decapsulation** (unwrapped).

## 🔁 TCP (Transmission Control Protocol)

- **Connection-based & reliable.**
- Ensures ordered, error-free delivery using **three-way handshake**.
- **Guarantees** delivery but is **slower** due to reliability mechanisms.

### TCP Advantages vs. Disadvantages

| Advantages | Disadvantages |
| --- | --- |
| Guarantees delivery & integrity | Slower due to overhead |
| Synchronizes devices | Requires reliable connection |
| Prevents flooding/out-of-order data | Inefficient on weak connections |

### TCP Headers

| Header | Function |
| --- | --- |
| **Source/Destination Port** | Identify sending and receiving applications. |
| **Source/Destination IP** | Identify sender and receiver devices. |
| **Sequence & Acknowledgement Numbers** | Ensure proper order and tracking of packets. |
| **Checksum** | Ensures data integrity. |
| **Flags** | Control behavior (e.g., SYN, ACK, FIN). |
| **Data** | Actual content being transmitted. |

## 🤝 TCP Three-Way Handshake

1. **SYN** – Client initiates connection (sends sequence number).
2. **SYN/ACK** – Server acknowledges and sends its own sequence number.
3. **ACK** – Client confirms and starts data transmission.
- **Purpose:** Synchronize sequence numbers between devices.
- **FIN:** Cleanly terminates a connection.
- **RST:** Abruptly resets due to error or failure.

### TCP Closing Connection

- **FIN → ACK → FIN → ACK** sequence ensures both sides agree to close.
- Releases system resources to prevent waste.

## ⚡ UDP (User Datagram Protocol)

- **Connectionless and stateless.**
- No handshake, acknowledgement, or error checking.
- **Faster but less reliable** than TCP.
- Used for real-time or loss-tolerant data (e.g., voice/video streaming).

### UDP Advantages vs. Disadvantages

| Advantages | Disadvantages |
| --- | --- |
| Fast, low overhead | No delivery guarantee |
| Flexible rate control | Possible data loss |
| No reserved connection | Poor performance on unstable links |

### UDP Headers

| Header | Purpose |
| --- | --- |
| **TTL** | Packet expiration timer |
| **Source/Destination Address** | Identify devices |
| **Source/Destination Port** | Identify sending and receiving services |
| **Data** | Payload being transmitted |

## 🚢 Ports 101

- **Ports:** Communication endpoints for applications (0–65535).
    
    Analogy: ships docking at specific harbors.
    
- **Common Ports (0–1024):** Standardized for well-known services.

### Common Protocols and Ports

| Protocol | Port | Purpose |
| --- | --- | --- |
| **FTP** | 21 | File transfers |
| **SSH** | 22 | Secure command-line access |
| **HTTP** | 80 | Web traffic |
| **HTTPS** | 443 | Secure web traffic |
| **SMB** | 445 | File & printer sharing |
| **RDP** | 3389 | Remote desktop access |
- Applications can use **non-standard ports** (e.g., HTTP on 8080).
- When using non-standard ports, specify them with a **colon (:)** (e.g., `http://example.com:8080`).