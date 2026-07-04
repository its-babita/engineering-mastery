# Sessions

> Part of the **Engineering Mastery** handbook.

## ⏱️ Quick Facts

| | |
|---|---|
| **Read Time** | 10 minutes |
| **Difficulty** | 🟢 Beginner |
| **Prerequisites** | Cookies |

---

## 📍 Where We Are in the Request Journey

```text
User Logs In
      │
      ▼
Server Creates Session
      │
      ▼
Session ID Stored in Cookie
      │
      ▼
Browser Sends Cookie
      │
      ▼
Server Finds Session
      │
      ▼
User Is Authenticated
```

---

## Imagine This...

You check into a hotel.

The receptionist verifies your identity and gives you a room key.

```
Reception Desk
        │
Creates Booking
        │
Gives Room Key
        ▼
Guest
```

The room key doesn't contain all your booking details.

It simply points to your booking stored by the hotel.

A session works the same way.

---

# 💡 Why This Matters

HTTP is stateless.

Cookies help identify a browser.

But where does the application store information like:

- User ID
- Login status
- Shopping cart
- Permissions

That's the job of a **session**.

---

# What Is a Session?

A **session** is data stored on the **server** that represents a user's interaction with an application.

Each session has a unique identifier called a **Session ID**.

The browser stores only the Session ID (usually inside a cookie).

The actual session data stays on the server.

---

# Cookies vs Sessions

| Cookies | Sessions |
|----------|----------|
| Stored in the browser | Stored on the server |
| Usually contain a Session ID | Contain user data |
| Sent with every request | Retrieved using the Session ID |

Think of them as working together.

---

# How Sessions Work

### Step 1

The user logs in.

```
POST /login
```

The server verifies the credentials.

---

### Step 2

The server creates a session.

Example:

```text
Session ID

abc123
```

Session data:

```text
User ID: 42
Role: Admin
Logged In: true
```

---

### Step 3

The server sends the Session ID back.

```http
Set-Cookie:

sessionId=abc123
```

---

### Step 4

The browser stores the cookie.

---

### Step 5

Every future request includes:

```http
Cookie:

sessionId=abc123
```

The server looks up:

```
abc123
```

and loads the user's session.

---

# Behind the Scenes

```text
User Logs In
      │
      ▼
Server Verifies Credentials
      │
      ▼
Create Session
      │
      ▼
Store Session on Server
      │
      ▼
Send Session ID in Cookie
      │
      ▼
Browser Stores Cookie
      │
      ▼
Future Requests Include Cookie
      │
      ▼
Server Retrieves Session
```

---

# Where Are Sessions Stored?

Depending on the application, sessions may be stored in:

- Server memory
- Redis
- Database

For production applications, Redis is a common choice because it's fast and shared across multiple servers.

---

# Production Perspective

Imagine an e-commerce website.

Alice logs in.

The server creates:

```text
Session ID

abc123
```

Stored in Redis:

```text
User ID: 17
Role: Customer
Cart: 3 Items
```

Browser stores:

```http
Cookie:

sessionId=abc123
```

Every request includes the cookie.

The server loads Alice's session from Redis and knows who she is.

---

# Why Not Store Everything in Cookies?

Because cookies are stored on the client's device.

Keeping important session data on the server:

- Improves security.
- Allows the server to invalidate sessions.
- Prevents exposing sensitive information.

---

# Common Misconceptions

### ❌ Cookies and Sessions are the same

They work together, but they are different.

Cookies live in the browser.

Sessions live on the server.

---

### ❌ Sessions only store login information

Sessions can store any user-related data needed during a visit.

---

### ❌ Sessions last forever

Sessions usually expire after inactivity or when the user logs out.

---

# 💡 Did You Know?

Clicking **Log Out** often removes the session from the server.

Even if the browser still has the old Session ID, it no longer points to a valid session.

---

# Key Takeaways

- Sessions store user data on the server.
- Browsers usually store only the Session ID.
- Cookies and sessions work together.
- Sessions allow applications to remember users across requests.
- Production applications often store sessions in Redis.

---

## 🚀 What's Next?

The server now knows **who** the user is.

But...

**How does it verify a user's identity in the first place?**

➡️ **Next Chapter:** Authentication