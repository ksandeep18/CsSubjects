# 📘 System Design Notes for Placement (Freshers Edition)

---

## 1. What is System Design?

- System Design is **planning how to build** large, scalable software systems.
- It involves **dividing the system into modules**, **choosing technologies**, and **ensuring performance**.

---

## 2. Basic Steps in System Design

**a) Gather Requirements:**
- Functional Requirements (What the system should do?)
- Non-Functional Requirements (Performance, Scalability, Security)

**Example:**  
For Instagram:
- Upload Photo (functional)
- Low upload time (non-functional)

**b) Estimate Scale:**
- How many users?  
- How much storage needed?  
- How much traffic expected per second?

**Example:**  
WhatsApp:
- Daily Active Users = 500 million+
- Messages per second = very high

**c) Design Database Schema:**
- Identify **Entities** (Tables)
- Relationships (One-to-Many, Many-to-Many)

**d) High Level Architecture:**
- Frontend → Backend → Database → Caching → Load Balancer → Servers

**e) Component Design:**
- Break system into microservices or layers.

**f) Handling Scale:**
- Add Caching, Load Balancing, Sharding, Replication.

---

## 3. Database Design Basics

**a) One-to-Many Relationship:**
- One User → Many Posts

```plaintext
User Table
------------
id | name | email

Post Table
------------
id | user_id | content | created_at
```

**b) Many-to-Many Relationship:**
- Users following other users (Instagram followers)

```plaintext
Followers Table
------------
id | user_id | follower_id
```

**c) Normalization:**
- Remove redundant data by splitting into multiple tables.

---

## 4. Scaling Systems

**a) Vertical Scaling:**
- Adding more RAM, CPU to existing server.

**b) Horizontal Scaling:**
- Adding more servers to handle more load.

> 🎯 Large companies like Netflix, Amazon use horizontal scaling.

---

## 5. Load Balancers

**Definition:**
- Distributes incoming traffic across multiple servers.

**Types:**
- Round Robin
- Least Connection
- IP Hashing

**Example:**  
- Netflix uses load balancers to manage huge numbers of users watching videos at the same time.

---

## 6. Caching

**Why Cache?**
- To reduce database load.
- Serve frequently accessed data quickly.

**Popular Caching Systems:**
- Redis
- Memcached

**Example:**  
- Instagram caches your profile data so opening your profile feels instant.

---

## 7. Stateless vs Stateful Systems

| Feature | Stateless | Stateful |
|:--------|:-----------|:---------|
| Meaning | Server does not store previous session info | Server remembers user session |
| Example | Search Queries | Online Shopping Cart (without login) |

---

## 8. Consistent Hashing

- Distributes data evenly across multiple servers.
- Adding/removing servers causes **minimum disturbance**.

**Example:**  
- Distributed caching in a WhatsApp message system.

---

## 9. CAP Theorem

In Distributed Systems, only **two out of three** are possible:

| Property | Meaning |
|:---------|:--------|
| Consistency | All nodes see the same data at the same time. |
| Availability | Every request gets a response (success/failure). |
| Partition Tolerance | System keeps working even if network failures happen. |

---

## 10. Common Real Life Examples

**a) Instagram Photo Upload Flow:**
1. User uploads photo
2. Backend saves photo into Storage Server (like AWS S3)
3. Metadata (caption, timestamp) is saved into Database
4. Updates cache for quick timeline loading
5. Notifications sent to followers

**b) WhatsApp Messaging System:**
1. User sends message
2. Message stored in database
3. Message pushed to receiver’s phone via queueing system
4. If offline, server stores message until online

**c) Netflix Streaming Flow:**
1. User clicks a movie
2. Request hits load balancer
3. Backend fetches movie metadata
4. Streaming service starts delivering chunks of movie (adaptive bitrate)

---

## 11. Tips for System Design Interviews (For Freshers)

✅ Always ask **clarifying questions**.  
✅ Think about **Scale**: storage, traffic.  
✅ Focus on **Database Schema** first.  
✅ Sketch a **high-level diagram** (Frontend, Backend, Cache, Database).  
✅ Talk about **failure handling** (what if server crashes?).  
✅ Prioritize **simplicity first**, then **optimize**.

---

## 12. Key Technologies to Know

- **Databases**: SQL (PostgreSQL, MySQL), NoSQL (MongoDB)
- **Cache**: Redis, Memcached
- **Load Balancers**: Nginx, HAProxy
- **Storage**: AWS S3, Google Cloud Storage
- **Message Queues**: Kafka, RabbitMQ
- **Scaling Techniques**: Sharding, Replication, Consistent Hashing

---

# 🌟 Summary Mindset for Freshers:

> "Design systems that are simple, scalable, and reliable.  
> Focus first on *what* needs to be built, then *how* to build it."

---

# 📈 Visual: A Simple System Design Template (For Interviews)

```plaintext
1. Functional Requirements
2. Non-Functional Requirements
3. Database Design
4. API Design (optional)
5. High-Level System Diagram
6. Scaling and Caching
7. Failure Handling
8. Final Touches (security, monitoring)
```

---

# ✅ Done!

