# 📘 Introduction to System Design

## 🔹 What is a Large-Scale Distributed System?

A **large-scale distributed system** is a system designed to handle:
- **Huge amounts of data** (e.g., storing the entire world map in Google Maps),
- **Millions of users** accessing it at the same time,
- **High reliability** — it should not crash even under heavy load.

**Example**: *Google Maps*  
It stores huge geographical data, handles millions of users daily, and always needs to stay available.

---



## 🔹 What is a Distributed System?

A **distributed system** means:
- Multiple servers are spread across **different geographic locations**.
- These servers work together to make the system faster, scalable, and fault-tolerant.

Most big tech companies use distributed systems.  
That’s why they value students who know how to **design and build** such systems.

---

## 🔹 What is a Design Pattern?

A **design pattern** is a reusable solution to a common software problem.

**Example**: **Publisher-Subscriber Model**
- One component (Publisher) sends updates.
- Other components (Subscribers) receive those updates when they happen.

---

## 🛠️ What Will We Build?

In this course/notes, we will learn how to design a **live streaming platform** (like **Zoom, Hotstar, or YouTube Live**).  
This will help us understand real-world system design principles like:
- Scalability  
- Load balancing  
- Caching  
- Database sharding  
- Event-driven architecture  
- And more.
