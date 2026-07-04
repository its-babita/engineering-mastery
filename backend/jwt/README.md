# JSON Web Token (JWT)

> Part of the **Engineering Mastery** handbook.

## ⏱️ Quick Facts

| | |
|---|---|
| **Read Time** | 12–15 minutes |
| **Difficulty** | 🟡 Intermediate |
| **Prerequisites** | Password Hashing |

---

## 📍 Where We Are in the Authentication Flow

```text
User Logs In
      │
      ▼
Password Verified
      │
      ▼
JWT Created ← You are here
      │
      ▼
Client Stores Token
      │
      ▼
Future Requests Include JWT
      │
      ▼
Server Verifies JWT
```

---

## Imagine This...

You attend a conference.

At the registration desk, your identity is verified.

Instead of checking your ID every time you enter a room, you're given a wristband.

As long as the wristband is valid, staff recognize that you've already been verified.

A JWT works in a similar way.

---

# 💡 Why This Matters

Without JWTs, a user might need the server to look up a session on every request.

JWTs allow the client to carry proof of authentication.

This makes them especially useful for APIs, mobile apps, and distributed systems.

---

# What Is a JWT?

A **JSON Web Token (JWT)** is a compact, signed token that contains information (called **claims**) about a user.

After a successful login, the server creates a JWT and sends it to the client.

The client includes the token in future requests.

---

# How JWT Authentication Works

## Step 1

The user logs in.

```http
POST /login
```

---

## Step 2

The server verifies the credentials.

If valid, it creates a JWT.

---

## Step 3

The server returns the token.

```json
{
  "token": "eyJhbGciOiJIUzI1NiIs..."
}
```

---

## Step 4

The client stores the token.

Common options include:

- Memory (recommended for SPAs)
- Secure HTTP-only cookie
- Secure device storage (mobile)

---

## Step 5

Every protected request includes the token.

```http
GET /profile

Authorization: Bearer <JWT>
```

---

## Step 6

The server verifies the token.

If valid, the request continues.

If invalid or expired, access is denied.

---

# JWT Structure

A JWT has three parts.

```text
Header
      .
Payload
      .
Signature
```

Example:

```text
xxxxx.yyyyy.zzzzz
```

---

## Header

Contains metadata.

Example:

```json
{
  "alg": "HS256",
  "typ": "JWT"
}
```

---

## Payload

Contains claims.

Example:

```json
{
  "userId": 42,
  "role": "admin"
}
```

> The payload is **encoded**, not encrypted. Do not store passwords or other sensitive information in it.

---

## Signature

The signature allows the server to verify that the token hasn't been modified.

If someone changes the payload, the signature no longer matches, and the token is rejected.

---

# JWT vs Sessions

| Sessions | JWT |
|----------|-----|
| Server stores session data | Client stores token |
| Requires server-side session storage | No server-side session storage required |
| Easy to revoke | Harder to revoke before expiration |
| Good for traditional web apps | Good for APIs and distributed systems |

Neither approach is universally better.

Choose the one that fits your application.

---

# Production Example

A user logs in.

Response:

```json
{
  "token": "eyJhbGciOi..."
}
```

Future request:

```http
GET /orders

Authorization: Bearer eyJhbGciOi...
```

The server verifies the signature.

If valid:

```
User authenticated ✅
```

Otherwise:

```
401 Unauthorized
```

---

# Best Practices

- Always use HTTPS.
- Set a reasonable expiration time.
- Never store passwords in the payload.
- Verify every token on the server.
- Rotate signing secrets when necessary.

---

# Common Mistakes

### ❌ JWT encrypts data

JWTs are usually **signed**, not encrypted.

Anyone with the token can read the payload.

---

### ❌ Store sensitive information in the payload

The payload is visible after decoding.

Store only the information needed by the application.

---

### ❌ JWT is always better than sessions

JWTs solve different problems.

Many applications successfully use server-side sessions.

Choose based on your architecture, not popularity.

---

# 💡 Did You Know?

Many large systems use **both** approaches.

For example:

- A web dashboard may use secure session cookies.
- A mobile application may use JWTs.

Different clients can authenticate differently while using the same backend.

---

# Key Takeaways

- JWT is a signed token used for authentication.
- Clients send the token with future requests.
- JWT consists of a header, payload, and signature.
- The payload is readable, so avoid storing sensitive data.
- JWTs are commonly used for APIs and mobile applications.

---

## 🚀 What's Next?

Users can now authenticate with a JWT.

But...

**How can users log in with Google, GitHub, or Microsoft without creating another password?**

➡️ **Next Chapter:** OAuth 2.0