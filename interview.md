### 1. The "SCI E-Learning" Tech Stack
*Based on public SCI infrastructure data, these are the core services you might be working on. Knowing how these work under the hood is a huge plus.*

*   **Jitsi Meet (Video Conferencing):**
    *   **Core Concept:** Jitsi is an open-source WebRTC application.
    *   **Key Component:** **Jitsi Videobridge (JVB)**. Unlike traditional mesh networks (where every user connects to every other user), JVB acts as a **SFU (Selective Forwarding Unit)**. It receives video streams from users and forwards them to others without transcoding (which saves CPU).
    *   **Interview Q:** *How does Jitsi handle scaling?* (Answer: You add more Videobridges and a load balancer/shard controller like "Jicofo").
*   **ShareLaTeX / Overleaf (Collaborative Editing):**
    *   **Core Concept:** Real-time collaboration.
    *   **Key Tech:** **WebSockets** (for real-time bidirectional communication) and **Operational Transformation (OT)** (the algorithm that resolves conflicts when two people type at the same time).
    *   **Storage:** Typically uses MongoDB and Redis (for session caching).
*   **Etherpad (Real-time Text):**
    *   Similar to ShareLaTeX but lighter. Also relies heavily on WebSockets.

---

### 2. Networking Basics (Refresher)
*Since you have a CCNA background, we’ll focus on the application layer relevant to E-Learning.*

*   **WebRTC (Web Real-Time Communication):**
    *   This is the backbone of Jitsi/BigBlueButton.
    *   **ICE (Interactive Connectivity Establishment):** The protocol used to find the best path to connect peers.
    *   **STUN Server:** Tells a client what its public IP is (needed because of NAT).
    *   **TURN Server:** Relays traffic if a direct P2P connection fails (e.g., symmetric firewalls). *SCI likely hosts their own STUN/TURN servers.*
*   **TCP vs. UDP:**
    *   **Video/Audio (Jitsi):** Uses **UDP**. If a packet (video frame) is lost, we don't care; we just want the next one immediately. TCP retransmission causes lag.
    *   **Text/Data (ShareLaTeX):** Uses **TCP** (via HTTP/WebSockets). We need 100% accuracy for code.
*   **Reverse Proxies (Nginx/HAProxy):**
    *   SCI likely uses Nginx as a frontend for all these services (Jitsi, GitLab, Websites).
    *   It handles **SSL Termination** (decrypting HTTPS requests before sending them to the backend) and **Load Balancing**.

---

### 3. System Design Concepts
*If they ask you to "design a system," use their own tools as examples.*

**Scenario: Design a simplified version of ShareLaTeX.**
1.  **Client:** Browser with a code editor (JS).
2.  **Load Balancer:** Nginx (distributes users to servers).
3.  **App Server:** Node.js (handles the logic).
4.  **Real-Time Engine:** **Socket.io** or pure WebSockets.
5.  **Conflict Resolution:** **Operational Transformation (OT)**.
    *   *User A types "Hello" at index 0.*
    *   *User B deletes character at index 0.*
    *   *Server transforms User B's action based on User A's action so the document stays consistent.*
6.  **Database:** Document store (MongoDB) for storing LaTeX files; Redis for active user sessions.

**Scenario: Design a Submission System (like the one SCI runs).**
*   **Scalability Issue:** Thousands of students upload PDFs at 23:59.
*   **Solution:** **Async Processing**.
    *   Student uploads file $\rightarrow$ API saves to S3/Disk $\rightarrow$ API pushes a message to a **Queue** (e.g., RabbitMQ/Redis).
    *   Worker service picks up the job, verifies the PDF, compiles it, and sends an email confirmation.

---

### 4. Software Architectures
*   **Microservices vs. Monolith:**
    *   SCI likely maintains some older "Monolithic" PHP/Python apps (e.g., simple CRUD apps for room booking) and newer "Microservice" style apps (Dockerized containers).
    *   **Docker:** You know this well. Be ready to explain `docker-compose` (often used for single-node deployments of Jitsi/ShareLaTeX) vs. `Kubernetes` (used for larger clusters).
*   **Virtualization:**
    *   The SCI email mentions a "Server Cluster" with virtualization.
    *   They likely use **KVM (Kernel-based Virtual Machine)** or **Proxmox** (common in German unis). This is "Infrastructure as a Service" (IaaS) on-premise.

---

### 5. Linux & Troubleshooting (The "HiWi" Daily Life)
*As a Student Assistant, you might debug why a service is down. Since you know Linux, just brush up on the standard procedure.*

*   **"The Server is Slow" - What do you do?**
    1.  `top` / `htop`: Check **Load Average** (is it higher than the number of CPU cores?) and **Memory** (is Swap being used? Swap = slow).
    2.  `df -h`: Is the disk full? (Common issue with log files).
    3.  `tail -f /var/log/syslog` or `journalctl -xe`: Read the logs!
    4.  `netstat -tulpen` or `ss -lntu`: Check which ports are open and what process is listening.
    5.  `systemctl status [service_name]`: Is the service actually running?

---

### 6. Quick Behavioral Prep
*   **"Tell me about a time you fixed a hard bug."**
    *   *Tip:* Use your "50+ tickets in under 6 months" experience from Maven Infosoft. Mention a specific time you traced a root cause (e.g., a memory leak or a misconfigured firewall).
*   **"Why SCI?"**
    *   *Answer:* You want to apply your DevOps/Cloud skills to an **On-Premise** educational environment. You use these tools (Jitsi/GitLab) daily as a student and want to contribute to their reliability.

**Cheat Sheet for Tomorrow:**
*   **Video:** UDP, WebRTC, SFU.
*   **Collab:** WebSockets, Operational Transformation.
*   **Server:** Nginx (Reverse Proxy), Docker, Linux Logs.
*   

### 1. APIs (Application Programming Interfaces)
**The Standard:** **REST** (Representational State Transfer) is still king, but knowing **GraphQL** and **gRPC** shows depth.

#### **Key Concepts to Know:**
*   **Restful Maturity (Richardson Maturity Model):**
    *   *Level 0:* The Swamp of POX (Plain Old XML/JSON).
    *   *Level 1:* Resources (using `/users`, `/courses`).
    *   *Level 2:* HTTP Verbs (GET for read, POST for create, PUT/PATCH for update, DELETE for remove). **(Most common industry standard).**
    *   *Level 3:* HATEOAS (Hypermedia As The Engine Of Application State) - The API response includes links to what you can do next.
*   **Idempotency:** A fancy word for "safety." If I send the same API request 10 times, the result on the server should be the same as if I sent it once.
    *   `GET`, `PUT`, `DELETE` = Idempotent.
    *   `POST` = Not Idempotent (sending it 10 times creates 10 resources).
*   **Authentication Standards:**
    *   **OAuth2 / OIDC (OpenID Connect):** The standard for "Log in with Google/GitHub." The university likely uses **SAML** (Shibboleth) for student logins, which is an older XML-based standard, but OIDC is the modern replacement.

#### **Interview Soundbite:**
> *"When designing APIs, I focus on standard HTTP status codes—don't return '200 OK' if the operation failed! I also prefer stateless architectures using JWT (JSON Web Tokens) for authentication so the server doesn't have to store session data in memory, making it easier to scale."*

---

### 2. Networks (The Plumbing)
**The Standard:** The **OSI Model** (Layers 4 and 7) and **DNS**.

#### **Key Concepts to Know:**
*   **Layer 4 vs. Layer 7 Load Balancing:**
    *   **Layer 4 (Transport):** Balances based on IP and Port. It doesn't look at the content. It’s fast.
    *   **Layer 7 (Application):** Balances based on URL, Cookies, or Headers. Smart but slower. (e.g., "Send all requests ending in `.jpg` to the storage server").
*   **DNS (Domain Name System):**
    *   **A Record:** Maps `example.com` $\to$ `192.168.1.1` (IPv4).
    *   **CNAME:** Maps `www.example.com` $\to$ `example.com` (Alias).
    *   **TTL (Time To Live):** How long the DNS info is cached. (Low TTL = easier to switch servers during migration; High TTL = faster lookup).
*   **HTTPS / TLS Handshake:**
    *   You don't need to know the math, but know the flow: *Client Hello* $\to$ *Server Hello (Certificate)* $\to$ *Key Exchange* $\to$ *Encrypted Traffic*.

---

### 3. Data-Driven & Event-Driven Architecture
**The Standard:** Moving from "Request-Response" to "Event-Based" systems.

#### **The Problem:**
In a classic API (Synchronous), Service A calls Service B. If Service B is slow, Service A hangs.

#### **The Solution: Event-Driven (Asynchronous)**
Instead of calling Service B, Service A drops a message into a **Message Queue** (like **RabbitMQ** or **Apache Kafka**).
*   **Producer:** The service creating data (e.g., Student Uploads PDF).
*   **Broker:** The Queue (holds the message safely).
*   **Consumer:** The Worker (picks up the PDF to process it).

**Why use this?**
1.  **Decoupling:** If the Worker crashes, the Queue holds the messages until the Worker comes back online. No data loss.
2.  **Smoothing Bursts:** If 1,000 students upload at once, the queue fills up, but your servers don't crash. They just work through the queue at their own pace.

#### **Interview Soundbite:**
> *"For the E-Learning platform, if we have heavy tasks like video processing, we shouldn't do that synchronously in the web request. We should use a message queue like RabbitMQ to handle it in the background to keep the user interface snappy."*

---

### 4. Servers (The Infrastructure)
**The Standard:** **Linux** is the operating system of the cloud.

#### **Web Servers (The Gatekeepers):**
*   **Nginx:** The industry standard for **Reverse Proxying**. It handles thousands of concurrent connections efficiently because it is **Event-Driven** (asynchronous), unlike Apache which spawns a new process/thread for every user (heavy).
*   **Apache:** Still used often in universities (especially for PHP apps), but Nginx is preferred for performance.

#### **Databases:**
*   **ACID Compliance (SQL):** **Atomicity, Consistency, Isolation, Durability**.
    *   *Example:* When a student registers for a course, you use SQL (PostgreSQL) because you cannot afford to "lose" that data or have it be "mostly" correct.
*   **CAP Theorem (NoSQL):** You can only pick 2: **Consistency**, **Availability**, **Partition Tolerance**.
    *   *Example:* Chat logs (Etherpad) might use NoSQL because it's okay if a message takes 500ms to sync, but the system must never go down.

---

### 5. Open Source Tools (The Toolkit)
*Mentioning these specific tools will resonate with the SCI team.*

| Category | The Industry Standard | What SCI likely uses |
| :--- | :--- | :--- |
| **OS** | Ubuntu / RHEL | **Debian / Ubuntu** (German unis love Debian stable) |
| **Container** | Docker / Kubernetes | **Docker** (almost certainly), maybe K8s for big stuff |
| **CI/CD** | Jenkins / GitHub Actions | **GitLab CI** (Most German unis host their own GitLab) |
| **Monitoring** | Datadog (Paid) | **Prometheus** (Metrics) & **Grafana** (Dashboards) |
| **Logging** | Splunk (Paid) | **ELK Stack** (Elasticsearch, Logstash, Kibana) |
| **Config Mgmt** | Terraform / Ansible | **Ansible** (Great for configuring on-prem servers) |

---

### Summary Checklist for Tomorrow

If they ask you: **"How would you ensure the Jitsi server stays online?"**

1.  **Architecture:** "I'd use a **Load Balancer (Nginx)** in front of multiple Jitsi nodes."
2.  **Monitoring:** "I'd set up **Prometheus** to scrape metrics (CPU, RAM, bandwidth) and **Grafana** to visualize them."
3.  **Alerting:** "I'd configure alerts to Slack/Email if CPU > 80%."
4.  **Resilience:** "I'd use **Docker** to easily restart crashed containers."
5.  **Logs:** "I'd check the logs (`journalctl` or `/var/log`) to find the root cause."

You know this stuff, Jaival. Your profile is impressive. Just connect the dots between "I used AWS" and "I can do the same with Linux servers on-premise."
