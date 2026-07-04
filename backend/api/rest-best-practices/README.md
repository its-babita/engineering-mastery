# REST API Best Practices

> Part of the **Engineering Mastery** handbook.

## ⏱️ Quick Facts

| | |
|---|---|
| **Read Time** | 10–12 minutes |
| **Difficulty** | 🟢 Beginner |
| **Prerequisites** | REST API Design |

---

## 💡 Why This Matters

A REST API isn't just about making requests work.

A well-designed API should be:

- Easy to understand
- Predictable
- Consistent
- Easy to maintain
- Friendly for frontend and mobile developers

Good API design reduces bugs, improves developer experience, and makes future development easier.

---

# 1. Use Nouns, Not Verbs

Resources should be represented by **nouns**.

✅ Good

```http
GET    /users
POST   /users
PATCH  /users/1
DELETE /users/1
```

❌ Avoid

```http
/getUsers
/createUser
/deleteUser
/updateUser
```

The HTTP method already describes the action.

---

# 2. Keep URLs Simple

URLs should be easy to read.

✅ Good

```http
/products
/products/10
/orders/25
```

❌ Avoid

```http
/get-all-products-list
/fetchUserInformationById
```

Short, meaningful URLs are easier to remember.

---

# 3. Use Plural Resource Names

Prefer plural names for collections.

✅

```http
/users
/products
/orders
/categories
```

Avoid mixing singular and plural styles.

---

# 4. Use HTTP Methods Correctly

| Method | Purpose |
|---------|---------|
| GET | Read data |
| POST | Create data |
| PUT | Replace data |
| PATCH | Update part of a resource |
| DELETE | Remove data |

Using the correct method makes your API intuitive.

---

# 5. Return Meaningful Status Codes

Don't always return:

```http
200 OK
```

Examples:

```http
201 Created
```

```http
204 No Content
```

```http
400 Bad Request
```

```http
404 Not Found
```

```http
500 Internal Server Error
```

Status codes communicate the outcome before the client even reads the response body.

---

# 6. Keep Response Formats Consistent

Choose one response structure and use it across your API.

Example:

```json
{
  "success": true,
  "data": {
    "id": 1,
    "name": "Alice"
  }
}
```

Error example:

```json
{
  "success": false,
  "message": "User not found"
}
```

Consistency makes frontend code simpler.

---

# 7. Use Meaningful Resource IDs

Instead of:

```http
/users?id=10
```

Prefer:

```http
/users/10
```

The path identifies a specific resource.

Query parameters are better suited for filtering and searching.

---

# 8. Use Query Parameters for Filtering

Examples:

```http
GET /products?category=laptops
```

```http
GET /users?role=admin
```

```http
GET /orders?status=pending
```

This keeps URLs flexible without creating new endpoints.

---

# 9. Version Your APIs

APIs evolve over time.

A common approach is to include the version in the URL.

```http
/api/v1/products
```

When introducing breaking changes, create a new version instead of changing existing behavior unexpectedly.

---

# 10. Write Helpful Error Messages

Instead of:

```json
{
  "error": true
}
```

Prefer:

```json
{
  "success": false,
  "message": "Email is already registered."
}
```

Clear error messages help developers debug faster.

---

# Production Example

A product API might expose:

```http
GET    /api/v1/products
GET    /api/v1/products/15

POST   /api/v1/products

PATCH  /api/v1/products/15

DELETE /api/v1/products/15
```

The naming is:

- Predictable
- Consistent
- Easy to document

---

# Common Mistakes

### ❌ Mixing naming styles

Avoid APIs like:

```http
/users
/getProducts
/orders
/deleteCategory
```

Choose one convention and use it everywhere.

---

### ❌ Returning different response formats

Every endpoint should follow the same response structure.

---

### ❌ Ignoring HTTP status codes

Status codes are part of your API contract.

Clients depend on them.

---

# Key Takeaways

- Design APIs around resources.
- Use nouns in URLs.
- Use the correct HTTP methods.
- Keep response formats consistent.
- Use meaningful status codes.
- Version APIs to support future changes.

---

## 🚀 What's Next?

A production API may contain millions of records.

Returning all of them at once isn't practical.

The next chapter explores how to efficiently return large datasets.

➡️ **Next Chapter:** Pagination