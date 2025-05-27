# System Design

## 🧩 **Module 1: Introduction to System Design**

### 🔍 What is System Design?

**System design** is the process of defining the architecture, components, modules, interfaces, and data for a system to satisfy specific requirements. It's like planning the blueprint of a building before construction.

In software, it covers:

* How components communicate (frontend, backend, databases, APIs)
* How data flows and is processed
* How to make systems **scalable**, **reliable**, and **maintainable**

### 🛠 Why Is It Important?

* **In Interviews**: Top tech companies ask system design questions to assess your architectural thinking.
* **In Real Projects**: Designing robust systems avoids technical debt and failures at scale.
* **In Team Work**: Helps communicate solutions clearly with developers, DevOps, and stakeholders.

> ✅ *“A well-designed system saves money, scales smoothly, and fails gracefully.”*

---

### 🧱 Key Components of a System

Here’s a high-level breakdown of what makes up a typical system:

| Component              | Role                                           |
| ---------------------- | ---------------------------------------------- |
| **Client**             | Initiates requests (e.g., browser, mobile app) |
| **Web Server**         | Handles HTTP requests and serves content       |
| **Application Server** | Runs business logic                            |
| **Database**           | Stores and retrieves data                      |
| **Cache**              | Temporary fast-access storage                  |
| **Load Balancer**      | Distributes traffic to multiple servers        |
| **Queue**              | Handles async task processing                  |
| **Storage**            | Manages large files (images, logs, backups)    |
| **Monitoring**         | Observes system health and metrics             |

---

### 🖥 Basic Computer Architecture Refresher

Understanding how a computer works helps with system design at scale.

#### 🔸 Components Overview:

```
[CPU] ⇄ [RAM]
  ↓         ↓
[Cache]   [Disk (HDD/SSD)]
```

#### 📌 Definitions:

* **CPU (Central Processing Unit)**: Executes instructions.
* **RAM (Random Access Memory)**: Temporary memory for active processes.
* **Cache**: Faster than RAM, stores frequently used data (L1, L2, L3).
* **Disk**: Long-term data storage (e.g., files, databases).

---

### 🧠 Diagram: Typical Web-Based System Architecture

```
[ Client (Browser/App) ]
          ↓
   [ Load Balancer ]
    ↙           ↘
[ Web Server ]  [ Web Server ]
       ↓             ↓
  [ App Logic / Backend ]
          ↓
     [ Database ]
         ↕
     [ Cache ]
```

---

### 🔎 Real-World Analogy

Think of a **restaurant**:

* You (client) make an order (request)
* The waiter (web server) takes it to the kitchen (application logic)
* The kitchen checks the pantry (database or cache)
* If ingredients (data) are not available, it fetches from storage (disk)
* The food (response) is delivered back to you

> 🎯 The goal is to keep service fast, reliable, and available even during rush hour (high traffic)!

---

### ✅ Summary Checklist

| Concept                      | Covered? ✅ |
| ---------------------------- | ---------- |
| What is system design?       | ✅          |
| Why is it important?         | ✅          |
| Key system components        | ✅          |
| Computer architecture basics | ✅          |
| Sample architecture diagram  | ✅          |
| Real-world analogy           | ✅          |

---

## 🧠 **Module 2: Core Principles of System Design**

---

### ⚙️ What Makes a Good System?

A well-designed system should be:

| Principle        | Meaning                                            |
| ---------------- | -------------------------------------------------- |
| **Scalable**     | Can handle increased load without performance loss |
| **Reliable**     | Functions correctly even when parts fail           |
| **Maintainable** | Easy to update, debug, and extend                  |
| **Efficient**    | Uses resources (CPU, memory, network) wisely       |
| **Available**    | Ready to serve users with minimal downtime         |
| **Secure**       | Protects data and access from threats              |

> 📌 These principles guide every architectural choice you make.

---

### 🌩️ The Three Pillars: Moving, Storing, Transforming Data

Every system revolves around these three key actions:

1. **Moving Data**
   E.g., HTTP requests, message queues, API calls

2. **Storing Data**
   E.g., SQL, NoSQL, object storage, distributed file systems

3. **Transforming Data**
   E.g., Business logic, computations, machine learning, formatting

> Think of your system as a pipeline that moves, stores, and transforms information continuously.

---

### 🧱 System Design Trade-Offs

You often can’t have it all—trade-offs are real. One major concept that frames this:

---

### 🔺 CAP Theorem

> *You can only choose 2 out of 3:*

| Component                   | Definition                                          |
| --------------------------- | --------------------------------------------------- |
| **Consistency (C)**         | All nodes see the same data at the same time        |
| **Availability (A)**        | System continues to operate even if some parts fail |
| **Partition Tolerance (P)** | System works even when network fails between nodes  |

#### Example:

* **CA (no Partition Tolerance)**: Traditional databases like SQL
* **CP (no Availability)**: Systems that prioritize consistency under network failure
* **AP (no Consistency)**: Systems like DNS or some NoSQL databases

🧠 **Diagram (Simple CAP Triangle):**

```
           Consistency
            /     \
           /       \
    Partition ——— Availability
         Tolerance
```

> ⚖️ You must decide what trade-offs to make based on the use case.

---

### 🔧 Design for Failure

No system is perfect. Assume things **will** go wrong:

| Strategy                        | Purpose                                       |
| ------------------------------- | --------------------------------------------- |
| **Redundancy**                  | Backup components take over when one fails    |
| **Retry Mechanisms**            | Auto-retry failed operations                  |
| **Timeouts & Circuit Breakers** | Avoid hanging requests or cascading failure   |
| **Monitoring & Alerts**         | Detect issues before users do                 |
| **Graceful Degradation**        | Continue partially even if some services fail |

> ✅ *"Hope for the best, but design for the worst."*

---

### 🧠 Real-World Analogy

**Think of a delivery company**:

* **Scalable**: Can hire more drivers for more orders
* **Reliable**: Still delivers even if a few vehicles break
* **Maintainable**: Routes and schedules are easy to update
* **CAP**: If GPS (network) fails, do we wait (consistency) or deliver based on the last known address (availability)?

---

### ✅ Summary Checklist

| Concept                       | Covered? ✅ |
| ----------------------------- | ---------- |
| Key system design principles  | ✅          |
| 3 data pillars                | ✅          |
| Trade-offs and CAP theorem    | ✅          |
| Design for failure strategies | ✅          |
| Real-world analogy            | ✅          |

---

## 🌐 **Module 3: Networking Basics**

---

### 🧩 IP Addresses (IPv4 vs IPv6)

| Property        | IPv4                       | IPv6                                      |
| --------------- | -------------------------- | ----------------------------------------- |
| Format          | 32-bit (e.g., 192.168.1.1) | 128-bit (e.g., 2001:0db8::1)              |
| Total Addresses | \~4.3 billion              | ≈ 340 undecillion (unlimited vibes)       |
| Address Style   | Decimal, dotted            | Hexadecimal, colon-separated              |
| Example         | `192.0.2.1`                | `2001:0db8:85a3:0000:0000:8a2e:0370:7334` |

> 📌 **IPv6** solves IPv4 exhaustion and is more secure and efficient in routing.

---

### 📦 Data Packets & Internet Protocol (IP)

* **Packet = Header + Payload**
* The header carries metadata (source, destination, TTL, etc.)
* **MTU (Maximum Transmission Unit)**: max packet size (e.g., 1500 bytes in Ethernet)

📌 Fragmentation occurs if packets exceed MTU and routers split them.

---

### 🔄 Transport Layer Protocols: TCP vs UDP

| Feature     | TCP                                 | UDP                            |
| ----------- | ----------------------------------- | ------------------------------ |
| Connection  | Connection-oriented                 | Connectionless                 |
| Reliability | Ensures delivery, ordering, no loss | No guarantee (fire-and-forget) |
| Speed       | Slower                              | Faster                         |
| Use Cases   | HTTP(S), FTP, Email, SSH            | DNS, VoIP, Gaming, Streaming   |

> 🧠 Think of TCP like sending registered mail, and UDP like tossing postcards.

---

### 🌍 DNS – Domain Name System

**Translates human-readable names to IPs**
Example: `www.google.com` → `142.250.190.4`

#### DNS Steps:

1. Browser checks local DNS cache
2. If not found, asks OS → Resolver → Root → TLD (.com) → Authoritative Server
3. IP is returned and cached

> ⚡ DNS caching (local, OS, ISP) boosts speed
> 🛡️ DNSSEC adds trust/authentication to DNS responses

---

### 🧱 Networking Infrastructure Overview

| Component      | Description                                                            |
| -------------- | ---------------------------------------------------------------------- |
| **Public IP**  | Globally routable (e.g., assigned by ISP)                              |
| **Private IP** | Local/internal use only (`192.168.x.x`, `10.x.x.x`, `172.16.x.x`)      |
| **Firewall**   | Security layer that filters traffic (stateful/stateless)               |
| **Port**       | Virtual endpoint for communication (e.g., port 80 = HTTP, 443 = HTTPS) |
| **NAT**        | Network Address Translation—maps private IPs to public                 |

📌 **Firewalls** and **NAT** work together to allow internal networks to talk to the internet securely.

---

### 🖼️ Simple Diagram: Request from Browser to Web Server

```
[Browser] 
   ↓ DNS Lookup
[DNS Resolver]
   ↓ Get IP
[Client (Private IP)] --[NAT + Firewall]--> [Internet]
   ↓
[Load Balancer] → [Web Server (Public IP)]
   ↓
[Database] or Response back
```

---

### 🚦Port Number Cheat Sheet

| Protocol | Port |
| -------- | ---- |
| HTTP     | 80   |
| HTTPS    | 443  |
| SSH      | 22   |
| FTP      | 21   |
| DNS      | 53   |
| SMTP     | 25   |
| IMAP     | 143  |
| POP3     | 110  |

---

### ✅ Quick Review

| Concept                 | ✅ Covered? |
| ----------------------- | ---------- |
| IP addressing basics    | ✅          |
| Packets & MTU           | ✅          |
| TCP vs UDP comparison   | ✅          |
| DNS lookup process      | ✅          |
| Public/private IP, NAT  | ✅          |
| Firewall and port usage | ✅          |

---

## 🍰 **Module 4: Application Layer Protocols**

---

The **Application Layer** is where humans interact with systems. It’s the top of the OSI model (Layer 7), where actual services like browsing, emailing, chatting, and file sharing live.

---

### 🌐 HTTP & HTTPS – Web Communication Basics

* **HTTP (Hypertext Transfer Protocol)**:

  * Stateless, plain-text communication
  * Follows a **request-response** model
  * Common methods: `GET`, `POST`, `PUT`, `DELETE`

* **HTTPS** = HTTP + TLS/SSL encryption

  * Ensures **data confidentiality, integrity, and authenticity**

#### Example Request:

```
GET /index.html HTTP/1.1
Host: example.com
```

#### Browser Interaction Flow:

```
Browser → DNS → IP → TCP (port 443) → TLS handshake → HTTP(S) Request
```

> 🔐 HTTPS is **critical** for protecting login forms, banking, and APIs.

---

### 🧃 WebSockets – Real-Time Web Communication

* **Full-duplex** communication over a single TCP connection.
* Unlike HTTP, it maintains a **persistent connection** between client/server.
* Useful for:

  * Chat apps (Messenger, Discord)
  * Real-time updates (stocks, game states)

#### Diagram:

```
[Client] ⇄ (WebSocket over TCP) ⇄ [Server]
```

> 💬 Think: HTTP is a walkie-talkie. WebSockets is a phone call.

---

### 📧 Email Protocols

| Protocol | Purpose           | Port         | Notes                            |
| -------- | ----------------- | ------------ | -------------------------------- |
| SMTP     | Send mail         | 25, 587, 465 | Used by outgoing mail servers    |
| IMAP     | Read from server  | 143, 993     | Keeps messages on server         |
| POP3     | Download + delete | 110, 995     | Downloads and clears local inbox |

* IMAP is **sync-friendly** (great for multiple devices)
* POP3 is old-school (offline-first)

---

### 📁 File Transfer Protocols

| Protocol | Secure? | Notes                              |
| -------- | ------- | ---------------------------------- |
| FTP      | ❌       | Plain text, not secure             |
| FTPS     | ✅       | FTP with SSL/TLS                   |
| SFTP     | ✅       | Uses SSH for secure file transfer  |
| SCP      | ✅       | Another SSH-based fast copy method |

> 🚚 For sensitive files, **SFTP** or **SCP** should be your go-to.

---

### 📡 Real-Time Messaging Protocols

| Protocol   | Use Case                              | Notes                                    |
| ---------- | ------------------------------------- | ---------------------------------------- |
| **WebRTC** | Peer-to-peer audio/video (Zoom, Meet) | Uses ICE, STUN, TURN for NAT traversal   |
| **MQTT**   | IoT devices (low power)               | Publish/subscribe model                  |
| **AMQP**   | Enterprise messaging (RabbitMQ)       | Queued messages with delivery guarantees |

> 🧠 MQTT = smart lights
> 📦 AMQP = enterprise queues

---

### 🧠 RPC – Remote Procedure Call

* **RPC**: One machine calls a function on another, as if it were local
* **Common Types**:

  * **JSON-RPC**: Lightweight, used in JavaScript
  * **XML-RPC**: Older, verbose
  * **gRPC**: Google’s high-performance RPC using Protocol Buffers

#### Example:

```protobuf
rpc GetUser(GetUserRequest) returns (UserResponse);
```

> ⚙️ Used in microservices to reduce REST overhead

---

### 🧪 When to Use What?

| Protocol Type     | Best For                         |
| ----------------- | -------------------------------- |
| HTTP/HTTPS        | REST APIs, web apps              |
| WebSockets        | Live chat, real-time games       |
| Email (SMTP/IMAP) | Communication                    |
| FTP/SFTP          | Large file transfers             |
| MQTT/AMQP         | IoT, queuing systems             |
| gRPC/RPC          | Fast internal microservice calls |

---

### ✅ Quick Review

| Topic                         | ✅ Covered? |
| ----------------------------- | ---------- |
| HTTP vs HTTPS                 | ✅          |
| WebSockets functionality      | ✅          |
| Email protocol differences    | ✅          |
| Secure file transfer methods  | ✅          |
| Real-time messaging protocols | ✅          |
| gRPC and RPC concepts         | ✅          |

---

## 🧩 **Module 5: API Design**

**“Let systems speak clearly, efficiently, and safely.”**

---

### 🍽️ What is an API?

> **API (Application Programming Interface)** is a contract between systems to exchange data in a defined format.

It enables communication between:

* Frontend ↔ Backend
* Microservices
* Third-party integrations (Google Maps, Stripe)

---

### 🔁 CRUD Operations & RESTful APIs

**CRUD = Create, Read, Update, Delete**

REST (Representational State Transfer) is the **most common** API style.

| Action     | HTTP Method | Endpoint Example |
| ---------- | ----------- | ---------------- |
| Create     | POST        | `/users`         |
| Read (all) | GET         | `/users`         |
| Read (one) | GET         | `/users/{id}`    |
| Update     | PUT/PATCH   | `/users/{id}`    |
| Delete     | DELETE      | `/users/{id}`    |

#### REST Features:

* **Stateless**: No session saved on server
* **Resource-oriented**: Each object (user, post) is a resource
* **JSON** or XML payloads

---

### 🧠 GraphQL – A Flexible Query Language

> "Ask exactly what you want, get exactly what you need."

Developed by Facebook to solve over-fetching or under-fetching data.

#### Example Query:

```graphql
query {
  user(id: "42") {
    name
    email
    posts {
      title
    }
  }
}
```

#### GraphQL Features:

* Single endpoint (`/graphql`)
* Strongly typed schema
* Reduces bandwidth (clients pick only needed fields)

> ⚠️ Needs good validation & security (introspection can leak metadata)

---

### 🚀 gRPC – Fast, Binary RPC

> Created by Google for **high-performance**, low-latency service-to-service communication.

#### Features:

* Uses **Protocol Buffers** instead of JSON (lightweight + fast)
* Supports streaming: **client, server, and bidirectional**
* Enforces contracts via `.proto` files
* Built-in support for **authentication** and **load balancing**

| Protocol | Transport | Speed | Best Use            |
| -------- | --------- | ----- | ------------------- |
| REST     | HTTP      | 🐢    | Public APIs         |
| GraphQL  | HTTP      | 🐇    | Frontend-heavy apps |
| gRPC     | HTTP/2    | 🚀    | Internal services   |

---

### 🧯 Versioning APIs

Helps maintain backward compatibility when your API evolves.

| Strategy          | Example                               |
| ----------------- | ------------------------------------- |
| URI Versioning    | `/v1/users`, `/v2/users`              |
| Header Versioning | `Accept: application/vnd.app.v1+json` |
| Query Parameter   | `/users?version=1`                    |

> 🔁 Tip: Avoid breaking old clients unless **really necessary**.

---

### 🧃 Rate Limiting & CORS

* **Rate Limiting**: Protect your APIs from abuse

  * e.g., Max 1000 requests/hour per user
  * Tools: NGINX, API Gateways, Redis-based counters

* **CORS (Cross-Origin Resource Sharing)**:

  * Allows JS apps from other origins to access your API
  * Configure HTTP headers like:

    ```
    Access-Control-Allow-Origin: *
    ```

---

### 🎓 Best Practices

✅ Use nouns in URLs (`/users`, not `/getUser`)
✅ Stick to standard HTTP codes (`200 OK`, `404 Not Found`)
✅ Use pagination (`?page=1&limit=10`)
✅ Always validate input & sanitize output
✅ Document with Swagger/OpenAPI

---

### 🎯 Summary Review

| Concept                        | ✅ Covered |
| ------------------------------ | ---------- |
| RESTful API design principles  | ✅         |
| CRUD operations                | ✅         |
| GraphQL structure              | ✅         |
| gRPC use cases                 | ✅         |
| API versioning strategies      | ✅         |
| Rate limiting & CORS explained | ✅         |

---

## 🧭 **Module 7: Proxy Servers and Load Balancing**

*"If caching is memory, proxies are brains with shields, and load balancers are the traffic cops."*

---

### 🔄 What is a Proxy Server?

A **proxy server** acts as an intermediary between a client and the destination server.

#### 🧩 Types of Proxy Servers:

| Type                  | Description                             | Example Use                   |
| --------------------- | --------------------------------------- | ----------------------------- |
| **Forward Proxy**     | Hides the client from the server        | Bypassing geo-restrictions 🌍 |
| **Reverse Proxy**     | Hides the server from the client        | Load balancing, caching, SSL  |
| **Transparent Proxy** | Intercepts traffic without modifying it | Schools, ISPs, workplaces 🏫  |

---

### 🛡️ Why Use Proxies?

* **Security**: IP masking, rate limiting, DDOS protection 🔐
* **Access Control**: Block/allow content or sites 🔒
* **Anonymity**: Hide client identity 🕵️
* **Caching**: Reduce repeated requests 💾
* **SSL Termination**: Offload HTTPS encryption from backend servers 🧯

---

### 🎛️ Load Balancers – Smart Traffic Distributors

> **Load balancers** distribute incoming traffic across multiple servers to avoid overloading any one server.

Think of it as a **traffic officer** standing at the entrance of a server farm 🧑‍✈️.

---

### ⚙️ Load Balancer Types

| Type                      | Description                            |
| ------------------------- | -------------------------------------- |
| **Layer 4 (Transport)**   | Operates at TCP/UDP level              |
| **Layer 7 (Application)** | Operates at HTTP level (smart routing) |

#### Examples:

* **Nginx**, **HAProxy**, **Traefik**, **AWS ELB**

---

### 🔁 Load Balancing Algorithms

| Algorithm                | How it works                                   | Use Case                       |
| ------------------------ | ---------------------------------------------- | ------------------------------ |
| **Round Robin**          | Cycles through servers                         | Equal server capacity          |
| **Least Connections**    | Sends to the server with fewest active clients | Varying loads                  |
| **IP Hash**              | Routes users to the same server based on IP    | Sticky sessions                |
| **Weighted Round Robin** | Gives more traffic to stronger servers         | Mixed server strengths         |
| **Geo-based**            | Chooses nearest server                         | Global apps (Netflix, YouTube) |

---

### ☂️ Handling Failures and Redundancy

Redundancy and failover are **critical** in system design:

* **Health Checks**: Regular ping tests to backend servers 🩺
* **Failover Mechanisms**: Reroute to healthy servers during downtime 🔁
* **Multi-region Load Balancing**: Fall back to another data center 🌍
* **Active-Passive Setup**: Backup LB/server kicks in only on failure 🛑➡️🟢
* **Auto-scaling**: Dynamically adds/removes servers based on load 📈

---

### 🧪 Real-Life Example

You're visiting **Amazon.com** during Black Friday:

1. Your request goes through a **reverse proxy** (Nginx).
2. The proxy handles SSL, checks for cached content.
3. If needed, the **load balancer** picks the best backend server (lowest load).
4. One server might handle cart operations, another handles product search.

Result: **Fast, reliable experience** — even with millions online.

---

### 🧠 Summary Cheat Sheet

| Concept       | Description                             |
| ------------- | --------------------------------------- |
| Proxy Server  | Middleman for traffic routing           |
| Reverse Proxy | Shields backend servers                 |
| Load Balancer | Distributes traffic                     |
| L4 vs L7      | Network vs Application level            |
| Redundancy    | Backup systems to prevent downtime      |
| Health Checks | Ensure servers are alive and responsive |

---

💾 **Module 8: Databases and Scaling**
*"Where your data breathes, grows, and sometimes screams for optimization."* 😅 ,`ChatGpt`

---

## 🗄️ **1. Types of Databases**

### 🔹 **Relational (SQL)**

* Structured data, with predefined schemas (tables, rows)
* Uses **SQL (Structured Query Language)**
* Examples: **PostgreSQL**, **MySQL**, **Oracle**, **SQL Server**
* Great for **transactions, financial systems, and consistent data**

> 🔑 ACID-compliant: Atomicity, Consistency, Isolation, Durability

---

### 🔸 **NoSQL (Non-relational)**

* Flexible schemas, suitable for unstructured or semi-structured data
* Types:

  * **Document-based**: MongoDB, CouchDB
  * **Key-value stores**: Redis, DynamoDB
  * **Wide-column**: Cassandra
  * **Graph DBs**: Neo4j
* Best for **scalability**, **agility**, and **large distributed systems**

> 🧩 BASE: Basically Available, Soft state, Eventually consistent

---

### 🔹 **In-memory Databases**

* Super-fast data access, stored in RAM
* Examples: **Redis**, **Memcached**
* Use cases: Caching, session storage, real-time analytics

---

## 📐 **2. Vertical vs Horizontal Scaling**

| Scaling Type   | Description                        | Example             |
| -------------- | ---------------------------------- | ------------------- |
| **Vertical**   | Add more power to the same machine | Upgrade CPU/RAM     |
| **Horizontal** | Add more machines (scale out)      | Add more DB servers |

* **Vertical scaling** is simpler but limited
* **Horizontal scaling** offers higher fault tolerance and better long-term growth

---

## 🧱 **3. Sharding and Replication**

### 🍰 **Sharding**

* Split the database into **smaller, manageable parts** (shards)
* Each shard holds a portion of the data
* Based on:

  * User ID
  * Region
  * Hashing

> 📦 Like dividing a warehouse into sections by product type or region

---

### 📡 **Replication**

* **Copy data** across multiple servers
* Types:

  * **Master-Slave** (Primary-Secondary)
  * **Master-Master**
  * **Read Replicas**

> 🧬 Boosts read performance and adds redundancy

---

## 🔍 **4. Database Performance Optimization**

* **Indexing**: Accelerate searches on columns
* **Query Optimization**: Write efficient SQL (avoid `SELECT *`)
* **Connection Pooling**: Reuse DB connections
* **Caching**: Store frequently accessed data in memory
* **Partitioning**: Divide large tables into smaller pieces

---

## 💡 Real-World Analogy

Imagine Amazon’s order system:

* A **SQL DB** ensures consistent transactions for payments.
* A **NoSQL DB** handles the fast, flexible product catalog.
* **Redis** stores your shopping cart for snappy interactions.
* **Shards** distribute users across servers by region.
* **Replication** ensures you don’t lose orders during server failure.

---

## 🧠 Summary Cheat Sheet

| Concept      | Purpose                             |
| ------------ | ----------------------------------- |
| SQL DB       | Structured data, strong consistency |
| NoSQL DB     | Scalability, flexible schema        |
| In-memory DB | Blazing speed, temporary storage    |
| Sharding     | Data distribution for scalability   |
| Replication  | High availability, load balancing   |
| Indexing     | Fast lookups                        |
| Partitioning | Divide large datasets               |

---

🫡 **Wrap-Up: System Design Masterclass Takeaway**
*"No packet dropped, no concept left behind."*

---

### 🧱 **Core Concepts Recap**

| 🧩 Module | Key Focus                      | Highlights                                               |
| --------- | ------------------------------ | -------------------------------------------------------- |
| 1. Intro  | What & Why of System Design    | System components, architecture, real-world significance |
| 2. Core   | Design Principles & Trade-offs | Scalability, CAP Theorem, system resilience              |
| 3. Net    | Networking Basics              | TCP/UDP, IPs, DNS, TTL—your first "ping" to architecture |
| 4. App    | Application Layer Protocols    | HTTP, WebSockets, SMTP, FTP, RPC magic                   |
| 5. API    | Designing Reliable Interfaces  | REST, gRPC, versioning, rate limiting, best practices    |
| 6. Cache  | Caching & CDN                  | Eviction policies, push vs pull CDN, speed & savings     |
| 7. Proxy  | Load Balancing & Proxy Power   | Round robin, IP hash, failovers, proxies in action       |
| 8. DB     | Databases & Scaling            | SQL vs NoSQL, sharding, replication, optimization tricks |

---

### 🔑 **Big Takeaways**

* 📡 *Scalability isn’t just a buzzword—it’s a survival skill.*
* 🔄 *Trade-offs define architecture; perfection is a myth.*
* ⚙️ *Modularity = maintainability = peace of mind.*
* 🧠 *Design for failure, cache for speed, and always plan for growth.*





