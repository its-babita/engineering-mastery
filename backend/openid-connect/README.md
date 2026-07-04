# OpenID Connect (OIDC)

> Part of the **Engineering Mastery** handbook.

## ⏱️ Quick Facts

| | |
|---|---|
| **Read Time** | 10–12 minutes |
| **Difficulty** | 🟡 Intermediate |
| **Prerequisites** | OAuth 2.0 |

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
OAuth 2.0
      ↓
OpenID Connect ← You are here
      ↓
REST API Design
```

---

## Imagine This...

Suppose you're checking into a hotel.

The receptionist asks for your passport.

They verify:

- Your name
- Your identity
- Your photo

Once verified, you're checked in.

Now imagine instead that a trusted travel agency has already verified your identity and sends that information securely to the hotel.

The hotel doesn't need to verify you again.

That's similar to how OpenID Connect works.

---

# 💡 Why This Matters

Many applications let users click:

- Continue with Google
- Continue with GitHub
- Continue with Microsoft
- Continue with Apple

Most developers call this "OAuth Login."

Technically, that's incomplete.

OAuth gives an application permission to access resources.

**OpenID Connect provides the user's identity.**

---

# What Is OpenID Connect?

**OpenID Connect (OIDC)** is an identity layer built on top of OAuth 2.0.

It allows an application to verify **who the user is** after they successfully sign in.

In simple terms:

- OAuth answers: **"Can this app access your data?"**
- OIDC answers: **"Who is the user?"**

---

# OAuth vs OIDC

| OAuth 2.0 | OpenID Connect |
|-----------|----------------|
| Authorization | Authentication |
| Grants access to resources | Provides user identity |
| Returns an Access Token | Returns an ID Token |
| Used for API access | Used for user login |

OIDC extends OAuth rather than replacing it.

---

# How OIDC Works

```text
User
   │
   ▼
Application
   │
   ▼
Identity Provider
(Google, Microsoft, GitHub, etc.)
   │
   ▼
User Signs In
   │
   ▼
Identity Verified
   │
   ▼
ID Token + Access Token
   │
   ▼
Application
```

The application now knows who the user is without ever handling the user's password.

---

# ID Token

One of the biggest additions introduced by OIDC is the **ID Token**.

An ID Token is usually a JWT that contains information about the authenticated user.

Example payload:

```json
{
  "sub": "123456789",
  "name": "Alice",
  "email": "alice@example.com"
}
```

The application uses this information to identify the signed-in user.

---

# Production Example

Imagine you click:

```
Continue with Google
```

Behind the scenes:

1. You're redirected to Google.
2. Google verifies your identity.
3. Google asks if you want to share your profile.
4. You approve.
5. Google returns an ID Token and an Access Token.
6. The application creates your account or signs you in.

At no point does the application know your Google password.

---

# Where Is OIDC Used?

OIDC powers login experiences across many types of applications, including:

- SaaS platforms
- Enterprise dashboards
- Mobile apps
- Developer tools
- Internal company portals

It's become the standard way to support third-party login providers.

---

# Best Practices

- Always use HTTPS.
- Verify ID Tokens on the backend.
- Request only the user information you need.
- Store user accounts using a stable identifier (such as `sub`), not just an email address.
- Keep libraries and identity provider configurations up to date.

---

# Common Mistakes

### ❌ OAuth and OIDC are the same

OIDC builds on OAuth.

OAuth handles authorization.

OIDC handles authentication.

---

### ❌ Trust user information without verification

Always validate the ID Token before accepting user identity.

---

### ❌ Assume every OAuth provider supports OIDC

Many major providers do, but OAuth and OIDC are separate specifications.

Check the provider's documentation before implementing login.

---

# 💡 Did You Know?

When you click **"Continue with Google"**, the application usually receives:

- An **ID Token** to identify you.
- An **Access Token** to access approved Google APIs (if requested).

These tokens serve different purposes.

---

# Key Takeaways

- OpenID Connect is built on top of OAuth 2.0.
- OIDC provides user identity.
- OAuth provides delegated authorization.
- OIDC introduces the ID Token.
- "Sign in with Google" commonly uses OpenID Connect.

---

## 🚀 What's Next?

Your application can now:

- Authenticate users ✅
- Authorize requests ✅
- Securely store passwords ✅
- Support third-party login ✅

The next step is learning how to expose backend functionality through well-designed APIs.

➡️ **Next Chapter:** REST API Design