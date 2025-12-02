# DNS in Detail

## 🧭 DNS (Domain Name System)

**Purpose:**

- Translates human-readable domain names (e.g., `tryhackme.com`) into IP addresses (e.g., `104.26.10.229`).
- Functions like an “address book” for the internet, allowing communication without remembering numerical IPs.

## 🌐 Domain Hierarchy

| Level | Example | Description |
| --- | --- | --- |
| **TLD (Top-Level Domain)** | `.com`, `.org`, `.uk` | Rightmost section of a domain. - **gTLDs** (generic): `.com`, `.org`, `.edu`, `.gov` - **ccTLDs** (country code): `.ca`, `.co.uk` |
| **Second-Level Domain (SLD)** | `tryhackme` in `tryhackme.com` | Main registered part of the domain. - Limited to 63 characters.  - May contain letters, numbers, and hyphens (with restrictions). |
| **Subdomain** | `admin.tryhackme.com` | Optional prefix separated by a dot.  - Used for organizing or hosting services.  - Same 63-character limit and naming rules.  - Can have multiple nested subdomains (≤253 characters total). |

## 📘 Common DNS Record Types

| Record Type | Purpose | Example |
| --- | --- | --- |
| **A** | Maps domain to an **IPv4** address | `tryhackme.com → 104.26.10.229` |
| **AAAA** | Maps domain to an **IPv6** address | `2606:4700:20::681a:be5` |
| **CNAME** | Alias for another domain name | `store.tryhackme.com → shops.shopify.com` |
| **MX** | Specifies mail servers for a domain | `tryhackme.com → alt1.aspmx.l.google.com` (with priority) |
| **TXT** | Stores text data for verification or email security | SPF, DKIM, domain ownership checks |

## ⚙️ DNS Resolution Process (How a Request Works)

1. **Local Cache Check:**
    
    Your computer first checks its DNS cache for a recent lookup.
    
2. **Recursive DNS Server:**
    - Provided by your ISP or set manually (e.g., Google’s 8.8.8.8).
    - Checks its cache; if not found, it queries further servers.
3. **Root DNS Servers:**
    - The backbone of DNS.
    - Direct the request to the correct **TLD server** (e.g., `.com`).
4. **TLD Server:**
    - Directs the query to the **Authoritative Nameserver** for that domain.
5. **Authoritative DNS Server:**
    - Contains the domain’s actual DNS records.
    - Sends the correct IP or record type back to the recursive server.
6. **Caching & TTL:**
    - The recursive server caches the response for a set **TTL (Time To Live)** value to speed up future lookups.