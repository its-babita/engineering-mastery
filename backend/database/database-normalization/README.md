# Database Normalization

> Part of the **Engineering Mastery** handbook.

**Category:** Database Engineering

## ⏱️ Quick Facts

| | |
|---|---|
| **Read Time** | 12–15 minutes |
| **Difficulty** | 🟢 Beginner |
| **Prerequisites** | SQL vs NoSQL |

---

## 💡 Why This Matters

Imagine an online store with 10,000 orders.

If every order stores the customer's:

- Name
- Email
- Phone
- Address

...the same information is duplicated thousands of times.

Now imagine the customer changes their phone number.

How many rows need updating?

Potentially thousands.

Normalization solves this problem.

---

# What Is Database Normalization?

**Normalization** is the process of organizing data to:

- Reduce duplication
- Improve consistency
- Simplify updates
- Maintain data integrity

The goal is simple:

> **Store each piece of information only once whenever practical.**

---

# The Problem

Suppose we store orders like this:

| Order ID | Customer | Email | Product |
|----------|----------|--------|---------|
| 101 | Alice | alice@example.com | Laptop |
| 102 | Alice | alice@example.com | Mouse |
| 103 | Alice | alice@example.com | Keyboard |

The same customer information is repeated in every row.

Problems:

- Wasted storage
- Harder updates
- Greater chance of inconsistent data

---

# A Better Design

Instead, separate the data.

### Customers

| ID | Name | Email |
|----|------|--------|
| 1 | Alice | alice@example.com |

### Orders

| Order ID | Customer ID | Product |
|----------|-------------|---------|
| 101 | 1 | Laptop |
| 102 | 1 | Mouse |
| 103 | 1 | Keyboard |

Customer information is stored once.

Orders reference the customer using an ID.

---

# Benefits

Suppose Alice changes her email.

Without normalization:

```
Update

↓

Order 101

↓

Order 102

↓

Order 103
```

With normalization:

```
Update

↓

Customers Table

↓

Done ✅
```

One update instead of many.

---

# Normal Forms (Simplified)

You don't need to memorize every normal form.

Understanding the purpose is more important.

## First Normal Form (1NF)

Each column should contain a single value.

✅ Good

| ID | Skills |
|----|--------|
| 1 | JavaScript |

❌ Avoid

| ID | Skills |
|----|--------|
| 1 | JavaScript, TypeScript, Go |

---

## Second Normal Form (2NF)

Store data where it logically belongs.

Avoid repeating information across multiple records.

---

## Third Normal Form (3NF)

Columns should depend on the primary key, not on other non-key columns.

In practice:

Keep unrelated information in separate tables.

---

# Real-World Example

Think about a university.

Instead of storing a professor's details in every student record:

```
Students

↓

Professor ID

↓

Professors
```

The professor's information exists only once.

---

# Production Example

An e-commerce database might have:

```
Customers

↓

Orders

↓

Order Items

↓

Products
```

Each table has a specific responsibility.

Relationships connect them together.

This design is easier to maintain as the application grows.

---

# When Not to Normalize

Normalization isn't always the best choice.

Sometimes a small amount of duplication is acceptable to improve performance.

This is called **denormalization**.

We'll explore it later when discussing database optimization.

---

# Best Practices

- Avoid unnecessary duplication.
- Store related information in separate tables.
- Use IDs to connect related data.
- Keep each table focused on one purpose.
- Normalize first, optimize later.

---

# Common Mistakes

### ❌ Repeating the same information everywhere

Duplicate data increases maintenance and the risk of inconsistencies.

---

### ❌ Creating one massive table

Large tables containing unrelated data become difficult to manage.

---

### ❌ Over-normalizing small projects

For simple applications, excessive normalization can make queries harder to understand.

Find a practical balance.

---

# 💡 Engineering Insight

Normalization is about **data quality**, not just saving storage.

Consistent data is easier to maintain, debug, and scale than duplicated data.

---

# Key Takeaways

- Normalization reduces data duplication.
- Related data should be stored in separate tables.
- IDs connect records across tables.
- Good database design improves consistency and maintainability.
- Normalize first; optimize later if needed.

---

## 🚀 What's Next?

Normalization introduces the idea of connecting tables.

The next chapter explores the keys that make those relationships possible.

➡️ **Next Chapter:** Primary Keys & Foreign Keys