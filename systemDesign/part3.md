
# 🛠️ Part 3: Designing the System – Requirements and Engineering Thinking

## 🔹 1. Functional & Non-Functional Requirements

Before designing, we must clearly define **what the system should do** (functional) and **how well it should do it** (non-functional).

### ➤ Functional Requirements:
- **Stream video in real-time** (live IPL match)
- **Process video** (compress, encode)
- **Broadcast to millions of users**
- **Support advertisements**
- **Show real-time reactions (likes, hearts)**
- **Display disclaimers or news flashes**
- **Auto-degrade video quality based on network**

### ➤ Non-Functional Requirements:
- **Failproof design** – Must continue even if parts fail
- **Scalable** – Handle millions of users at once
- **Secure** – Prevent hacking or code injection

---

## 🔹 2. Example Scenario – IPL Match in 8K

Imagine you're **shooting a live IPL match in 8K resolution**.  
Your users should:
- Get the stream in real-time.
- Never see any buffering or lag.
- Not worry **how** it’s delivered. It’s a **black box** for them.

> As engineers, we **hide the internal complexity** and just provide a clean **API**.

---

## 🔹 3. Think in Terms of APIs and Objects

You expose an **API** that the frontend or app team uses:
- This API returns objects like `videoFeed`, `timestamp`, `resolution`, `viewerCount`, etc.
- Internally, we handle all compression, failovers, streaming protocols, and CDNs.

---

## 🔹 4. Methods vs. APIs

| Feature     | Methods                            | APIs                                     |
|-------------|------------------------------------|------------------------------------------|
| Called via  | Inside program                     | Over network (HTTP, gRPC, WebSocket)     |
| Usage       | Function in code                   | Interface between services/systems       |
| Scope       | Internal to app                    | External, connects different services     |
| Example     | `playVideo()` in code              | `GET /stream?id=123` HTTP API            |

---

## 🔹 5. Engineering for Failure

A good system design **assumes things will go wrong**.  
We must prepare for all types of failures:

| Failure Type | Example Scenario |
|--------------|------------------|
| Database crash | Users can’t comment or view new videos |
| Firewall blocks requests | App becomes unreachable from outside |
| Hacker changes logic | Wrong video shown, or privacy breach |
| Disk full | Server can’t store or buffer new data |
| CDN outage | Users get slow or broken streams |

---

### ✅ Solution Strategies:
- Use **replicated databases**.
- Set up **health checks** and **auto-restarts**.
- Use **firewall rules + monitoring**.
- **Rollback and versioning** of code.
- Use **distributed systems** so that failure of one server doesn’t stop the entire system.

---

## 🧠 Summary

Designing a large system like live streaming:
- Starts from **clear requirements**.
- Requires **abstracting complexity behind APIs**.
- Needs careful thought on **how to handle failures**.
- Aims for a **smooth user experience**, no matter how complex things are behind the scenes.
"""
