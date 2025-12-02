# HTTP in Detail

## 🌐 HTTP & HTTPS

- **HTTP (HyperText Transfer Protocol):**
    - Developed (1989–1991) by Tim Berners-Lee.
    - Protocol for transferring web content (HTML, images, videos, etc.) between client and server.
- **HTTPS (Secure HTTP):**
    - Encrypted version of HTTP using SSL/TLS.
    - Provides confidentiality, integrity, and authenticity—ensures secure communication with the correct server.

## 🔗 URLs (Uniform Resource Locators)

A URL defines *how and where* to access a resource.

**Components:**

- **Scheme:** Protocol (e.g., HTTP, HTTPS, FTP).
- **User:** Optional credentials (username/password).
- **Host:** Domain name or IP address of the server.
- **Port:** Communication port (default: 80 for HTTP, 443 for HTTPS).
- **Path:** File or directory location on the server.
- **Query String:** Parameters for data requests (e.g., `?id=1`).
- **Fragment:** Points to a specific part of the page (e.g., `#section2`).

## ⚙️ Requests & Responses

**Request Example:**

```
GET / HTTP/1.1
Host: tryhackme.com
User-Agent: Mozilla/5.0 Firefox/87.0
Referer: https://tryhackme.com/
```

- **Request Line:** Defines method, resource path, and HTTP version.
- **Headers:** Provide metadata (host, browser info, referrer, etc.).
- **Blank Line:** Signals end of request.

**Response Example:**

```
HTTP/1.1 200 OK
Server: nginx/1.15.8
Date: Fri, 09 Apr 2021 13:34:03 GMT
Content-Type: text/html
Content-Length: 98
```

- **Status Line:** Protocol version + status code.
- **Headers:** Metadata (server, date, type, length).
- **Body:** Actual content (HTML, image, etc.).
- **Blank Line:** Marks end of headers.

## 🧭 HTTP Methods

| **Method** | **Purpose** |
| --- | --- |
| **GET** | Retrieve data from a server. |
| **POST** | Submit new data (e.g., form submission). |
| **PUT** | Update existing resource. |
| **DELETE** | Remove resource from server. |

## 📊 HTTP Status Codes

**Categories:**

- **100–199:** Informational (rarely used).
- **200–299:** Success.
- **300–399:** Redirection.
- **400–499:** Client errors.
- **500–599:** Server errors.

**Common Codes:**

- **200 OK:** Request succeeded.
- **201 Created:** Resource created.
- **301 Moved Permanently:** Permanent redirect.
- **302 Found:** Temporary redirect.
- **400 Bad Request:** Invalid request.
- **401 Unauthorized:** Requires authentication.
- **403 Forbidden:** Access denied.
- **404 Not Found:** Resource doesn’t exist.
- **405 Method Not Allowed:** Incorrect HTTP method.
- **500 Internal Server Error:** Server-side failure.
- **503 Service Unavailable:** Server overloaded or down.

## 📬 Headers

**Request Headers (client → server):**

- **Host:** Specifies target website.
- **User-Agent:** Identifies browser/software.
- **Content-Length:** Size of data sent.
- **Accept-Encoding:** Compression methods supported.
- **Cookie:** Sends stored session/user data.

**Response Headers (server → client):**

- **Set-Cookie:** Sends cookie to client.
- **Cache-Control:** Caching policy.
- **Content-Type:** Data format (HTML, image, etc.).
- **Content-Encoding:** Compression type used.

## 🍪 Cookies

- Small data pieces stored on the client’s device.
- Sent via **Set-Cookie** header and returned with subsequent requests.
- Used for:
    - Authentication (e.g., session tokens).
    - Personalization (user settings).
    - Tracking visits or site preferences.
- **HTTP is stateless** → cookies provide “memory” for user sessions.

**Viewing Cookies:**

- Open browser **Developer Tools → Network tab → Cookies section** to inspect cookies sent/received in requests.