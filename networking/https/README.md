# HTTPS

> Part of the **Engineering Mastery** handbook.

## ⏱️ Quick Facts

| | |
|---|---|
| **Read Time** | 8–10 minutes |
| **Difficulty** | 🟢 Beginner |
| **Prerequisites** | TLS & SSL |

---

## 📍 Where We Are in the Request Journey

```text
URL ✅
    ↓
DNS ✅
    ↓
IP Address ✅
    ↓
Port ✅
    ↓
TCP Handshake ✅
    ↓
TLS ✅
    ↓
HTTPS ← You are here
    ↓
HTTP Request
    ↓
Response
```

---

## Imagine This...

You're sending a confidential document.

There are two ways to send it.

### Option 1

A normal envelope.

Anyone who gets hold of it can read what's inside.

### Option 2

A sealed, tamper-proof envelope.

Only the intended recipient can open and read it.

HTTPS is like the second option.

It doesn't change the message.

It protects the message while it's being delivered.

---

# 💡 Why This Matters

Whenever you:

- Log in to a website
- Make an online payment
- Submit a registration form
- Access an API

Your data travels across multiple networks.

Without HTTPS, that information could be exposed if intercepted.

---

# What Is HTTPS?

**HTTPS (Hypertext Transfer Protocol Secure)** is the secure version of HTTP.

It uses **TLS** to encrypt communication between a client and a server.

Think of it like this:

```text
HTTPS

=

HTTP

+

TLS
```

- **HTTP** defines how data is exchanged.
- **TLS** protects that data during transmission.

Together, they form **HTTPS**.

---

# 🧠 Mental Model

Imagine sending a letter.

HTTP decides:

- What goes inside the letter.
- How the sender and receiver communicate.

TLS adds:

- A locked envelope.
- A security seal.

HTTPS is simply:

```
HTTP

inside

TLS protection
```

---

# HTTP vs HTTPS

| Feature | HTTP | HTTPS |
|---------|------|-------|
| Encryption | ❌ No | ✅ Yes |
| Authentication | ❌ No | ✅ Yes |
| Data Integrity | ❌ No | ✅ Yes |
| Default Port | 80 | 443 |
| URL Prefix | `http://` | `https://` |

---

# Behind the Scenes

When you open:

```
https://shopsphere.example
```

a simplified flow looks like this:

```text
Browser
    │
    ▼
DNS Lookup
    │
    ▼
TCP Connection
    │
    ▼
TLS Handshake
    │
    ▼
Encrypted Connection
    │
    ▼
HTTP Request
    │
    ▼
HTTP Response
```

Notice that the **HTTP request is still HTTP**.

The difference is that it travels through an encrypted TLS connection.

---

# Why Is HTTPS Important?

Without HTTPS:

```
Client

↓

Login Request

↓

Anyone on the network can potentially read it
```

With HTTPS:

```
Client

↓

Encrypted Login Request

↓

Unreadable to anyone without the encryption keys
```

Even if someone captures the traffic, they can't easily understand its contents.

---

# Production Perspective

Today, HTTPS is the default for almost every production application.

Examples include:

- Banking platforms
- E-commerce websites
- Social media applications
- Cloud dashboards
- REST APIs

Many browsers now warn users before opening websites that only support HTTP.

Some modern browser features also require HTTPS before they'll work.

---

# Common Misconceptions

### ❌ HTTPS is a completely different protocol

It isn't.

HTTPS is simply **HTTP running over a secure TLS connection**.

---

### ❌ HTTPS makes a website safe

HTTPS secures the communication.

It does not guarantee that the website itself is trustworthy.

A malicious website can still use HTTPS.

---

### ❌ Only login pages need HTTPS

Every page should use HTTPS.

Encrypting all traffic protects user privacy and prevents unnecessary risks.

---

# 💡 Did You Know?

Many websites automatically redirect:

```
http://example.com
```

to

```
https://example.com
```

This ensures users always communicate over a secure connection.

---

# Key Takeaways

- HTTPS is HTTP protected by TLS.
- HTTPS encrypts data during transmission.
- HTTPS provides encryption, authentication, and integrity.
- HTTPS uses port **443** by default.
- Modern production systems should use HTTPS everywhere.

---

## 🚀 What's Next?

We've learned how communication becomes secure.

Now it's time to understand the protocol that powers almost every website and API.

**How does HTTP actually work?**

➡️ **Next Chapter:** HTTP