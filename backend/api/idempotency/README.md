# Idempotency

> Part of the **Engineering Mastery** handbook.

## ⏱️ Quick Facts

| | |
|---|---|
| **Read Time** | 10–12 minutes |
| **Difficulty** | 🟡 Intermediate |
| **Prerequisites** | Rate Limiting |

---

## 💡 Why This Matters

Imagine you're buying a laptop online.

You click **Pay**.

The internet becomes slow.

You're unsure whether the payment succeeded, so you click **Pay** again.

Without protection, the payment might be processed twice.

That's a serious problem.

Idempotency helps ensure that repeating the same request doesn't create duplicate operations.

---

# What Is Idempotency?

An operation is **idempotent** if performing it multiple times produces the same final result as performing it once.

Think of a light switch.

```
OFF

↓

Turn OFF

↓

Still OFF

↓

Turn OFF Again

↓

Still OFF
```

Turning it off repeatedly doesn't change the final state.

---

# Why Does It Matter?

Networks are unreliable.

A client might retry a request because:

- The connection timed out.
- The server responded too slowly.
- The user clicked twice.
- A mobile device lost connectivity.
- An automatic retry mechanism was triggered.

Your API should handle these situations safely.

---

# HTTP Methods and Idempotency

| Method | Idempotent? |
|---------|-------------|
| GET | ✅ Yes |
| PUT | ✅ Yes |
| DELETE | ✅ Yes |
| POST | ❌ Usually No |
| PATCH | Depends on the operation |

Example:

```
GET /products/10
```

Requesting the same product multiple times doesn't change the data.

Now consider:

```
POST /orders
```

Sending it twice might create two separate orders.

---

# A Real Example

Without idempotency:

```
POST /payments

↓

Payment Created

↓

Client Retries

↓

Second Payment Created ❌
```

With idempotency:

```
POST /payments

↓

Payment Created

↓

Client Retries

↓

Existing Payment Returned ✅
```

The payment is processed only once.

---

# Idempotency Keys

A common solution is an **Idempotency-Key**.

Example:

```http
POST /payments

Idempotency-Key: abc123
```

Flow:

```
Client

↓

Generate Unique Key

↓

Server Receives Request

↓

Has This Key Been Seen?

        │
   ┌────┴────┐
   │         │
  No        Yes
   │         │
   ▼         ▼
Process   Return Previous Response
```

The server stores the key and remembers the response.

If the same request arrives again with the same key, it returns the original result instead of processing it again.

---

# Production Example

Imagine a payment API.

Request:

```http
POST /payments

Idempotency-Key: pay-001
```

Response:

```json
{
  "paymentId": 123,
  "status": "Success"
}
```

If the client retries using the same key:

```http
POST /payments

Idempotency-Key: pay-001
```

The server returns:

```json
{
  "paymentId": 123,
  "status": "Success"
}
```

No duplicate payment is created.

---

# Where Is Idempotency Useful?

Idempotency is especially important for:

- Payment processing
- Order creation
- Ticket booking
- Inventory updates
- Financial transactions

These operations should never be executed twice accidentally.

---

# Best Practices

- Use unique idempotency keys for retryable operations.
- Store keys for a limited period.
- Return the original response for duplicate requests.
- Apply idempotency to operations that create or modify critical data.
- Clearly document idempotent endpoints.

---

# Common Mistakes

### ❌ Assuming retries never happen

Network failures and client retries are common in distributed systems.

---

### ❌ Ignoring duplicate requests

Duplicate processing can lead to:

- Double payments
- Duplicate orders
- Incorrect inventory
- Poor user experience

---

### ❌ Reusing the same idempotency key for unrelated operations

Each logical operation should have its own unique key.

---

# 💡 Did You Know?

Many payment providers require idempotency keys for payment requests.

This ensures customers aren't charged multiple times if a request is retried.

---

# Key Takeaways

- Idempotency makes retrying requests safe.
- GET, PUT, and DELETE are naturally idempotent.
- POST often requires additional protection.
- Idempotency keys prevent duplicate processing.
- Critical operations should be designed with retries in mind.

---

## 🎉 Module Complete

You now understand the foundations of building production-ready REST APIs:

- REST principles
- API design
- Pagination
- Filtering & Sorting
- Request Validation
- Error Handling
- API Versioning
- Rate Limiting
- Idempotency

These concepts apply regardless of the backend framework or programming language.

➡️ **Next Module:** Database Engineering