# Pagination

> Part of the **Engineering Mastery** handbook.

## ⏱️ Quick Facts

| | |
|---|---|
| **Read Time** | 10–12 minutes |
| **Difficulty** | 🟢 Beginner |
| **Prerequisites** | REST API Best Practices |

---

## 💡 Why This Matters

Imagine your database contains:

- 100 users
- 10,000 products
- 5 million orders

Should an API return all of them in a single response?

No.

Large responses:

- Slow down the server.
- Increase network usage.
- Consume more memory.
- Create a poor user experience.

Pagination solves this by returning data in smaller, manageable chunks.

---

# What Is Pagination?

**Pagination** is the process of splitting a large dataset into multiple pages.

Instead of returning every record, the API returns only a subset.

Example:

```http
GET /products?page=1&limit=10
```

The response contains only the first 10 products.

---

# How Pagination Works

Suppose a table contains 100 products.

Without pagination:

```text
Request

↓

100 Products Returned
```

With pagination:

```text
Page 1

↓

Products 1–10

----------------

Page 2

↓

Products 11–20

----------------

Page 3

↓

Products 21–30
```

Each request retrieves only the requested page.

---

# Common Query Parameters

Most APIs use:

```http
?page=
```

and

```http
?limit=
```

Example:

```http
GET /products?page=3&limit=20
```

Meaning:

- Page: 3
- 20 items per page

---

# Example Response

```json
{
  "page": 2,
  "limit": 10,
  "total": 56,
  "totalPages": 6,
  "data": [
    ...
  ]
}
```

This gives the client enough information to build pagination controls.

---

# Offset-Based Pagination

This is the most common approach.

```http
GET /products?page=2&limit=10
```

Database concept:

```text
Skip first 10 records

↓

Return next 10
```

Easy to understand and implement.

Suitable for many applications.

---

# Cursor-Based Pagination

Instead of page numbers, the client sends a cursor.

Example:

```http
GET /products?cursor=abc123
```

The server returns the next set of records after that cursor.

Cursor pagination performs better for very large datasets because it avoids skipping large numbers of rows.

---

# Offset vs Cursor

| Offset Pagination | Cursor Pagination |
|-------------------|-------------------|
| Uses page numbers | Uses a cursor/token |
| Easy to implement | Better performance on large datasets |
| Great for admin dashboards | Great for social feeds and timelines |

Choose the approach that matches your application's needs.

---

# Production Example

Imagine an online store with 1 million products.

The homepage requests:

```http
GET /products?page=1&limit=20
```

When the user clicks **Next**:

```http
GET /products?page=2&limit=20
```

Only 20 products are transferred each time, keeping the application responsive.

---

# Best Practices

- Always set a default page size.
- Define a maximum limit (for example, 100 items).
- Return pagination metadata.
- Use consistent parameter names.
- Consider cursor pagination for large or frequently changing datasets.

---

# Common Mistakes

### ❌ Returning every record

Avoid responses that grow without limit.

Always paginate collections that can become large.

---

### ❌ Allowing unlimited limits

Avoid:

```http
GET /products?limit=1000000
```

Set a reasonable maximum to protect your server.

---

### ❌ Omitting metadata

Returning only the data makes it difficult for clients to know whether more pages exist.

Include information such as:

- Current page
- Page size
- Total records
- Total pages

---

# 💡 Did You Know?

Many social media platforms use **cursor-based pagination** instead of page numbers because new posts are constantly being added.

Cursor pagination helps avoid missing or duplicating items while users scroll.

---

# Key Takeaways

- Pagination divides large datasets into smaller pages.
- It improves performance and user experience.
- Offset pagination is simple and widely used.
- Cursor pagination scales better for very large datasets.
- Always return useful pagination metadata.

---

## 🚀 What's Next?

Users often want more than just the next page.

They may want to search, filter, or sort the results.

➡️ **Next Chapter:** Filtering & Sorting