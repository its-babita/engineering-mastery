# SQL vs NoSQL

> Part of the **Engineering Mastery** handbook.

## ⏱️ Quick Facts

| | |
|---|---|
| **Read Time** | 12–15 minutes |
| **Difficulty** | 🟢 Beginner |
| **Prerequisites** | Database Fundamentals |

---

## 💡 Why This Matters

Not every application stores data in the same way.

Consider these examples:

- 🏦 A banking system
- 🛒 An e-commerce platform
- 💬 A chat application
- 📷 A social media platform

Although they all store data, their requirements are different.

Choosing the right database can improve performance, scalability, and maintainability.

---

# The Two Major Database Families

Most modern databases fall into two categories:

## SQL Databases

Store data in **tables**.

Example:

| id | name | email |
|----|------|--------|
| 1 | Alice | alice@example.com |
| 2 | Bob | bob@example.com |

Data follows a predefined structure called a **schema**.

---

## NoSQL Databases

Store data in different formats depending on the database type.

A document database may store data like this:

```json
{
  "id": 1,
  "name": "Alice",
  "email": "alice@example.com"
}
```

Different records can have different fields if needed.

---

# SQL Databases

Popular examples:

- PostgreSQL
- MySQL
- SQLite
- Microsoft SQL Server

They organize information into related tables.

Example:

```
Users Table

↓

Orders Table

↓

Products Table
```

Relationships between tables are a key strength of SQL databases.

---

# NoSQL Databases

Popular examples:

- MongoDB
- Cassandra
- Redis
- DynamoDB

They are designed for different types of data and workloads.

Not every NoSQL database works the same way.

Some store:

- Documents
- Key-value pairs
- Graphs
- Wide-column data

---

# SQL vs NoSQL

| SQL | NoSQL |
|------|--------|
| Table-based | Multiple data models |
| Fixed schema | Flexible schema |
| Excellent for relationships | Excellent for flexible or rapidly changing data |
| Strong consistency | Depends on the database |

Neither approach is universally better.

---

# Real-World Example

### Online Banking

A money transfer must be accurate.

```
Account A

↓

Transfer

↓

Account B
```

Losing or duplicating a transaction is unacceptable.

SQL databases are commonly chosen for these scenarios because they provide strong consistency and transactional guarantees.

---

### Social Media

A user profile may include:

- Name
- Bio
- Photos
- Interests
- Links

Different users may have different profile information.

A document database can make this kind of evolving data easier to manage.

---

# Production Example

A large application may use multiple databases.

Example:

| Data | Database Type |
|------|---------------|
| Users | SQL |
| Orders | SQL |
| Product Catalog | SQL or NoSQL |
| Cache | Redis |
| Analytics | NoSQL |

This approach is called **polyglot persistence**—using different databases for different jobs.

---

# When to Choose SQL

SQL databases are often a good choice when:

- Data has clear relationships.
- Transactions must be reliable.
- Data consistency is critical.
- Reporting and complex queries are important.

Examples:

- Banking
- E-commerce
- Payroll
- Inventory systems

---

# When to Choose NoSQL

NoSQL databases are often a good choice when:

- Data structure changes frequently.
- Large-scale horizontal scaling is important.
- Flexible document structures are useful.
- Extremely high read/write throughput is required.

Examples:

- Chat applications
- Content management systems
- Logging platforms
- User activity feeds

---

# Best Practices

- Start with your application's requirements, not database popularity.
- Understand your data model before choosing a database.
- Use the simplest solution that meets your needs.
- Avoid switching databases without a strong reason.
- Don't hesitate to use multiple databases when appropriate.

---

# Common Mistakes

### ❌ SQL is outdated

SQL databases continue to power many of the world's largest applications.

---

### ❌ NoSQL is always faster

Performance depends on the workload, schema, indexes, and queries—not just the database type.

---

### ❌ One database fits every problem

Different problems often require different storage solutions.

---

# 💡 Engineering Insight

Experienced engineers don't ask:

> "Which database is the best?"

They ask:

> "Which database best fits this problem?"

The right choice depends on your application's requirements.

---

# Key Takeaways

- SQL and NoSQL solve different problems.
- SQL excels at structured, relational data.
- NoSQL offers flexibility for many modern workloads.
- Many production systems use both.
- Choose based on requirements, not trends.

---

## 🚀 What's Next?

Before designing tables, it's important to understand how relational databases organize information.

The next chapter introduces **Database Normalization**, a technique for reducing duplication and improving data consistency.

➡️ **Next Chapter:** Database Normalization