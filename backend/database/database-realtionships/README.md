# Database Relationships

> Part of the **Engineering Mastery** handbook.

**Category:** Database Engineering

## ⏱️ Quick Facts

| | |
|---|---|
| **Read Time** | 10–12 minutes |
| **Difficulty** | 🟢 Beginner |
| **Prerequisites** | Primary & Foreign Keys |

---

## 💡 Why This Matters

Applications rarely store isolated data.

Consider an online store:

- A customer places many orders.
- An order contains many products.
- A product belongs to a category.

These connections are called **relationships**.

Understanding relationships is essential for designing a good database.

---

# What Is a Database Relationship?

A relationship describes how records in one table are connected to records in another table.

Think of relationships as links between tables.

```
Customers

↓

Orders

↓

Products
```

Without relationships, data becomes duplicated and difficult to manage.

---

# One-to-One (1:1)

One record is related to exactly one other record.

Example:

```
User

↓

User Profile
```

Each user has one profile.

Each profile belongs to one user.

```
Users
+----+-------+
| ID | Name  |
+----+-------+
| 1  | Alice |
+----+-------+

Profiles
+----+---------+
| ID | User ID |
+----+---------+
| 1  | 1       |
+----+---------+
```

---

# One-to-Many (1:N)

One record is related to many records.

This is the most common relationship.

Example:

```
Customer

↓

Orders
```

One customer can place many orders.

Each order belongs to one customer.

```
Customer

↓

Order 1

Order 2

Order 3
```

---

# Many-to-Many (N:M)

Many records relate to many other records.

Example:

Students and Courses.

```
Student A

↓

Math

Science

Student B

↓

Science

History
```

A student can enroll in many courses.

A course can have many students.

This relationship usually requires a **junction table**.

```
Students

↓

Enrollments

↓

Courses
```

---

# Junction Table

Instead of connecting tables directly:

```
Students

×

Courses
```

Use an intermediate table.

```
Students

↓

Enrollments

↓

Courses
```

Example:

| Student ID | Course ID |
|------------|-----------|
| 1 | 2 |
| 1 | 3 |
| 2 | 1 |

This keeps the design flexible and scalable.

---

# Real-World Examples

| Relationship | Example |
|--------------|---------|
| 1:1 | User → Profile |
| 1:N | Customer → Orders |
| N:M | Students ↔ Courses |
| N:M | Products ↔ Categories (depending on design) |
| 1:N | Blog → Comments |

---

# Production Example

An e-commerce application might have:

```
Customers
      │
      ▼
Orders
      │
      ▼
Order Items
      │
      ▼
Products
      │
      ▼
Categories
```

Every relationship models how the business works.

---

# Best Practices

- Design relationships based on real business rules.
- Use Foreign Keys to enforce relationships.
- Use junction tables for many-to-many relationships.
- Avoid unnecessary duplication.
- Keep relationships simple and meaningful.

---

# Common Mistakes

### ❌ Storing repeated information

Use relationships instead of copying data across tables.

---

### ❌ Ignoring business rules

The database should reflect how the real world works.

---

### ❌ Creating unnecessary many-to-many relationships

Use them only when both sides genuinely need multiple connections.

---

# 💡 Engineering Insight

Good database design isn't about creating more tables.

It's about modeling real-world relationships accurately.

When your data model reflects the business domain, your application becomes easier to understand and maintain.

---

# Key Takeaways

- Relationships connect tables.
- One-to-One links one record to one record.
- One-to-Many is the most common relationship.
- Many-to-Many requires a junction table.
- Well-designed relationships reduce duplication and improve consistency.

---

## 🚀 What's Next?

Now that we understand relationships, it's time to visualize them.

➡️ **Next Chapter:** Entity Relationship Diagrams (ER Diagrams)