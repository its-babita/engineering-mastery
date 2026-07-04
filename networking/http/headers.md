# HTTP Headers

HTTP headers provide additional information about a request or response.

Think of them as **metadata**.

They don't contain the main data itself.

Instead, they describe the data or tell the client and server how to handle the request.

---

## 🧠 Mental Model

Imagine shipping a package.

Inside the package:

```
Laptop
```

Outside the package:

```
From: ShopSphere
To: Alice
Fragile
Priority Delivery
```

Those labels aren't the package.

They describe the package.

HTTP headers work the same way.

---

# Why Headers Matter

Headers help answer questions like:

- What type of data is being sent?
- Is the user authenticated?
- Can this response be cached?
- Which language does the client prefer?

Without headers, communication would be much less organized.

---

# Request Headers

A client sends request headers to provide additional information to the server.

Example:

```http
GET /products HTTP/1.1
Host: api.shopsphere.example
Authorization: Bearer <token>
Accept: application/json
```

---

# Response Headers

The server sends response headers back to the client.

Example:

```http
HTTP/1.1 200 OK

Content-Type: application/json
Cache-Control: no-cache
Content-Length: 245
```

These help the client understand how to process the response.

---

# Common Request Headers

| Header | Purpose |
|---------|---------|
| Host | Target server |
| Authorization | User credentials or token |
| Accept | Preferred response format |
| User-Agent | Information about the client |
| Cookie | Sends stored cookies |

---

# Common Response Headers

| Header | Purpose |
|---------|---------|
| Content-Type | Type of returned data |
| Content-Length | Size of the response |
| Cache-Control | Caching rules |
| Set-Cookie | Creates or updates cookies |
| Location | Redirect destination |

---

# Production Perspective

A request to an API might include:

```http
GET /api/products

Authorization: Bearer eyJ...
Accept: application/json
```

The server responds with:

```http
HTTP/1.1 200 OK

Content-Type: application/json
Cache-Control: max-age=300
```

The client now knows:

- The request is authenticated.
- The response contains JSON.
- The response may be cached for five minutes.

---

# Common Mistakes

### ❌ Headers contain the main data

No.

The body contains the main data.

Headers only provide additional information.

---

### ❌ Every request uses the same headers

Different requests require different headers depending on the application.

---

### ❌ Headers are only for browsers

Mobile apps, backend services, and APIs all use HTTP headers extensively.

---

# Key Takeaways

- Headers provide metadata about requests and responses.
- Clients send request headers.
- Servers send response headers.
- Headers control authentication, caching, content types, and more.
- They are essential for modern web applications and APIs.

---

## 🚀 What's Next?

The server has processed our request.

Now it needs to tell us the result.

Was it successful?

Was the resource not found?

Did something go wrong?

➡️ **Next:** HTTP Status Codes