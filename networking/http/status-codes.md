# HTTP Status Codes

HTTP status codes are three-digit numbers returned by the server to indicate the result of a request.

Instead of reading the entire response, a client can quickly understand whether the request succeeded, failed, or requires another action.

---

## 🧠 Mental Model

Imagine ordering food at a restaurant.

You place an order.

The waiter comes back with a response.

```
✅ Your order is ready.

❌ That item isn't available.

⚠️ We need you to sign in first.
```

HTTP status codes work the same way.

They are short messages that describe the outcome of a request.

---

# Status Code Categories

The first digit tells you the general result.

| Range | Meaning |
|--------|---------|
| 1xx | Informational |
| 2xx | Success |
| 3xx | Redirection |
| 4xx | Client Error |
| 5xx | Server Error |

Most developers work with **2xx**, **4xx**, and **5xx** responses.

---

# 2xx — Success

The request was processed successfully.

## 200 OK

The request succeeded.

```http
GET /products

HTTP/1.1 200 OK
```

Common for:

- Fetching products
- Viewing user profiles
- Loading dashboards

---

## 201 Created

A new resource was successfully created.

```http
POST /users

HTTP/1.1 201 Created
```

Common for:

- User registration
- Creating orders
- Uploading files

---

## 204 No Content

The request succeeded, but there's nothing to return.

Example:

```http
DELETE /products/5

HTTP/1.1 204 No Content
```

---

# 3xx — Redirection

The client needs to perform another action.

## 301 Moved Permanently

The resource has permanently moved.

Browsers automatically use the new location.

---

## 302 Found

The resource is temporarily available at another location.

---

# 4xx — Client Errors

Something is wrong with the request.

---

## 400 Bad Request

The request is invalid.

Examples:

- Missing required fields
- Invalid JSON
- Incorrect data format

---

## 401 Unauthorized

Authentication is required.

Example:

```
Missing JWT token
```

---

## 403 Forbidden

The client is authenticated,

but doesn't have permission.

Example:

```
Regular user trying to access an admin page
```

---

## 404 Not Found

The requested resource doesn't exist.

Example:

```http
GET /products/99999

↓

404 Not Found
```

---

# 5xx — Server Errors

The request reached the server,

but the server couldn't complete it.

---

## 500 Internal Server Error

An unexpected error occurred.

Examples:

- Application crash
- Unhandled exception
- Unexpected bug

---

## 503 Service Unavailable

The server is temporarily unavailable.

Common causes:

- Maintenance
- High traffic
- Server overload

---

# Production Example

Suppose a user logs in.

## Success

```http
POST /login

↓

200 OK
```

---

## Wrong Password

```http
POST /login

↓

401 Unauthorized
```

---

## Missing Required Field

```http
POST /login

↓

400 Bad Request
```

---

## Server Failure

```http
POST /login

↓

500 Internal Server Error
```

---

# Choosing the Right Status Code

Returning the correct status code helps:

- Frontend developers
- Mobile applications
- API consumers
- Monitoring systems

For example:

Returning:

```
200 OK
```

for an error makes debugging difficult.

Returning:

```
404 Not Found
```

immediately tells the client what happened.

---

# Common Mistakes

### ❌ Returning 200 for every request

Use status codes that accurately describe the outcome.

---

### ❌ Using 500 for client mistakes

If the client sends invalid data,

return a **4xx** status,

not a server error.

---

### ❌ Ignoring status codes

Status codes are part of the API contract.

Clients rely on them to make decisions.

---

# Key Takeaways

- Status codes describe the outcome of an HTTP request.
- 2xx indicates success.
- 3xx indicates redirection.
- 4xx indicates client errors.
- 5xx indicates server errors.
- Choosing the correct status code improves API design and debugging.

---

## 🚀 What's Next?

HTTP is stateless.

So how does a website remember that you're logged in after making multiple requests?

The answer starts with **Cookies**.

➡️ **Next Chapter:** Cookies