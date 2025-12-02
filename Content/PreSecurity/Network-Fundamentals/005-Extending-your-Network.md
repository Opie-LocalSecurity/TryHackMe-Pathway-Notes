# Extending your Network

## Port Forwarding

- **Purpose:** Makes internal network services (e.g., web servers) accessible from the Internet.
- **How it works:**
    - Configured on a router to forward incoming traffic from a specific public port to a private IP and port on the local network.
    - Example: Public IP `82.62.51.70` forwards traffic on port 80 to internal server `192.168.1.10:80`.
- **Comparison with Firewalls:**
    - **Port forwarding:** Opens a specific port for access.
    - **Firewall:** Controls whether traffic is allowed through that port.

## Firewalls

- **Function:** Control inbound and outbound traffic based on rules. Acts as “border security” for networks.
- **Rule Criteria:**
    - Source/destination address
    - Port number
    - Protocol type (TCP, UDP, etc.)
- **Types:**
    
    
    | Type | Description |
    | --- | --- |
    | **Stateful Firewall** | Analyzes the **entire connection** (dynamic). Uses more resources. Blocks based on connection behavior. |
    | **Stateless Firewall** | Analyzes **individual packets** (static rules). Uses fewer resources but is less intelligent. Useful for filtering large traffic volumes like DDoS attacks. |
- **Examples:** Hardware firewalls (enterprise routers), software-based firewalls (e.g., Snort).

## VPN (Virtual Private Network)

- **Purpose:** Securely connects devices or networks over the Internet using an **encrypted tunnel**.
- **Functionality:** Creates a private network between remote devices or offices (e.g., Office #1 ↔ Office #2).
- **Key Benefits:**
    
    
    | Benefit | Description |
    | --- | --- |
    | **Remote connectivity** | Connects geographically separate offices or networks. |
    | **Privacy** | Encrypts traffic to prevent eavesdropping on public Wi-Fi. |
    | **Anonymity** | Hides user identity from ISPs and intermediaries (depending on VPN provider practices). |
- **Use Case (TryHackMe):** Safely connect users to vulnerable machines without public Internet exposure.
- **Common VPN Technologies:**
    
    
    | Technology | Description |
    | --- | --- |
    | **PPP (Point-to-Point Protocol)** | Handles authentication and encryption; not routable by itself. |
    | **PPTP (Point-to-Point Tunneling Protocol)** | Uses PPP data for tunneling; easy setup but weak encryption. |
    | **IPSec (Internet Protocol Security)** | Encrypts IP packets directly; strong encryption but complex setup. |

## LAN Networking Devices

### Routers

- **Function:** Connect different networks and determine the best path for data (Layer 3 of OSI).
- **Responsibilities:**
    - Route packets based on factors like shortest, fastest, or most reliable path.
    - Support configurations such as port forwarding and firewall rules.
- **Key Role:** Directs traffic between networks (e.g., local and Internet).

|  | **🧭 OSPF (Open Shortest Path First)** | **🛣️ RIP (Routing Information Protocol)** |
| --- | --- | --- |
| **Key Characteristics:** | • **Type:** **Link-State** routing protocol.
• **Metric:** **Cost**, which is calculated based on **link bandwidth** (default formula: $10^8 / \text{Bandwidth in bps}$).
• **Algorithm:** Uses **Dijkstra's Shortest Path First (SPF) algorithm** to construct a topological map of the entire network.
• **Update Mechanism:** Routers send **Link State Advertisements (LSAs)** only when a network change occurs, and every 30 minutes to ensure database synchronization. | • **Type:** **Distance-Vector** routing protocol.
• **Metric:** **Hop Count** (number of routers traversed).
• **Algorithm:** Uses the **Bellman-Ford algorithm** (or a variation).
• **Update Mechanism:** Routers send their **entire routing table** to their immediate neighbors every **30 seconds**, regardless of whether the network has changed. |
| **👍 Advantages:** | • **Scalability:** Highly **scalable** and suited for large, complex networks because it supports **hierarchical design** (Areas).
• **Convergence:** Very **fast convergence** due to event-triggered updates, allowing quick adaptation to network changes.
• **Loop-Free:** The SPF algorithm guarantees a **loop-free** routing topology.
• **Intelligent Path:** Chooses the best path based on **bandwidth**, providing more efficient traffic distribution. | • **Simplicity:** Very **easy to configure and implement**, making it suitable for small environments.
• **Low Overhead (Initial):** Requires **less initial processing power** compared to OSPF's database creation. |
| **👎 Disadvantages:** | • **Complexity:** More **complex to configure and troubleshoot** than RIP.
• **Overhead:** Requires **more CPU and memory resources** from the routers to run the SPF algorithm and maintain the link-state database. | • **Scalability Limit:** Has a maximum hop count of **15** (a path of 16 hops is considered unreachable), severely limiting network size.
• **Convergence:** **Slow convergence** due to periodic updates and reliance on timers (e.g., hold-down timers) to resolve network issues.
• **Less Efficient Path:** Only considers the **number of hops**, potentially choosing a slower path over a fast, high-bandwidth path that has one more hop.
• **Bandwidth Use:** Periodic broadcasts of the **entire routing table** can consume unnecessary network bandwidth, even when the network is stable. |

### Switches

- **Function:** Connect multiple devices within the same network.
- **Types:**
    
    
    | Type | OSI Layer | Function |
    | --- | --- | --- |
    | **Layer 2 Switch** | Layer 2 | Forwards **frames** using **MAC addresses**. |
    | **Layer 3 Switch** | Layer 3 | Forwards **frames** and also **routes packets** using **IP addresses** (partial router functionality). |
- **VLAN (Virtual LAN):**
    - Splits a physical network into logical segments for **security** and **traffic management**.
    - Example: “Sales” and “Accounting” departments share the same switch but cannot communicate directly while both access the Internet.