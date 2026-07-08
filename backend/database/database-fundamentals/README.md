# Database Fundamentals

> Part of the **Engineering Mastery** handbook.

## ⏱️ Quick Facts

| | |
|---|---|
| **Read Time** | 10–12 minutes |
| **Difficulty** | 🟢 Beginner |
| **Prerequisites** | Production REST API |

---

## 💡 Why This Matters

Almost every backend application needs to store data.

Think about applications you use every day:

- Social media stores posts and comments.
- E-commerce platforms store products and orders.
- Banking systems store transactions.
- Food delivery apps store restaurants and deliveries.

Without a database, all of this information would disappear whenever the application restarts.

---

# The Problem

Imagine a simple backend application.

```
User

↓

Backend

↓

Memory
```

The backend stores everything in memory.

Example:

```
Users

Alice

Bob

Charlie
```

Now the server restarts.

```
Memory Cleared

↓

Users Lost ❌
```

The application has forgotten everything.

This isn't acceptable for real-world systems.

---

# What Is a Database?

A **database** is a system that stores and organizes data so it can be retrieved, updated, and managed efficiently.

Unlike application memory, a database persists data even after the application stops or restarts.

Think of it as the long-term memory of your application.

---

# How a Database Fits Into a Backend

```
Client
   │
   ▼
Backend API
   │
   ▼
Database
```

The backend acts as the middle layer.

Clients never communicate directly with the database.

Instead:

1. The client sends a request.
2. The backend validates the request.
3. The backend reads or updates the database.
4. The backend returns a response.

---

# What Can a Database Do?

A database allows you to:

- Store data
- Retrieve data
- Update data
- Delete data
- Search records
- Sort records
- Filter records

These operations are commonly known as **CRUD**:

| Operation | Meaning |
|----------|---------|
| Create | Add new data |
| Read | Retrieve data |
| Update | Modify existing data |
| Delete | Remove data |

---

# Real-World Example

Imagine an online bookstore.

When a customer places an order:

```
Customer

↓

Backend

↓

Database

↓

Order Saved
```

Even if the server restarts five minutes later, the order is still available because it was stored in the database.

---

# Production Example

Suppose a user registers.

```
POST /users
```

The backend:

1. Validates the request.
2. Hashes the password.
3. Stores the user in the database.
4. Returns a success response.

When the user logs in a week later, the backend retrieves the stored data from the database.

Without persistent storage, login wouldn't be possible.

---

# Characteristics of a Good Database

A production database should provide:

- Reliable storage
- Fast retrieval
- Data consistency
- Security
- Scalability
- Backup and recovery

Different database systems achieve these goals in different ways.

---

# Where Are Databases Used?

Databases power almost every modern application, including:

- E-commerce platforms
- Banking systems
- Hospital management systems
- Messaging applications
- Streaming services
- Learning platforms

If an application stores information, it almost certainly uses one or more databases.

---

# Best Practices

- Store important data in a database, not application memory.
- Keep the database behind the backend API.
- Regularly back up production data.
- Protect sensitive information with encryption and hashing where appropriate.
- Design your data model carefully before building features.

---

# Common Mistakes

### ❌ Treating memory as permanent storage

Application memory is temporary.

Restarting the server clears it.

---

### ❌ Allowing clients to access the database directly

Clients should communicate with the backend, not the database.

---

### ❌ Ignoring backups

Hardware failures, software bugs, or accidental deletions can happen.

Backups are part of a production-ready system.

---

# 💡 Did You Know?

Large applications often use **multiple databases**.

For example, an e-commerce platform might use one database for customer accounts, another for orders, and another for analytics to improve scalability and reliability.

---

# Key Takeaways

- Databases provide persistent storage.
- They allow applications to create, read, update, and delete data.
- The backend communicates with the database on behalf of clients.
- Persistent storage is essential for real-world applications.
- Almost every backend system relies on one or more databases.

---

## 🚀 What's Next?

Not all databases work the same way.

Some organize data into tables.

Others store flexible documents.

The next chapter compares the two most common approaches.

➡️ **Next Chapter:** SQL vs NoSQL