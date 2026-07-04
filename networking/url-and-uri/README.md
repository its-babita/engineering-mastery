# URL & URI

> Part of the **Engineering Mastery** handbook.

## ⏱️ Quick Facts

| | |
|---|---|
| **Read Time** | 8–10 minutes |
| **Difficulty** | 🟢 Beginner |
| **Prerequisites** | How the Internet Works |

---

## Imagine This...

You open your browser and type:

```
https://github.com
```

How does your browser know:

- Which website to visit?
- Which page to open?
- Whether the connection should be secure?

The answer lies in the **URL**.

---

# 💡 Why This Matters

Every request on the web starts with an address.

Without an address, your browser has no idea where to send your request.

As a backend engineer, you'll work with URLs every day:

- API endpoints
- Image links
- Database connections
- OAuth callbacks
- Webhooks

Understanding URLs is fundamental.

---

# What is a URI?

A **URI (Uniform Resource Identifier)** is a string that identifies a resource.

Think of it as an umbrella term.

A URI can:

- Identify a resource
- Locate a resource
- Or both

---

# What is a URL?

A **URL (Uniform Resource Locator)** is a type of URI that tells your browser **where** a resource is located and **how** to access it.

Every URL is a URI.

But **not every URI is a URL**.

Think of it like this:

```
URI
│
├── URL ✅
└── URN
```

> 💡 **Good to Know:** In everyday web development, you'll mostly use **URLs**. You'll rarely need to distinguish between a URI and a URL unless you're reading specifications or preparing for interviews.

---

# Breaking Down a URL

Consider this URL:

```
https://api.example.com:443/users/42?sort=desc#profile
```

| Part | Example | Purpose |
|------|---------|---------|
| Protocol | `https` | How to communicate |
| Host | `api.example.com` | Server name |
| Port | `443` | Service entry point |
| Path | `/users/42` | Specific resource |
| Query | `sort=desc` | Extra information |
| Fragment | `profile` | Section within the page |

Visual representation:

```text
https://api.example.com:443/users/42?sort=desc#profile
│      │                │    │         │          │
│      │                │    │         │          └── Fragment
│      │                │    │         └──────────── Query
│      │                │    └────────────────────── Path
│      │                └─────────────────────────── Port
│      └──────────────────────────────────────────── Host
└─────────────────────────────────────────────────── Protocol
```

---

# What Happens After You Press Enter?

When you press **Enter**, your browser roughly follows these steps:

```
Read URL
      │
      ▼
Extract Domain
      │
      ▼
Find IP Address (DNS)
      │
      ▼
Connect to Server
      │
      ▼
Send HTTP Request
```

This entire process usually completes in milliseconds.

---

# Real-World Examples

### Homepage

```
https://github.com
```

Opens GitHub's homepage.

---

### User Profile

```
https://github.com/octocat
```

Requests the profile of `octocat`.

---

### API Endpoint

```
https://api.github.com/users/octocat
```

Returns user information in JSON.

Backend developers work with URLs like this every day.

---

# Understanding the Path

Suppose you're building an online bookstore.

```
/books
```

Returns all books.

```
/books/15
```

Returns the book with ID `15`.

```
/books/15/reviews
```

Returns reviews for that book.

The **path** tells the server *what resource* you're requesting.

---

# Understanding Query Parameters

Query parameters provide additional instructions.

Example:

```
/products?category=laptop&sort=price
```

The path identifies the resource:

```
/products
```

The query customizes the result:

- Filter by `laptop`
- Sort by `price`

This keeps APIs flexible without creating many different endpoints.

---

# Production Perspective

Companies like Amazon and Netflix design URLs carefully.

Good URLs are:

- Predictable
- Readable
- Consistent
- Easy to cache
- Easy to document

Example:

✅

```
/users/42/orders
```

❌

```
/getUserOrders?id=42&type=current
```

A clean URL makes an API easier to understand and maintain.

---

# Common Mistakes

### ❌ Confusing URLs with File Paths

A URL identifies a resource.

It doesn't always point to a physical file on the server.

For example:

```
/users/42
```

The server might generate this response dynamically.

---

### ❌ Ignoring URL Encoding

Characters like spaces cannot appear directly in a URL.

For example:

```
Engineering Mastery
```

becomes:

```
Engineering%20Mastery
```

Browsers automatically encode special characters.

---

### ❌ Putting Sensitive Data in URLs

Avoid this:

```
/login?password=secret123
```

URLs can be stored in:

- Browser history
- Server logs
- Analytics tools

Sensitive information belongs in the request body or headers, not the URL.

---

# Key Takeaways

- A URI identifies a resource.
- A URL is a type of URI that tells the browser where and how to access a resource.
- Every URL has different parts, such as protocol, host, path, and query.
- Clean URLs improve API design.
- Sensitive information should never be placed in URLs.

---

## 🚀 What's Next?

The browser now knows the domain:

```
github.com
```

But computers don't understand domain names.

They communicate using **IP addresses**.

So...

**How does `github.com` become an IP address?**

➡️ **Next Chapter:** DNS (Domain Name System)