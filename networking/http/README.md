# HTTP (Hypertext Transfer Protocol)

> Part of the **Engineering Mastery** handbook.

## ⏱️ Quick Facts

| | |
|---|---|
| **Read Time** | 12–15 minutes |
| **Difficulty** | 🟢 Beginner |
| **Prerequisites** | HTTPS |

---

## 📍 Where We Are in the Request Journey

```text
URL
  ↓
DNS
  ↓
IP Address
  ↓
Port
  ↓
TCP
  ↓
TLS
  ↓
HTTPS
  ↓
HTTP ← You are here
  ↓
Server
  ↓
Response
```

---

## Imagine This...

You walk into a restaurant.

The conversation usually looks like this:

```
Customer:
I'd like a coffee.

Waiter:
Sure.

☕

Coffee arrives.
```

Notice something?

The customer and waiter both understand **how to communicate**.

HTTP works in the same way.

It defines the rules for communication between a client and a server.

---

# 💡 Why This Matters

Every time you:

- Open a website
- Call an API
- Submit a form
- Upload a file
- Fetch product details

You're using HTTP.

If networking is the road...

HTTP is the language spoken on that road.

---

# What Is HTTP?

**HTTP (Hypertext Transfer Protocol)** is an application-layer protocol used for communication between a client and a server.

It defines:

- How a request is sent.
- How a response is returned.
- What information is included.
- How both sides understand each other.

HTTP doesn't decide **where** data goes.

Networking protocols already handled that.

HTTP decides **how** data is exchanged.

---

# 🧠 Mental Model

Imagine ordering food.

```
Customer

↓

Places Order

↓

Kitchen Prepares Food

↓

Food Returned
```

Similarly:

```
Client

↓

HTTP Request

↓

Server Processes Request

↓

HTTP Response
```

---

# The Request–Response Cycle

Every HTTP communication follows the same pattern.

```text
Client
   │
   │ HTTP Request
   ▼
Server
   │
   │ HTTP Response
   ▼
Client
```

One request.

One response.

This simple model powers almost every website and API.

---

# What's Inside an HTTP Request?

A request usually contains:

- HTTP Method
- URL
- Headers
- Optional Body

Example:

```text
GET /products HTTP/1.1

Host: api.shopsphere.example
```

Don't worry about every line yet.

We'll explore each part in later chapters.

---

# What's Inside an HTTP Response?

A response usually contains:

- Status Code
- Headers
- Response Body

Example:

```text
HTTP/1.1 200 OK

Content-Type: application/json

{
  "id": 1,
  "name": "Laptop"
}
```

---

# HTTP Is Stateless

One of HTTP's most important characteristics is that it's **stateless**.

This means:

Every request is treated independently.

The server doesn't automatically remember previous requests.

Example:

```
Request 1

↓

Server responds

↓

Connection ends

↓

Request 2

↓

Server treats it as a new request
```

This design keeps HTTP simple and scalable.

Later, we'll see how **cookies** and **sessions** help applications remember users.

---

# HTTP Methods (Overview)

Methods describe the action the client wants to perform.

| Method | Purpose |
|---------|----------|
| GET | Retrieve data |
| POST | Create data |
| PUT | Replace data |
| PATCH | Update part of existing data |
| DELETE | Remove data |

We'll explore each method in detail later.

---

# HTTP Status Codes (Overview)

The server tells the client whether the request succeeded.

Examples:

| Status | Meaning |
|---------|----------|
| 200 | Success |
| 201 | Resource Created |
| 400 | Bad Request |
| 401 | Unauthorized |
| 404 | Not Found |
| 500 | Internal Server Error |

Status codes help clients understand the result of a request.

---

# HTTP Versions (Overview)

HTTP has evolved over time.

| Version | Highlights |
|---------|------------|
| HTTP/1.1 | Persistent connections |
| HTTP/2 | Multiplexing and header compression |
| HTTP/3 | Built on QUIC for lower latency |

For most backend developers, the concepts of requests and responses remain the same regardless of the version.

---

# Behind the Scenes

Suppose a user opens:

```
https://shopsphere.example/products
```

The request journey now looks like this:

```text
Browser
    │
    ▼
Create HTTP Request
    │
    ▼
Send to Server
    │
    ▼
Server Processes Request
    │
    ▼
Generate Response
    │
    ▼
Return HTTP Response
    │
    ▼
Browser Displays Result
```

---

# Production Perspective

Every modern backend application depends on HTTP.

Examples include:

- E-commerce platforms
- Mobile application backends
- Banking systems
- SaaS products
- Public APIs
- Internal microservices

Even when applications communicate through other protocols, HTTP is often used for administration, health checks, and external APIs.

---

# Common Mistakes

### ❌ HTTP and HTML are the same

HTML is a markup language.

HTTP is a communication protocol.

They solve completely different problems.

---

### ❌ HTTP is only for websites

HTTP powers:

- REST APIs
- Mobile applications
- Web dashboards
- IoT devices
- Microservices

It's much more than web pages.

---

### ❌ HTTP remembers previous requests

HTTP is stateless.

If an application needs to remember users, it must use additional mechanisms such as cookies, sessions, or tokens.

---

# Key Takeaways

- HTTP defines how clients and servers communicate.
- Communication follows a request–response model.
- HTTP requests and responses have a well-defined structure.
- HTTP is stateless by design.
- Almost every backend application relies on HTTP.

---

## 🚀 What's Next?

Now that we understand how HTTP works...

Let's look at one of its most important parts.

**How does the client tell the server what action it wants to perform?**

➡️ **Next Chapter:** HTTP Methods