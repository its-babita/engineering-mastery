# REST API Design

> Part of the **Engineering Mastery** handbook.

## ⏱️ Quick Facts

| | |
|---|---|
| **Read Time** | 12–15 minutes |
| **Difficulty** | 🟢 Beginner |
| **Prerequisites** | HTTP, HTTP Methods, Authentication |

---

## 📍 Where We Are in the Backend Journey

```text
Networking ✅
      ↓
Authentication ✅
      ↓
REST API Design ← You are here
      ↓
API Best Practices
      ↓
Validation
      ↓
Error Handling
```

---

## Imagine This...

Imagine you're visiting a restaurant.

You don't walk into the kitchen and cook your own food.

Instead:

```
Customer
      │
      ▼
Menu
      │
      ▼
Place Order
      │
      ▼
Kitchen
      │
      ▼
Food Returned
```

The menu is the only way customers interact with the kitchen.

A REST API works the same way.

The **client never interacts directly with the database**.

It communicates through well-defined API endpoints.

---

# 💡 Why This Matters

Modern applications rarely work alone.

A backend often serves multiple clients:

- Web applications
- Mobile apps
- Smart TVs
- Desktop applications
- Third-party integrations

A REST API provides a consistent way for all of them to communicate with the backend.

---

# What Is REST?

**REST (Representational State Transfer)** is an architectural style for designing web APIs.

REST is not:

- A programming language
- A framework
- A library

Instead, it's a set of design principles for building scalable and predictable APIs.

---

# Resource-Based Design

In REST, everything revolves around **resources**.

Examples:

```
Users
Products
Orders
Categories
Reviews
```

Each resource has its own URL.

```text
/users
/products
/orders
```

Instead of describing actions in URLs, REST describes **resources** and uses HTTP methods to perform actions.

---

# Good vs Bad API Design

✅ Good

```http
GET /users
POST /users
GET /users/42
PATCH /users/42
DELETE /users/42
```

❌ Avoid

```http
/getUsers
/createUser
/updateUser
/deleteUser
```

The HTTP method already describes the action.

The URL should identify the resource.

---

# A REST Request

Example:

```http
GET /products/10
```

Breakdown:

```
GET
│
Action

/products
│
Resource

10
│
Resource Identifier
```

---

# Stateless Communication

REST builds on HTTP, which is stateless.

Each request should contain all the information the server needs.

Example:

```http
GET /profile

Authorization: Bearer <token>
```

The server shouldn't rely on previous requests to understand the current one.

---

# CRUD Mapping

REST maps naturally to CRUD operations.

| CRUD | HTTP Method | Example |
|------|-------------|----------|
| Create | POST | `/products` |
| Read | GET | `/products/10` |
| Update | PATCH | `/products/10` |
| Delete | DELETE | `/products/10` |

This consistency makes APIs easier to understand.

---

# Production Example

Imagine an online store.

Common endpoints might include:

```http
GET    /products
GET    /products/15

POST   /products

PATCH  /products/15

DELETE /products/15
```

Every client—whether it's a website, mobile app, or admin dashboard—uses the same API.

---

# REST Principles (Simplified)

A well-designed REST API typically follows these principles:

- Resource-oriented URLs
- Stateless requests
- Standard HTTP methods
- Meaningful status codes
- Consistent responses

You don't need to memorize these.

You'll naturally apply them as you design APIs.

---

# Best Practices

- Use nouns for resource names.
- Keep URLs simple and predictable.
- Use HTTP methods correctly.
- Return appropriate status codes.
- Keep request and response formats consistent.

---

# Common Mistakes

### ❌ Using verbs in URLs

Prefer:

```http
POST /orders
```

Instead of:

```http
POST /createOrder
```

---

### ❌ Designing different patterns for every endpoint

Consistency is more important than cleverness.

---

### ❌ Ignoring HTTP methods

Don't use `POST` for every operation.

Use the method that best represents the action.

---

# 💡 Did You Know?

Large platforms expose thousands of REST endpoints.

Even with many teams working independently, consistent naming conventions make APIs easier to learn and maintain.

---

# Key Takeaways

- REST is an architectural style for web APIs.
- APIs should be resource-oriented.
- HTTP methods describe actions.
- URLs identify resources.
- Consistency is one of the most important aspects of API design.

---

## 🚀 What's Next?

Now that we know what a good REST API looks like...

Let's learn the principles that make APIs easy to use, maintain, and scale.

➡️ **Next Chapter:** REST API Best Practices