# Authentication

> Part of the **Engineering Mastery** handbook.

## ⏱️ Quick Facts

| | |
|---|---|
| **Read Time** | 10–12 minutes |
| **Difficulty** | 🟢 Beginner |
| **Prerequisites** | Sessions |

---

## 📍 Where We Are in the User Journey

```text
User Opens Website
        │
        ▼
Login Page
        │
        ▼
Enter Email & Password
        │
        ▼
Authentication ← You are here
        │
        ▼
Session or JWT Created
        │
        ▼
Future Requests
        │
        ▼
Authorization
```

---

## Imagine This...

You arrive at an office building.

The security guard asks for your ID card.

If your identity is verified, you're allowed to enter the building.

The guard only answers one question:

> **"Who are you?"**

That's authentication.

---

# 💡 Why This Matters

Almost every application needs to identify its users.

Examples include:

- Online banking
- E-commerce websites
- Social media
- Hospital systems
- Company dashboards

Before an application can decide **what you're allowed to do**, it must first know **who you are**.

---

# What Is Authentication?

**Authentication** is the process of verifying a user's identity.

It answers the question:

> **"Are you really who you claim to be?"**

If the answer is yes, the user is authenticated.

---

# Authentication vs Authorization

These terms are often confused.

| Authentication | Authorization |
|----------------|---------------|
| Verifies identity | Verifies permissions |
| "Who are you?" | "What can you do?" |
| Happens first | Happens after authentication |

Example:

```
Alice logs in.

↓

Authentication

↓

System confirms Alice's identity.

↓

Authorization

↓

Alice can view orders but cannot access the admin dashboard.
```

---

# How Authentication Works

A typical login flow looks like this:

```text
User
   │
Enter Email & Password
   ▼
Server
   │
Find User
   │
Compare Password
   ▼
Valid?
   │
 ┌───────┴────────┐
 │                │
 ▼                ▼
Yes              No
 │                │
 ▼                ▼
Create Session   Return Error
or JWT
```

---

# Common Authentication Methods

Applications verify identity in different ways.

### Password-Based Authentication

The user provides:

- Email or username
- Password

This is the most common authentication method.

---

### Multi-Factor Authentication (MFA)

The user provides:

- Password
- One-time code
- Authenticator app
- Security key

Even if a password is stolen, an attacker still needs the second factor.

---

### Social Login

Users authenticate through another provider.

Examples include:

- Google
- GitHub
- Apple

The application trusts the identity verification performed by that provider.

---

# Production Perspective

Suppose Alice logs in.

```
POST /login
```

Request:

```json
{
  "email": "alice@example.com",
  "password": "********"
}
```

The backend:

1. Finds Alice's account.
2. Verifies the password.
3. Creates a session or generates a JWT.
4. Returns a successful response.

Future requests now include that session or token instead of Alice entering her password every time.

---

# Best Practices

- Never store plain-text passwords.
- Always use HTTPS.
- Hash passwords before storing them.
- Rate-limit login attempts.
- Support multi-factor authentication when appropriate.

We'll cover password hashing and JWT in upcoming chapters.

---

# Common Mistakes

### ❌ Authentication and authorization are the same

Authentication verifies identity.

Authorization verifies permissions.

---

### ❌ Storing plain-text passwords

Passwords should always be securely hashed before storage.

---

### ❌ Sending passwords over HTTP

Always use HTTPS to protect credentials during transmission.

---

# 💡 Did You Know?

Most applications ask for your password only once.

After that, they rely on a session or token to recognize you until you log out or your session expires.

---

# Key Takeaways

- Authentication verifies a user's identity.
- It answers: **"Who are you?"**
- Authentication happens before authorization.
- Applications commonly use passwords, MFA, or social login.
- After successful authentication, a session or JWT is usually created.

---

## 🚀 What's Next?

The application now knows **who the user is**.

But...

**How does it decide what that user is allowed to do?**

➡️ **Next Chapter:** Authorization