# Primary Keys & Foreign Keys

> Part of the **Engineering Mastery** handbook.

**Category:** Database Engineering

## ⏱️ Quick Facts

| | |
|---|---|
| **Read Time** | 10–12 minutes |
| **Difficulty** | 🟢 Beginner |
| **Prerequisites** | Database Normalization |

---

## 💡 Why This Matters

Imagine an e-commerce application.

A customer places an order.

How does the database know **which customer owns that order?**

The answer is simple:

It connects records using **keys**.

Without keys:

- Relationships break.
- Duplicate records increase.
- Data becomes inconsistent.

---

# What Is a Primary Key?

A **Primary Key (PK)** is a column that uniquely identifies each record in a table.

Every row must have a unique primary key.

Example:

### Users

| ID | Name |
|----|------|
| 1 | Alice |
| 2 | Bob |
| 3 | Charlie |

Here:

```
ID
```

is the Primary Key.

No two users can have the same ID.

---

# Characteristics of a Primary Key

A Primary Key should be:

- Unique
- Not empty (`NULL`)
- Stable (shouldn't change frequently)

Good examples:

- User ID
- Product ID
- Order ID

Avoid using values like email addresses as primary keys because they can change.

---

# What Is a Foreign Key?

A **Foreign Key (FK)** is a column that references the Primary Key of another table.

It creates a relationship between tables.

Example:

### Users

| ID | Name |
|----|------|
| 1 | Alice |
| 2 | Bob |

### Orders

| Order ID | User ID | Product |
|----------|---------|---------|
| 101 | 1 | Laptop |
| 102 | 1 | Mouse |
| 103 | 2 | Keyboard |

Here:

```
User ID
```

inside the **Orders** table is a Foreign Key.

It points to the **Users** table.

---

# How They Work Together

```
Users
+-----------+
| ID | Name |
+-----------+
| 1  | Alice|
| 2  | Bob  |
+-----------+
      ▲
      │
      │ Foreign Key
      │
Orders
+-------------------------+
| Order | User ID | Item  |
+-------------------------+
| 101   | 1       | Laptop|
| 102   | 2       | Mouse |
+-------------------------+
```

The database knows:

- Order **101** belongs to Alice.
- Order **102** belongs to Bob.

---

# Why Use Foreign Keys?

Foreign Keys help:

- Maintain relationships
- Prevent invalid references
- Improve data integrity

For example, an order shouldn't reference a customer who doesn't exist.

---

# Referential Integrity

Foreign Keys enforce **referential integrity**.

That means every Foreign Key value must reference a valid Primary Key.

Example:

```
Users

ID = 1
ID = 2
```

Valid:

```
Order

User ID = 2 ✅
```

Invalid:

```
Order

User ID = 99 ❌
```

The database can reject invalid relationships.

---

# Real-World Example

Think of a library.

### Books

| Book ID | Title |
|----------|-------|
| 1 | Clean Code |
| 2 | Design Patterns |

### Borrow Records

| Borrow ID | Book ID |
|------------|---------|
| 10 | 1 |
| 11 | 2 |

The **Book ID** connects each borrow record to a book.

---

# Production Example

An online store may contain:

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
```

Each table has its own Primary Key.

Relationships are created using Foreign Keys.

This structure keeps the data organized and consistent.

---

# Best Practices

- Every table should have a Primary Key.
- Use Foreign Keys to represent relationships.
- Prefer numeric or UUID-based IDs for primary keys.
- Keep Primary Keys stable.
- Let the database enforce referential integrity.

---

# Common Mistakes

### ❌ Using names as identifiers

Names aren't guaranteed to be unique.

Use IDs instead.

---

### ❌ Ignoring Foreign Keys

Without Foreign Keys, relationships can become inconsistent.

---

### ❌ Updating Primary Keys frequently

Primary Keys should remain stable because other tables depend on them.

---

# 💡 Engineering Insight

A relational database isn't just a collection of tables.

It's a network of related data.

Primary Keys identify records.

Foreign Keys connect them.

Together, they form the foundation of relational database design.

---

# Key Takeaways

- A Primary Key uniquely identifies a record.
- A Foreign Key connects one table to another.
- Foreign Keys enforce valid relationships.
- Primary Keys should be unique and stable.
- Relationships are what make relational databases powerful.

---

## 🚀 What's Next?

Finding a record by scanning millions of rows is slow.

The next chapter explores how databases locate data efficiently using **Indexes**.

➡️ **Next Chapter:** Indexes