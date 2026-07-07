# Rate Limiting

> Part of the **Engineering Mastery** handbook.

## ⏱️ Quick Facts

| | |
|---|---|
| **Read Time** | 10–12 minutes |
| **Difficulty** | 🟢 Beginner |
| **Prerequisites** | API Versioning |

---

## 💡 Why This Matters

Imagine your login API receives:

```
1 request

↓

10 requests

↓

1,000 requests

↓

100,000 requests
```

Should your server continue accepting every request?

Probably not.

Without limits:

- Servers become overloaded.
- APIs become slow.
- Brute-force attacks become easier.
- Infrastructure costs increase.

Rate limiting helps protect your application.

---

# What Is Rate Limiting?

**Rate limiting** restricts how many requests a client can make within a specific period of time.

Example:

```
100 requests

per

1 minute
```

If the limit is exceeded, the server temporarily rejects additional requests.

---

# A Simple Example

Suppose an API allows:

```
5 requests per minute
```

A client sends:

```
✅ Request 1

✅ Request 2

✅ Request 3

✅ Request 4

✅ Request 5

❌ Request 6
```

The sixth request is rejected until the limit resets.

---

# Why Rate Limiting?

Rate limiting helps:

- Protect servers
- Prevent abuse
- Reduce spam
- Slow brute-force attacks
- Improve fairness among users

It's one of the simplest ways to improve API reliability.

---

# What Happens When the Limit Is Reached?

A common response is:

```http
429 Too Many Requests
```

Example:

```json
{
  "success": false,
  "message": "Rate limit exceeded. Please try again later."
}
```

The client knows the request wasn't processed because it exceeded the allowed request rate.

---

# Common Strategies

## Fixed Window

Example:

```
100 requests

every

1 minute
```

Easy to understand and implement.

---

## Sliding Window

Instead of resetting at fixed intervals, the server continuously evaluates requests over a moving time window.

This produces smoother rate limiting.

---

## Token Bucket

Imagine a bucket filled with tokens.

Each request consumes one token.

Tokens refill over time.

```
Bucket

🟢🟢🟢🟢🟢

↓

Request

↓

🟢🟢🟢🟢
```

This allows occasional bursts while still enforcing an average request rate.

---

# Production Example

Imagine a login endpoint.

Limit:

```
POST /login

5 requests

per minute

per IP address
```

If someone repeatedly guesses passwords:

```
Attempt 1 ✅

Attempt 2 ✅

Attempt 3 ✅

Attempt 4 ✅

Attempt 5 ✅

Attempt 6 ❌

429 Too Many Requests
```

This slows automated attacks.

---

# Where Can You Apply Rate Limiting?

Rate limiting is useful for:

- Login endpoints
- Password reset requests
- Public APIs
- Search endpoints
- File uploads
- Payment APIs

Different endpoints may have different limits.

---

# Best Practices

- Return **429 Too Many Requests** when limits are exceeded.
- Set limits based on endpoint sensitivity.
- Combine rate limiting with authentication.
- Log repeated violations.
- Use distributed storage (such as Redis) when running multiple server instances.

---

# Common Mistakes

### ❌ Applying the same limit everywhere

A login endpoint and a product listing endpoint often require different limits.

---

### ❌ Returning 500 errors

Exceeding a rate limit isn't a server failure.

Use:

```http
429 Too Many Requests
```

---

### ❌ Ignoring distributed deployments

If your application runs on multiple servers, store rate limit data in shared storage instead of server memory.

---

# 💡 Did You Know?

Many public APIs publish their rate limits so developers know how many requests they can safely make.

Some also return headers indicating:

- Remaining requests
- Limit value
- Time until reset

This helps clients avoid hitting the limit unexpectedly.

---

# Key Takeaways

- Rate limiting controls how frequently clients can access an API.
- It protects applications from abuse and overload.
- Return **429 Too Many Requests** when limits are exceeded.
- Different endpoints may require different limits.
- Shared storage is important in distributed systems.

---

## 🚀 What's Next?

Some operations should happen **only once**, even if the client retries the request.

For example:

- Creating a payment
- Placing an order
- Charging a credit card

The next chapter explores how APIs safely handle retries.

➡️ **Next Chapter:** Idempotency