# TCP vs UDP

> Part of the **Engineering Mastery** handbook.

## ⏱️ Quick Facts

| | |
|---|---|
| **Read Time** | 10 minutes |
| **Difficulty** | 🟢 Beginner |
| **Prerequisites** | Ports |

---

## Imagine This...

You're sending a package.

There are two delivery options:

### Option 1: Registered Courier

- Confirms delivery
- Retries if the package is lost
- Ensures everything arrives correctly

### Option 2: Standard Postcard

- Sent immediately
- No delivery confirmation
- If it's lost, it's gone

Both deliver information.

They simply have different priorities.

This is exactly the difference between **TCP** and **UDP**.

---

# 💡 Why This Matters

Every application on the internet sends data.

But not every application has the same requirements.

A banking application values **accuracy**.

A live video call values **speed**.

Choosing the wrong protocol can make your application slow or unreliable.

---

# What is TCP?

**TCP (Transmission Control Protocol)** is a communication protocol designed for **reliable** data transfer.

Before sending data, TCP establishes a connection between the sender and receiver.

It makes sure:

- Data arrives.
- Data arrives in the correct order.
- Missing data is retransmitted.

If reliability matters, TCP is usually the right choice.

---

# What is UDP?

**UDP (User Datagram Protocol)** is designed for **speed**.

It sends data immediately without establishing a connection.

UDP:

- Doesn't verify delivery.
- Doesn't retransmit lost packets.
- Doesn't guarantee packet order.

This makes it much faster than TCP.

---

# 🧠 Mental Model

Imagine two ways of talking.

### TCP

Like a phone conversation.

```
"Can you hear me?"

"Yes."

"Great, let's begin."
```

Both sides confirm communication before exchanging information.

---

### UDP

Like speaking through a loudspeaker.

```
"The event starts now!"
```

You simply broadcast the message.

If someone misses it, you don't repeat everything.

---

# TCP vs UDP

| Feature | TCP | UDP |
|---------|-----|-----|
| Connection | ✅ Required | ❌ Not Required |
| Reliable | ✅ Yes | ❌ No |
| Ordered Delivery | ✅ Yes | ❌ No |
| Retransmission | ✅ Yes | ❌ No |
| Speed | Slower | Faster |

---

# Real-World Examples

### TCP

Used when every piece of data matters.

Examples:

- Websites
- Online banking
- Email
- File downloads
- REST APIs

Missing data could cause errors.

---

### UDP

Used when speed is more important than perfection.

Examples:

- Video calls
- Voice calls
- Live streaming
- Online gaming
- DNS lookups

Losing a tiny amount of data is usually better than waiting for retransmission.

---

# Behind the Scenes

## TCP

```text
Create Connection
        │
        ▼
Send Data
        │
        ▼
Receive Confirmation
        │
        ▼
Continue
```

---

## UDP

```text
Send Data
     │
     ▼
Done
```

Simple.

Fast.

No guarantees.

---

# Production Perspective

Most backend APIs use **TCP** because requests must be complete and accurate.

For example:

- Login requests
- Payment processing
- Database communication
- File uploads

On the other hand, applications such as:

- Video conferencing
- Multiplayer games
- Live sports streaming

often use **UDP** to minimize delay.

A brief loss of data is less noticeable than a long pause.

---

# Which One Should You Choose?

Choose **TCP** when:

- Accuracy matters.
- Data must not be lost.
- Order is important.

Choose **UDP** when:

- Low latency is critical.
- Small data loss is acceptable.
- Speed is more important than reliability.

---

# Common Mistakes

### ❌ UDP is "bad"

It's not.

UDP is the best choice for many real-time applications.

---

### ❌ TCP is always better

TCP provides reliability,

but reliability has a cost.

More checks mean more overhead.

---

### ❌ Faster always means better

The best protocol depends on the problem you're solving.

---

# Key Takeaways

- TCP focuses on reliability.
- UDP focuses on speed.
- TCP establishes a connection before sending data.
- UDP sends data immediately.
- Choose the protocol based on your application's needs.

---

## 🚀 What's Next?

We've learned that TCP creates a connection before sending data.

But...

**How is that connection actually established?**

➡️ **Next Chapter:** TCP Three-Way Handshake