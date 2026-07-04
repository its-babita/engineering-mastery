# TCP Three-Way Handshake

> Part of the **Engineering Mastery** handbook.

## ⏱️ Quick Facts

| | |
|---|---|
| **Read Time** | 10–12 minutes |
| **Difficulty** | 🟢 Beginner |
| **Prerequisites** | TCP vs UDP |

---

## Imagine This...

Before making a phone call, you don't immediately start talking.

The conversation usually begins like this:

```
You: Hello?

Friend: Hi, I can hear you.

You: Great, let's talk.
```

Only after both sides confirm they can communicate does the conversation begin.

TCP works the same way.

Before sending actual data, both devices first establish a connection.

---

# 💡 Why This Matters

Imagine sending important data before checking whether the other device is ready.

- What if the server is offline?
- What if the network is slow?
- What if the request reaches the wrong destination?

TCP avoids these problems by establishing a connection first.

---

# What Is the TCP Three-Way Handshake?

The **TCP Three-Way Handshake** is the process used to establish a reliable connection between a client and a server before exchanging data.

It consists of **three messages**:

1. SYN
2. SYN-ACK
3. ACK

Only after these three steps does data transfer begin.

---

# 🧠 Mental Model

Think of visiting someone's house.

```
Knock

↓

Someone opens the door

↓

You greet each other

↓

Conversation starts
```

You don't walk in before knowing someone is home.

TCP follows the same principle.

---

# Step 1 — SYN

The client wants to start a connection.

It sends a **SYN (Synchronize)** message.

```
Client
   │
   ├──────── SYN ───────►
   │
Server
```

Meaning:

> "I'd like to start a conversation."

---

# Step 2 — SYN-ACK

The server receives the request.

If it's ready, it replies with **SYN-ACK**.

```
Client
   │
   ├──────── SYN ───────►
   │
   ◄────── SYN-ACK ─────┤
Server
```

Meaning:

> "I received your request, and I'm ready."

---

# Step 3 — ACK

The client confirms it received the server's response.

```
Client
   │
   ├──────── SYN ───────►
   │
   ◄────── SYN-ACK ─────┤
   │
   ├──────── ACK ───────►
   │
Server
```

Meaning:

> "Perfect. Let's begin."

The connection is now established.

Data transfer can start.

---

# Complete Flow

```text
Client                         Server

   SYN  ---------------------->

        <------------------  SYN-ACK

   ACK  ---------------------->

===============================
Connection Established
===============================

      Data Transfer Begins
```

---

# Why Three Steps?

The handshake ensures that:

- Both devices are reachable.
- Both devices are ready.
- Both agree to start communication.

Without this process, one side might begin sending data before the other is prepared.

---

# Where Is It Used?

Every time you:

- Open a website
- Call an API
- Download a file
- Connect to a database
- Access a cloud service

A TCP connection is usually established first.

It happens so quickly that users rarely notice it.

---

# Production Perspective

Suppose a user opens:

```
https://shopsphere.example
```

A simplified sequence looks like this:

```text
Browser
     │
     ▼
DNS Lookup
     │
     ▼
Server IP
     │
     ▼
TCP Three-Way Handshake
     │
     ▼
TLS Handshake (HTTPS)
     │
     ▼
HTTP Request
     │
     ▼
HTTP Response
```

The TCP handshake happens **before** the browser sends the HTTP request.

Without a successful TCP connection, the server never receives the request.

---

# Common Mistakes

### ❌ TCP starts sending data immediately

No.

The connection must first be established.

---

### ❌ The handshake transfers application data

It doesn't.

Its only purpose is to establish the connection.

Actual data is sent afterward.

---

### ❌ Every protocol uses a handshake

No.

UDP does not establish a connection before sending data.

---

# Performance Note

The handshake introduces a small amount of latency because three messages are exchanged before data transfer begins.

However, this overhead provides the reliability that TCP is known for.

---

# Key Takeaways

- TCP establishes a connection before sending data.
- The connection is created using three steps:
  - SYN
  - SYN-ACK
  - ACK
- The handshake confirms both devices are ready.
- No application data is exchanged during the handshake.
- Reliable communication begins only after the handshake completes.

---

## 🚀 What's Next?

The connection is established.

But...

How can two devices exchange sensitive information safely over a public network?

The answer is **TLS/SSL**.

➡️ **Next Chapter:** TLS & SSL