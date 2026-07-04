# HTTP Methods

HTTP methods tell the server **what action the client wants to perform**.

Think of them as verbs in a sentence.

Without methods, every request would look the same, and the server wouldn't know whether you wanted to fetch data, create a new resource, or delete one.

---

## 🧠 Mental Model

Imagine a library.

You can:

- Read a book
- Add a new book
- Update book information
- Remove a book

Each action is different.

HTTP methods work the same way.

---

# Common HTTP Methods

| Method | Purpose | Safe | Idempotent |
|---------|---------|------|------------|
| GET | Retrieve data | ✅ | ✅ |
| POST | Create a resource | ❌ | ❌ |
| PUT | Replace a resource | ❌ | ✅ |
| PATCH | Partially update a resource | ❌ | ❌* |
| DELETE | Remove a resource | ❌ | ✅ |

> *PATCH can be idempotent depending on how it's implemented.

---

# GET

Retrieves data from the server.

Example:

```http
GET /products
```

Typical use cases:

- Product listings
- User profiles
- Search results

A GET request **should not change data**.

---

# POST

Creates a new resource.

Example:

```http
POST /products
```

Request body:

```json
{
  "name": "Laptop",
  "price": 1200
}
```

Typical use cases:

- User registration
- Login
- Creating orders
- Uploading data

---

# PUT

Replaces an existing resource.

Example:

```http
PUT /users/15
```

```json
{
  "name": "John",
  "email": "john@example.com"
}
```

If you're replacing the entire resource, PUT is the conventional choice.

---

# PATCH

Updates only part of a resource.

Example:

```http
PATCH /users/15
```

```json
{
  "email": "new@example.com"
}
```

Only the provided fields are updated.

---

# DELETE

Removes a resource.

Example:

```http
DELETE /products/20
```

Used when a resource should no longer be available.

---

# Safe vs Unsafe Methods

A **safe** method doesn't modify server data.

Examples:

- GET

Unsafe methods can change server state.

Examples:

- POST
- PUT
- PATCH
- DELETE

---

# Idempotent Methods

An **idempotent** request produces the same result even if it's sent multiple times.

Example:

```
DELETE /products/10
```

First request:

```
Product deleted
```

Second request:

```
Product already deleted
```

The final state is still the same.

---

# Production Perspective

A REST API for an online store might look like this:

| Action | Method | Endpoint |
|---------|---------|----------|
| View products | GET | `/products` |
| View one product | GET | `/products/10` |
| Create product | POST | `/products` |
| Update product | PATCH | `/products/10` |
| Delete product | DELETE | `/products/10` |

This consistent pattern makes APIs predictable and easier to use.

---

# Common Mistakes

### ❌ Using GET to delete data

GET should only retrieve data.

---

### ❌ Using POST for every request

POST is useful, but choosing the correct method makes APIs clearer and more maintainable.

---

### ❌ Confusing PUT and PATCH

- PUT replaces an entire resource.
- PATCH updates only specific fields.

---

# Key Takeaways

- HTTP methods describe the client's intent.
- GET retrieves data.
- POST creates resources.
- PUT replaces resources.
- PATCH updates part of a resource.
- DELETE removes resources.
- Choosing the right method improves API design.

---

## 🚀 What's Next?

HTTP methods describe **what** the client wants to do.

Now let's see **how the client sends additional information** with a request.

➡️ **Next:** HTTP Headers