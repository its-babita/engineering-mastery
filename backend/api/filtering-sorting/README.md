# Filtering & Sorting

> Part of the **Engineering Mastery** handbook.

## ⏱️ Quick Facts

| | |
|---|---|
| **Read Time** | 10–12 minutes |
| **Difficulty** | 🟢 Beginner |
| **Prerequisites** | Pagination |

---

## 💡 Why This Matters

Imagine an online store with:

- 50,000 products
- 500 categories
- Thousands of customers

No user wants to browse every product.

Instead, they want to:

- Search for laptops
- Filter by category
- Show only in-stock items
- Sort by price
- View the newest products first

A good API makes all of this possible without creating dozens of endpoints.

---

# What Is Filtering?

**Filtering** returns only the records that match specific conditions.

Example:

```http
GET /products?category=laptops
```

Instead of returning every product, the API returns only laptops.

---

# Common Filtering Examples

Filter by category:

```http
GET /products?category=electronics
```

Filter by status:

```http
GET /orders?status=completed
```

Filter by role:

```http
GET /users?role=admin
```

Filter by availability:

```http
GET /products?inStock=true
```

Each filter narrows the result set.

---

# Multiple Filters

Filters can be combined.

```http
GET /products?category=laptops&brand=Dell&inStock=true
```

The API returns only products that satisfy **all** conditions.

This keeps your API flexible without creating new endpoints.

---

# What Is Sorting?

**Sorting** controls the order of returned data.

Examples:

- Lowest price first
- Highest rating first
- Newest products first
- Alphabetical order

---

# Common Sorting Examples

Sort by price:

```http
GET /products?sort=price
```

Sort by newest:

```http
GET /products?sort=createdAt
```

Sort descending:

```http
GET /products?sort=-price
```

A common convention is:

- `price` → Ascending
- `-price` → Descending

Document whichever format your API uses and keep it consistent.

---

# Combining Pagination, Filtering, and Sorting

A production API often combines all three.

Example:

```http
GET /products?page=2&limit=20&category=laptops&sort=-price
```

This request means:

- Page 2
- 20 products
- Category = laptops
- Highest price first

One endpoint can support many use cases.

---

# Example Response

```json
{
  "page": 2,
  "limit": 20,
  "total": 128,
  "data": [
    {
      "id": 101,
      "name": "Laptop Pro",
      "price": 1499
    }
  ]
}
```

The response format remains the same regardless of how the data was filtered or sorted.

---

# Production Example

Imagine an e-commerce homepage.

The frontend requests:

```http
GET /products?category=phones&sort=-rating&page=1&limit=12
```

The backend:

1. Filters products by category.
2. Sorts them by rating (highest first).
3. Returns the first 12 results.

The frontend doesn't need multiple endpoints like:

```text
/top-rated-phones
/new-phones
/cheap-phones
```

One flexible endpoint is enough.

---

# Best Practices

- Use query parameters for filtering and sorting.
- Keep parameter names consistent.
- Support combining multiple filters.
- Validate user input before querying the database.
- Document supported filters and sort fields.

---

# Common Mistakes

### ❌ Creating a new endpoint for every filter

Avoid:

```http
/products/electronics
/products/books
/products/furniture
```

A single endpoint with query parameters is easier to maintain.

---

### ❌ Allowing sorting on every database field

Only allow sorting by fields that make sense and are indexed when appropriate.

---

### ❌ Using inconsistent parameter names

Avoid switching between:

```text
sortBy
order
direction
sortField
```

Choose one style and use it consistently.

---

# 💡 Did You Know?

Many modern APIs support filtering by multiple fields, but they also place limits on which fields can be filtered or sorted to protect performance and prevent expensive database queries.

---

# Key Takeaways

- Filtering narrows the result set.
- Sorting changes the order of results.
- Query parameters make APIs flexible.
- Pagination, filtering, and sorting work together.
- One well-designed endpoint is better than many specialized endpoints.

---

## 🚀 What's Next?

Even a well-designed API must protect itself from invalid input.

The next chapter explores how to validate incoming requests before processing them.

➡️ **Next Chapter:** Request Validation