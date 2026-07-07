# Error Handling

> Part of the **Engineering Mastery** handbook.

## ⏱️ Quick Facts

| | |
|---|---|
| **Read Time** | 10–12 minutes |
| **Difficulty** | 🟢 Beginner |
| **Prerequisites** | Request Validation |

---

## 💡 Why This Matters

No application is error-free.

A request can fail because:

- The user entered invalid data.
- A resource doesn't exist.
- The database is unavailable.
- An external API is down.
- A bug exists in the application.

A production API should handle these situations gracefully instead of crashing or exposing internal details.

---

# What Is Error Handling?

**Error handling** is the process of detecting, managing, and responding to errors in a predictable way.

Good error handling helps:

- Users understand what went wrong.
- Developers debug issues faster.
- Applications remain stable.

---

# A Simple Flow

```text
Client Request
      │
      ▼
Application
      │
      ▼
Did an Error Occur?
      │
 ┌────┴────┐
 │         │
 ▼         ▼
No        Yes
 │         │
 ▼         ▼
Response  Handle Error
           │
           ▼
     Return Safe Response
```

---

# Types of Errors

## Client Errors (4xx)

The client sent an invalid request.

Examples:

- Missing required fields
- Invalid email
- Unauthorized request
- Resource not found

Typical responses:

```http
400 Bad Request
401 Unauthorized
403 Forbidden
404 Not Found
```

---

## Server Errors (5xx)

The server couldn't complete the request.

Examples:

- Database connection failed
- Unexpected exception
- Third-party service unavailable

Typical responses:

```http
500 Internal Server Error
503 Service Unavailable
```

---

# Good Error Responses

Instead of returning:

```json
{
  "error": true
}
```

Return something meaningful:

```json
{
  "success": false,
  "message": "Product not found."
}
```

For validation errors:

```json
{
  "success": false,
  "message": "Validation failed.",
  "errors": {
    "price": "Price must be greater than 0."
  }
}
```

Consistency helps frontend developers handle errors correctly.

---

# Don't Expose Internal Errors

Avoid sending stack traces or database errors to clients.

❌ Don't return:

```text
DatabaseError:
Connection refused at line 128...
```

Instead:

```json
{
  "success": false,
  "message": "Something went wrong."
}
```

Log the detailed error on the server, but return a safe message to the client.

---

# Centralized Error Handling

Instead of handling errors differently in every route:

```text
Route A
Route B
Route C
```

Use one centralized error handler.

```text
Request
   │
   ▼
Business Logic
   │
   ▼
Central Error Handler
   │
   ▼
Consistent Response
```

This keeps your API consistent and easier to maintain.

---

# Production Example

A client requests:

```http
GET /products/9999
```

The product doesn't exist.

Response:

```http
404 Not Found
```

```json
{
  "success": false,
  "message": "Product not found."
}
```

If the database is temporarily unavailable:

```http
500 Internal Server Error
```

```json
{
  "success": false,
  "message": "An unexpected error occurred."
}
```

Notice that the client receives useful information without exposing internal implementation details.

---

# Logging Errors

Users need friendly messages.

Developers need detailed logs.

A production system should:

- Return safe responses to clients.
- Log detailed information for debugging.
- Include request identifiers when possible.

Never rely on client responses for debugging production issues.

---

# Best Practices

- Use appropriate HTTP status codes.
- Keep error responses consistent.
- Log errors on the server.
- Avoid exposing sensitive information.
- Handle expected errors gracefully.

---

# Common Mistakes

### ❌ Returning 200 for errors

If the request failed, use the correct error status code.

---

### ❌ Returning stack traces

Clients don't need internal implementation details.

Log them internally instead.

---

### ❌ Using different error formats

Every endpoint should return errors in a consistent structure.

---

# 💡 Did You Know?

Many production systems attach a unique request ID to every request.

When a user reports an issue, developers can use that ID to quickly locate the corresponding logs.

---

# Key Takeaways

- Errors are a normal part of backend development.
- Return meaningful and consistent error responses.
- Use the correct HTTP status codes.
- Never expose internal errors to clients.
- Log detailed errors for debugging.

---

## 🚀 What's Next?

Your API now validates requests and handles failures.

The next challenge is evolving your API without breaking existing clients.

➡️ **Next Chapter:** API Versioning