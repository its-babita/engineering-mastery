# Request Validation

> Part of the **Engineering Mastery** handbook.

## ⏱️ Quick Facts

| | |
|---|---|
| **Read Time** | 10–12 minutes |
| **Difficulty** | 🟢 Beginner |
| **Prerequisites** | Filtering & Sorting |

---

## 💡 Why This Matters

Every API receives data from clients.

Examples:

- User registration
- Login
- Product creation
- Order placement
- Profile updates

Can you trust that data?

No.

Clients can send:

- Missing fields
- Invalid values
- Wrong data types
- Unexpected properties
- Malicious input

Validation ensures your application accepts only valid data.

---

# What Is Request Validation?

**Request validation** is the process of checking incoming data before your application processes it.

If the data is invalid, the request should be rejected with a clear error message.

Think of validation as a security checkpoint.

```
Client Request
      │
      ▼
Validation
      │
 ┌────┴────┐
 │         │
 ▼         ▼
Valid    Invalid
 │         │
 ▼         ▼
Continue  Return Error
```

---

# Why Validate Requests?

Validation helps you:

- Prevent invalid data
- Improve API reliability
- Protect your database
- Improve user experience
- Reduce unexpected application errors

Without validation, bad data can spread throughout your system.

---

# Example

Suppose your API creates a new user.

Request:

```json
{
  "name": "Alice",
  "email": "alice@example.com",
  "age": 25
}
```

This looks valid.

Now imagine receiving:

```json
{
  "name": "",
  "email": "not-an-email",
  "age": -5
}
```

Without validation, incorrect data could be stored in the database.

---

# Common Validation Rules

### Required Fields

```text
Email is required.
Password is required.
```

---

### Data Type

```text
Age must be a number.
```

---

### Length

```text
Password must be at least 8 characters.
```

---

### Format

```text
Email must be a valid email address.
```

---

### Value Range

```text
Age must be greater than 0.
```

---

### Allowed Values

```text
Role must be:

admin
customer
manager
```

---

# Validation Flow

```text
Client
   │
   ▼
API Receives Request
   │
   ▼
Validate Data
   │
 ┌────┴────┐
 │         │
 ▼         ▼
Valid    Invalid
 │         │
 ▼         ▼
Business  400 Bad Request
Logic
```

Notice that validation happens **before** business logic.

---

# Example Error Response

```http
HTTP/1.1 400 Bad Request
```

```json
{
  "success": false,
  "message": "Validation failed.",
  "errors": {
    "email": "Invalid email address.",
    "password": "Must contain at least 8 characters."
  }
}
```

Clear error messages help frontend developers and API consumers fix problems quickly.

---

# Production Example

Suppose an e-commerce API receives:

```json
{
  "name": "",
  "price": -500,
  "stock": "many"
}
```

The backend should reject the request immediately instead of saving invalid data.

This keeps the database clean and prevents downstream bugs.

---

# Popular Validation Libraries

Different frameworks provide different tools.

### JavaScript / Node.js

- Zod
- Joi
- express-validator

### TypeScript

Zod is a popular choice because it provides runtime validation and strong type inference.

Choose the tool that fits your stack and team.

---

# Best Practices

- Validate every incoming request.
- Validate on the server, even if the frontend already validates.
- Return clear error messages.
- Keep validation rules close to your API layer.
- Reject unknown or unexpected fields when appropriate.

---

# Common Mistakes

### ❌ Trusting frontend validation

Frontend validation improves user experience.

Backend validation protects your application.

You need both.

---

### ❌ Returning vague error messages

Avoid:

```json
{
  "error": true
}
```

Prefer:

```json
{
  "message": "Email is required."
}
```

---

### ❌ Mixing validation with business logic

Keep validation separate from your core application logic.

This makes your code easier to maintain and test.

---

# 💡 Did You Know?

Most modern backend frameworks perform validation before the request reaches controllers or route handlers.

This means invalid requests are rejected early, reducing unnecessary processing.

---

# Key Takeaways

- Never trust client input.
- Validate every incoming request.
- Reject invalid data before executing business logic.
- Return meaningful validation errors.
- Backend validation is essential, even if the frontend validates data.

---

## 🚀 What's Next?

Even with validation, unexpected problems can still occur.

Databases can fail.

External services can be unavailable.

Business rules can be violated.

The next chapter explores how to handle these situations gracefully.

➡️ **Next Chapter:** Error Handling