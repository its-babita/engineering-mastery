# Entity Relationship (ER) Diagrams

> Part of the **Engineering Mastery** handbook.

**Category:** Database Engineering

## ⏱️ Quick Facts

| | |
|---|---|
| **Read Time** | 8–10 minutes |
| **Difficulty** | 🟢 Beginner |
| **Prerequisites** | Database Relationships |

---

## 💡 Why This Matters

Before writing SQL or creating tables, engineers often design the database visually.

An **Entity Relationship (ER) Diagram** helps you understand:

- What data your application stores
- How tables are connected
- How information flows between entities

Think of it as a blueprint before constructing a building.

---

# What Is an ER Diagram?

An **Entity Relationship (ER) Diagram** is a visual representation of a database.

It shows:

- Entities (tables)
- Attributes (columns)
- Relationships between tables

Instead of reading dozens of SQL statements, you can understand the database structure at a glance.

---

# Main Components

## Entity

An entity represents a table.

Examples:

- Users
- Products
- Orders
- Categories

```
+-----------+
|  Users    |
+-----------+
```

---

## Attribute

Attributes are the columns inside a table.

```
Users

-----------------
ID
Name
Email
Password
```

---

## Relationship

Relationships show how tables connect.

```
Users

↓

Orders
```

One user can place many orders.

---

# Example

Imagine a small online store.

```
Users
+---------+
| id      |
| name    |
| email   |
+---------+
      │
      │ 1
      │
      │
      ▼
Orders
+------------+
| id         |
| user_id    |
| total      |
+------------+
      │
      │ 1
      │
      ▼
Order Items
+--------------+
| order_id     |
| product_id   |
| quantity     |
+--------------+
      │
      │
      ▼
Products
+-------------+
| id          |
| name        |
| price       |
+-------------+
```

Even without SQL, it's easy to understand the relationships.

---

# Why Engineers Use ER Diagrams

ER diagrams help you:

- Plan the database before implementation
- Identify missing relationships
- Reduce duplicate data
- Improve team communication
- Understand existing projects faster

They're useful during both development and code reviews.

---

# Real-World Example

Suppose you're building a Hostel Finder application.

Your main entities might be:

```
Students

↓

Bookings

↓

Hostels

↓

Rooms
```

Looking at the diagram immediately answers questions like:

- Can one hostel have multiple rooms?
- Can one student have multiple bookings?
- Which table stores room information?

---

# Production Example

A food delivery platform could have:

```
Customers

↓

Orders

↓

Restaurants

↓

Menu Items

↓

Payments
```

Before a single table is created, the engineering team reviews the ER diagram to ensure the design matches the business requirements.

---

# Best Practices

- Start with the main business entities.
- Keep names simple and consistent.
- Show relationships clearly.
- Review the diagram before creating tables.
- Update the diagram when the database evolves.

---

# Common Mistakes

### ❌ Creating tables before designing

A few minutes spent designing can save hours of refactoring later.

---

### ❌ Adding every possible detail

An ER diagram should explain the structure, not every implementation detail.

---

### ❌ Ignoring business rules

A database should reflect how the business actually works.

---

# 💡 Engineering Insight

In many engineering teams, database discussions begin with an ER diagram—not SQL.

It's much easier to review a visual model than hundreds of lines of migration scripts.

---

# Key Takeaways

- ER diagrams visualize a database.
- They show entities, attributes, and relationships.
- They're useful for planning and communication.
- Good diagrams make database design easier.
- A clear ER diagram often leads to a cleaner database.

---

## 🚀 What's Next?

Designing a good database is only half the challenge.

As your data grows, finding information quickly becomes essential.

The next chapter explores how databases use **Indexes** to speed up queries.