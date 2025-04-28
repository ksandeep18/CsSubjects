# 📚 Databases In Depth

## 🌐 Client and Network Layer Relation
- When a **client** (user or application) wants to use a **database**, they **send a request** (usually a query like SQL) over a **network**.
- The **network layer** handles transferring this request **securely and reliably** to the **database server**.

**Example:**  
A user sends a `SELECT * FROM users;` query from their laptop. The network layer transports this query to the database server.

---

## 🛠 1st Component: Frontend of Database

The **frontend** is the part of a database that **understands the user's query** and **prepares it for execution**.

### It includes:

- **Tokenizer**  
  - **Definition:** Breaks down the SQL query into **small pieces** called **tokens**.
  - **Example:**  
    Query: `SELECT name FROM users;` → Tokens: `SELECT`, `name`, `FROM`, `users`, `;`

- **Parser**  
  - **Definition:** **Checks query validity** (grammar and structure) and **builds a syntax tree**.
  - **Example:**  
    Parser confirms "SELECT name FROM users;" is a correct query.

- **Optimizer**  
  - **Definition:** **Finds the best and fastest way** to run the query.
  - **Example:**  
    Decides whether to scan the whole table or use an index.

- **Bytecode/Operations**  
  - **Definition:** Converts the optimized query plan into **low-level operations** (like scan, filter).

---

## ⚙️ 2nd Component: Execution Engine

The **execution engine** **runs the query** based on the frontend's output.

### It includes:

- **Query Executor**  
  - **Definition:** **Performs operations** like scanning tables, applying filters, and fetching results.

- **Cache Manager**  
  - **Definition:** **Stores recently accessed data** to quickly respond to repeated queries.

- **Utility Services**  
  - **Definition:** Handles **authentication (oAuth, passwords)**, **backup**, **restore**, and **user management**.

---

## 🔒 3rd Component: Transaction, Lock, and Recovery Managers

Responsible for **safety, locking, and recovery**.

- **Transaction Manager**  
  - **Definition:** Manages **start, commit, and rollback** of transactions.
  - **Example:** Ensures full money transfer between two accounts.

- **Lock Manager**  
  - **Definition:** Controls **access to data** to avoid conflicts.
  - **Example:** Prevents two users from editing the same data simultaneously.

- **Recovery Manager**  
  - **Definition:** **Restores database** after crashes or failures.
  - **Example:** Rolls back incomplete transactions after a server crash.

**Issues faced:**
- Deadlocks
- Inconsistent data if recovery fails

---

## 🔄 4th Component: Concurrency Manager

- **Definition:** Manages **multiple transactions running at once** without errors.
- **Relation:** Works **with Transaction Manager and Lock Manager** for safe parallelism.

**Example:**  
Two users trying to book the last movie ticket — only one should succeed.

---

## 🌍 5th Component: Distributed System Managers

Handles databases spread across **multiple servers**.

- **Shard Manager**  
  - **Definition:** Divides database into **smaller parts (shards)** across servers.
  - **Example:** Users 'A-M' on server 1, 'N-Z' on server 2.

- **Cluster Manager**  
  - **Definition:** Manages **multiple servers as one database**.

- **Replication Manager**  
  - **Definition:** **Copies data** across servers for **backup and high availability**.

---

## 💾 6th Component: Storage Engine

Handles **saving and retrieving data** from disk.

- **Disk Storage Manager**
  - **Definition:** Stores data smartly using structures like:
    - **LSM Trees:** Best for **heavy writes**.
    - **B-Trees:** Best for **fast reads**.
    - **Indexing:** Helps in **quick lookups**.

- **Buffer Manager**
  - **Definition:** Manages **data movement** between disk and memory.
  - **Difference from Cache Manager:**  
    - **Cache Manager:** Caches query results.  
    - **Buffer Manager:** Handles low-level disk page reads/writes.

- **Index Manager**
  - **Definition:** Maintains **indexes** for fast data access.

- **Caching Mechanisms (Basics):**
  - **Page Caching:** Stores disk pages in memory.
  - **Query Caching:** Stores query outputs for reuse.

---

## 🖥 7th Component: OS Interaction Layer

- **Definition:** Interacts with the **Operating System** using **system calls**.
- **System Calls:**  
  Special requests like **read/write files**, **allocate memory**, **open network connections**.

**Difference:**  
Database engines make **high-level data requests**, while OS translates them into **hardware operations**.

---

# ⚖️ Scalability vs Availability Trade-off

- **Scalability:** Database's ability to handle **increasing load** by adding more resources.
- **Availability:** Database's ability to stay **online and accessible**.

**Trade-off:**  
Often, making a system more scalable can affect its availability and vice-versa, especially in distributed systems.

---

# 🔁 Revision: How the Client Talks to Database (Sequence of 7 Components)

1. Client sends query via network.
2. **Frontend** processes query (Tokenizer → Parser → Optimizer).
3. **Execution Engine** runs the operations.
4. **Transaction Manager** ensures transaction safety.
5. **Concurrency Manager** ensures safe parallelism.
6. **Storage Engine** saves/fetches actual data.
7. **OS Layer** handles low-level system interactions.

---

# 🔗 Extra Important Points

- **Concurrency Manager + Lock Manager:**
  - Work together to ensure **parallel operations are safe** without deadlocks.

- **Recovery Manager:**
  - Handles **rollback and database restoration** after crashes.

- **MVCC (Multi-Version Concurrency Control):**
  - **Definition:** Maintains **multiple versions** of data.
  - **Benefit:** Reads don't block writes and writes don't block reads.

**Example:**  
When a user reads a row, they get an **old stable version**, even if another transaction is updating it at the same time.

---

# ✅ Summary Table

| Component | Main Job | Example |
|:---|:---|:---|
| Frontend | Understands query | Tokenizes, Parses, Optimizes |
| Execution Engine | Runs query | Executes "SELECT * FROM users" |
| Transaction + Lock + Recovery Managers | Safe transactions | Bank transfer, crash recovery |
| Concurrency Manager | Parallel safe operations | Multiple users booking tickets |
| Shard/Cluster/Replication Managers | Distributed databases | Spreading data across servers |
| Storage Engine | Saves data smartly | B-trees, LSM trees |
| OS Interaction Layer | Talks to operating system | Reading disk blocks |
