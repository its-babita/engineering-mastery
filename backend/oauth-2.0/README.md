# OAuth 2.0

> Part of the **Engineering Mastery** handbook.

## ⏱️ Quick Facts

| | |
|---|---|
| **Read Time** | 12–15 minutes |
| **Difficulty** | 🟡 Intermediate |
| **Prerequisites** | JSON Web Token (JWT) |

---

## 📍 Where We Are in the Authentication Journey

```text
Authentication
      ↓
Authorization
      ↓
Password Hashing
      ↓
JWT
      ↓
OAuth 2.0 ← You are here
      ↓
OpenID Connect (OIDC)
```

---

## Imagine This...

Suppose you hire a house cleaner.

You want them to enter your house while you're away.

Would you give them your personal house key?

Probably not.

Instead, you give them a temporary access card that:

- Works only during certain hours.
- Opens only specific rooms.
- Can be revoked at any time.

OAuth works in a similar way.

It allows an application to access certain resources **without sharing your password**.

---

# 💡 Why This Matters

Imagine a photo-printing app.

The app wants to import photos from your cloud storage.

Without OAuth, you would have to give the app your account password.

That would be risky.

Instead, OAuth lets you grant limited permission without exposing your credentials.

---

# What Is OAuth 2.0?

**OAuth 2.0** is an authorization framework.

It allows a user to grant one application limited access to resources managed by another application.

The user shares **permission**, not their password.

---

# A Real-World Example

Imagine you're using a photo-printing service.

It asks:

> "Allow access to your photos?"

You click **Allow**.

The application can now read your photos.

It still doesn't know your password.

---

# Key Roles in OAuth

| Role | Responsibility |
|------|----------------|
| Resource Owner | The user who owns the data |
| Client | The application requesting access |
| Authorization Server | Verifies the user and issues tokens |
| Resource Server | Stores the protected resources |

---

# How OAuth Works

```text
User
 │
 │ Wants to use an application
 ▼
Client Application
 │
 │ Redirect user to authorization server
 ▼
Authorization Server
 │
 │ User signs in and grants permission
 ▼
Access Token Issued
 │
 ▼
Client Uses Access Token
 │
 ▼
Resource Server
 │
 ▼
Protected Resource Returned
```

Notice that the client application never receives the user's password.

---

# Access Token

After the user grants permission, the authorization server issues an **access token**.

Example:

```text
eyJhbGciOi...
```

The client includes this token when requesting protected resources.

```http
GET /photos

Authorization: Bearer <Access Token>
```

The resource server verifies the token before returning data.

---

# Common OAuth Use Cases

OAuth is widely used for:

- Connecting cloud storage
- Calendar integrations
- Payment provider integrations
- Social media integrations
- Enterprise applications

---

# OAuth Is Not Authentication

This is the most common misunderstanding.

OAuth answers:

> "Can this application access your data?"

It does **not** answer:

> "Who are you?"

That's why OAuth alone is not a login system.

---

# Production Perspective

Suppose you connect a calendar application to your work calendar.

Instead of entering your company password into the calendar app:

1. You're redirected to your company's identity provider.
2. You sign in there.
3. You approve access.
4. The calendar app receives an access token.
5. It can now read your calendar events.

Your password never leaves the identity provider.

---

# Best Practices

- Always use HTTPS.
- Request only the permissions you need.
- Keep access tokens short-lived.
- Revoke tokens that are no longer needed.
- Never expose client secrets in frontend applications.

---

# Common Mistakes

### ❌ OAuth is authentication

OAuth is an authorization framework.

Identity is handled by OpenID Connect.

---

### ❌ Share user passwords between applications

OAuth exists to avoid this.

Applications should never ask for another service's password.

---

### ❌ Request unnecessary permissions

Follow the principle of least privilege.

Ask only for the access your application truly needs.

---

# 💡 Did You Know?

When you see:

- "Allow this app to access your calendar"
- "Allow access to your contacts"
- "Allow access to your photos"

you're usually interacting with an OAuth authorization flow.

---

# Key Takeaways

- OAuth 2.0 is an authorization framework.
- It allows applications to access resources without sharing user passwords.
- Access is granted through access tokens.
- OAuth is not the same as authentication.
- OAuth enables secure integrations between applications.

---

## 🚀 What's Next?

OAuth lets applications access your resources.

But...

**How does "Sign in with Google" actually verify who you are?**

That's where **OpenID Connect (OIDC)** comes in.

➡️ **Next Chapter:** OpenID Connect (OIDC)