
# 🎯 Part 2: Aim of System Design – Defining Requirements & Building the System

## 🔹 1. Understanding the Aim

The **product manager** defines what the user wants by analyzing data and usage patterns.  
From that, the team identifies the **most important features** to focus on first.

**Example**:  
In a video streaming platform:
- **Primary feature**: Playing the video (even in 480p).
- **Secondary feature**: HD quality or auto-resolution switch.

> If the user can’t see the video at all, HD doesn’t matter. So we build **critical features first**.

---

## 🔹 2. Prioritize Stability Before Features

Before adding fancy features, we must ensure:
- The **server doesn't go down**.
- The system is **always available**.

> A great feature is useless if the system crashes.

---

## 🔹 3. From Features to Architecture

Once features are identified, the process flows like this:

```
User Requirements → Abstract Concepts → Data Definitions → Object Design → Database Schema → APIs
```

### ➤ Step-by-Step:
1. **Features**: Define what the user can do.
2. **Abstract Concepts**: E.g., a "Video" or "User" is a high-level concept.
3. **Data Definitions**: What data is needed for each concept (e.g., title, duration for a video).
4. **Object Design**: Convert these into software objects/classes.
5. **Database Design**: Define tables and relationships.
6. **API Endpoints**: Build backend APIs to allow frontend to interact with the system.

---

## 🔹 4. Handling Load with Partitioning

We must ensure the system doesn't fail even when traffic spikes.

**Example**:  
If 10 million users watch videos at the same time:
- One server can’t handle all.
- So, we **partition the load across multiple servers** using techniques like:
  - Load balancers
  - Database sharding
  - Caching (e.g., Redis)

---

## 🔹 5. Extensibility (Design for the Future)

Build the system so that **new features can be added easily**.

**Example**:  
Suppose we build a basic video player first.  
Later, we may want to add:
- Live chat
- Subtitles
- Multiple audio tracks

If the system is extensible, we can add these **without breaking the existing code**.

---

## 🔹 6. Testing the System

Always test for:
- **Functionality**: Does everything work as expected?
- **Load**: Can it handle many users at once?
- **Edge Cases**: What happens if a video fails to load?

**Example**:  
- Simulate 1 million users watching at the same time.
- Force a server failure and check if backup servers take over.

---

## ✅ Summary

System design begins with understanding **what users really need**, and ends with building a **stable, scalable, and extensible** product.  
Everything in between — data, objects, APIs, databases — must support this goal.
