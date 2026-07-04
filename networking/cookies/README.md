# Cookies

> Part of the **Engineering Mastery** handbook.

## ⏱️ Quick Facts

| | |
|---|---|
| **Read Time** | 10 minutes |
| **Difficulty** | 🟢 Beginner |
| **Prerequisites** | HTTP Status Codes |

---

## 📍 Where We Are in the Request Journey

```text
Client
   │
   ▼
HTTP Request
   │
   ▼
Server Response
   │
   ▼
🍪 Cookie Stored
   │
   ▼
Future Requests Automatically Include the Cookie
```

---

## Imagine This...

You visit your favorite coffee shop.

The cashier gives you a loyalty card.

```
Customer

↓

Receives Loyalty Card

↓

Returns Tomorrow

↓

Shows Same Card
```

The cashier recognizes you because you brought back the same card.

A cookie works in a very similar way.

---

# 💡 Why This Matters

HTTP is **stateless**.

That means the server doesn't automatically remember previous requests.

Without cookies:

- You would need to log in on every page.
- Shopping carts would disappear.
- Websites couldn't remember your preferences.

Cookies help solve this problem.

---

# What Is a Cookie?

A **cookie** is a small piece of data that a server asks the browser to store.

The browser automatically sends that cookie back with future requests to the same website.

Think of it as a small note that helps the server recognize returning clients.

---

# How Cookies Work

### First Request

```
Browser

↓

GET /login

↓

Server
```

The server responds:

```http
Set-Cookie: sessionId=abc123
```

The browser stores it.

---

### Future Request

Later, the browser requests another page.

```http
GET /profile

Cookie: sessionId=abc123
```

The browser automatically includes the cookie.

The server can now recognize the user.

---

# Behind the Scenes

```text
Client
   │
   │ Request
   ▼
Server
   │
   │ Set-Cookie
   ▼
Browser Stores Cookie
   │
   │
Future Request
   │
Cookie Sent Automatically
   ▼
Server Recognizes Client
```

---

# What Can Cookies Store?

Cookies commonly store:

- Session identifiers
- User preferences
- Theme (Light/Dark)
- Language settings
- Analytics identifiers

A cookie usually stores a small identifier—not large amounts of application data.

---

# Cookie Attributes

Cookies include additional settings.

| Attribute | Purpose |
|-----------|---------|
| Expires | Expiration date |
| Max-Age | Lifetime in seconds |
| Secure | Send only over HTTPS |
| HttpOnly | Prevent JavaScript access |
| SameSite | Helps protect against CSRF attacks |

You don't need to memorize these yet.

You'll use them frequently when building authentication systems.

---

# Production Perspective

Suppose Alice logs in.

The server responds:

```http
HTTP/1.1 200 OK

Set-Cookie: sessionId=abc123
```

Alice visits:

```
/dashboard
```

Her browser automatically sends:

```http
Cookie: sessionId=abc123
```

The server recognizes the session and serves the dashboard without asking Alice to log in again.

---

# Common Misconceptions

### ❌ Cookies store passwords

They shouldn't.

Cookies usually store a session identifier or another small token.

---

### ❌ Cookies are only used for authentication

Cookies can also remember:

- Language
- Theme
- Shopping cart preferences
- Analytics information

---

### ❌ Browsers require JavaScript for cookies

No.

Browsers handle cookies automatically through HTTP headers.

---

# 💡 Did You Know?

When you clear your browser cookies, many websites log you out.

That's because the server no longer receives the session identifier it was using to recognize you.

---

# Key Takeaways

- Cookies are small pieces of data stored by the browser.
- Servers create cookies using the `Set-Cookie` header.
- Browsers automatically send cookies with future requests.
- Cookies help applications remember users across multiple requests.
- Cookies often store identifiers, not sensitive user data.

---

## 🚀 What's Next?

Cookies help identify a browser.

But...

**Where is the actual user session stored?**

➡️ **Next Chapter:** Sessions