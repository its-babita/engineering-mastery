# TLS & SSL

> Part of the **Engineering Mastery** handbook.

## ⏱️ Quick Facts

| | |
|---|---|
| **Read Time** | 10 minutes |
| **Difficulty** | 🟢 Beginner |
| **Prerequisites** | TCP Three-Way Handshake |

---

## Imagine This...

Suppose you need to send your bank details to a server.

If anyone on the network can read your message, your information is no longer private.

You need a way to communicate securely—even over a public network.

That's where **TLS** comes in.

---

# 💡 Why This Matters

Every day, millions of users:

- Log in to websites
- Make online payments
- Send personal messages
- Access cloud services

Without encryption, anyone intercepting the traffic could read sensitive information.

TLS protects that communication.

---

# What Are SSL and TLS?

**SSL (Secure Sockets Layer)** was the original protocol designed to secure communication over the internet.

Over time, SSL was replaced by **TLS (Transport Layer Security)**, which is faster, more secure, and fixes weaknesses found in SSL.

Today:

- SSL is **obsolete**
- TLS is the **modern standard**

Even though people still say **"SSL Certificate"**, they're almost always referring to certificates used with TLS.

---

# 🧠 Mental Model

Imagine sending a letter.

Without protection:

```
Letter

↓

Anyone can open it
```

With TLS:

```
Letter

↓

Locked in a secure box

↓

Only the recipient has the key
```

The package still travels through public roads.

But only the intended recipient can read what's inside.

---

# Where Does TLS Fit?

When you open:

```
https://shopsphere.example
```

the simplified flow looks like this:

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
```

Notice:

**TLS happens after TCP and before HTTP data is exchanged.**

---

# What Does TLS Provide?

TLS offers three important guarantees.

## 1. Encryption

Data is converted into an unreadable format during transmission.

Even if someone intercepts it, they can't understand it without the proper keys.

---

## 2. Authentication

TLS helps verify that you're talking to the correct server.

This reduces the risk of connecting to an attacker pretending to be a legitimate website.

---

## 3. Integrity

TLS helps ensure that data isn't modified while traveling across the network.

If someone changes the data, the connection detects it.

---

# Behind the Scenes

A simplified TLS process looks like this:

```text
TCP Connection
       │
       ▼
Exchange Security Information
       │
       ▼
Create Shared Encryption Keys
       │
       ▼
Encrypted Communication Begins
```

The actual TLS protocol is more complex, but this mental model is enough to understand its purpose.

---

# What Is a Certificate?

When you visit a secure website, the server presents a **digital certificate**.

Think of it as an official ID card.

It tells your browser:

> "I really am the server you intended to visit."

If the certificate is trusted, the browser continues the secure connection.

If not, you'll often see a warning message.

---

# Production Perspective

Modern production systems encrypt almost all communication.

Examples include:

- Browser → Web Server
- API Gateway → Backend Service
- Backend Service → Database
- Service → Service communication

Encrypting internal traffic is an important security practice, especially in cloud environments.

---

# Common Misconceptions

### ❌ SSL and TLS are different technologies used today

Not anymore.

TLS replaced SSL years ago.

Most modern systems use TLS, even if people casually say "SSL."

---

### ❌ TLS only encrypts passwords

TLS encrypts the entire communication session, not just login credentials.

---

### ❌ Encryption alone proves a website is trustworthy

Encryption protects communication.

It does **not** guarantee that the website itself is honest or safe.

---

# 💡 Did You Know?

You can often identify a secure connection by the **lock icon** in your browser.

That lock indicates the connection is protected using HTTPS, which relies on TLS.

---

# Key Takeaways

- TLS secures communication over the internet.
- SSL is obsolete and has been replaced by TLS.
- TLS provides:
  - Encryption
  - Authentication
  - Integrity
- TLS operates after TCP establishes a connection.
- HTTPS depends on TLS to protect web traffic.

---

## 🚀 What's Next?

We've established a secure connection.

Now...

**What exactly is HTTPS, and how is it different from HTTP?**

➡️ **Next Chapter:** HTTPS