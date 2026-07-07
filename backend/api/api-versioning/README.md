# API Versioning

> Part of the **Engineering Mastery** handbook.

## ⏱️ Quick Facts

| | |
|---|---|
| **Read Time** | 8–10 minutes |
| **Difficulty** | 🟢 Beginner |
| **Prerequisites** | Error Handling |

---

## 💡 Why This Matters

APIs rarely stay the same forever.

Over time you may need to:

- Add new features
- Rename fields
- Remove old endpoints
- Improve response formats

Changing an existing API without a version can break mobile apps, frontend applications, and third-party integrations.

API versioning allows you to evolve your API while keeping existing clients working.

---

# What Is API Versioning?

**API versioning** is the practice of creating different versions of an API so that changes don't break existing consumers.

Instead of changing:

```http
GET /users
```

You introduce a new version:

```http
GET /api/v1/users
```

Later:

```http
GET /api/v2/users
```

Older clients continue using **v1** while newer clients move to **v2**.

---

# Why Version APIs?

Imagine a mobile app released six months ago.

It expects this response:

```json
{
  "name": "Alice"
}
```

Now imagine you change it to:

```json
{
  "fullName": "Alice"
}
```

The older app may stop working because it still expects `name`.

Versioning prevents this problem.

---

# Common Versioning Strategies

## URL Versioning

The version appears in the URL.

```http
GET /api/v1/products
```

```http
GET /api/v2/products
```

This is the most common and beginner-friendly approach.

---

## Header Versioning

The version is sent in a request header.

Example:

```http
API-Version: 2
```

The URL stays the same:

```http
GET /products
```

This keeps URLs clean but is less visible.

---

## Query Parameter Versioning

Example:

```http
GET /products?version=2
```

Simple, but less commonly used for public APIs.

---

# Which Approach Should You Use?

For most projects:

✅ URL versioning is a great choice.

It's:

- Easy to understand
- Easy to document
- Easy to test
- Widely used

---

# Production Example

Version 1:

```http
GET /api/v1/users/1
```

Response:

```json
{
  "id": 1,
  "name": "Alice"
}
```

Version 2:

```http
GET /api/v2/users/1
```

Response:

```json
{
  "id": 1,
  "fullName": "Alice",
  "email": "alice@example.com"
}
```

Both versions can exist at the same time while clients migrate.

---

# When Should You Create a New Version?

A new version is usually needed when making **breaking changes**, such as:

- Renaming fields
- Removing fields
- Changing response formats
- Changing endpoint behavior

Adding optional fields generally doesn't require a new version.

---

# Best Practices

- Keep old versions available while clients migrate.
- Clearly document version differences.
- Avoid creating a new version for every small change.
- Deprecate old versions before removing them.
- Use consistent version naming.

---

# Common Mistakes

### ❌ Breaking existing APIs

Avoid changing response structures without versioning.

---

### ❌ Creating too many versions

Only introduce a new version when necessary.

---

### ❌ Removing old versions immediately

Give consumers enough time to migrate.

---

# 💡 Did You Know?

Many companies support multiple API versions simultaneously to ensure older mobile apps continue working until users update them.

---

# Key Takeaways

- APIs evolve over time.
- Versioning prevents breaking existing clients.
- URL versioning is simple and widely adopted.
- Create new versions only for breaking changes.
- Deprecate old versions gradually.

---

## 🚀 What's Next?

Even a well-designed API needs protection from abuse.

The next chapter explores how to prevent excessive requests and keep services reliable.

➡️ **Next Chapter:** Rate Limiting