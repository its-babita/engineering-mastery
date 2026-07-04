# Ports

> Part of the **Engineering Mastery** handbook.

## ⏱️ Quick Facts

| | |
|---|---|
| **Read Time** | 8–10 minutes |
| **Difficulty** | 🟢 Beginner |
| **Prerequisites** | IP Address |

---

## Imagine This...

DNS helped your browser find the server.

```
shopsphere.example

↓

203.0.113.10
```

Now your computer knows **which server** to contact.

But here's another question:

> **How does the server know which application should handle your request?**

That's where **ports** come in.

---

# 💡 Why This Matters

A single server can run many applications at the same time.

For example:

- A web server
- A database
- An SSH server
- A mail server

They all share the same IP address.

Ports make sure requests reach the correct application.

---

# What Is a Port?

A **port** is a logical communication endpoint used by applications on a device.

Think of an IP address as an apartment building.

A port is the apartment number.

```
IP Address

↓

Port

↓

Application
```

Without a port, the operating system wouldn't know which application should receive incoming data.

---

# 🧠 Mental Model

Imagine this address:

```
Sunrise Apartments

Apartment 302
```

The apartment building tells the courier **where** to go.

The apartment number tells them **which door** to knock on.

Likewise:

```
203.0.113.10

Port 443
```

- IP Address → Server
- Port → Application

Both are needed.

---

# How Ports Work

Suppose a server is running:

| Application | Port |
|-------------|-----:|
| Website | 443 |
| HTTP Website | 80 |
| SSH | 22 |
| PostgreSQL | 5432 |

When a request arrives at:

```
203.0.113.10:443
```

The operating system sends it to the web server.

When a request arrives at:

```
203.0.113.10:5432
```

It goes to PostgreSQL instead.

The IP address is the same.

The destination application is different.

---

# Where Do You See Ports?

Most of the time, browsers hide common ports.

For example:

```
https://shopsphere.example
```

actually uses:

```
https://shopsphere.example:443
```

Similarly,

```
http://shopsphere.example
```

uses:

```
http://shopsphere.example:80
```

Since these are standard ports, your browser automatically uses them.

---

# When Is the Port Visible?

If an application runs on a non-standard port, you must specify it.

Example:

```
http://localhost:3000
```

Here:

- Host → `localhost`
- Port → `3000`

This is common during local development.

---

# Common Ports

| Port | Service |
|------:|---------|
| 20/21 | FTP |
| 22 | SSH |
| 25 | SMTP |
| 53 | DNS |
| 80 | HTTP |
| 443 | HTTPS |
| 3306 | MySQL |
| 5432 | PostgreSQL |
| 6379 | Redis |
| 27017 | MongoDB |

> You don't need to memorize these today. You'll become familiar with them naturally as you build applications.

---

# Behind the Scenes

When you open:

```
https://shopsphere.example
```

your browser roughly performs:

```text
URL
 │
 ▼
DNS Lookup
 │
 ▼
IP Address
 │
 ▼
Port 443
 │
 ▼
Web Server
 │
 ▼
HTTP Response
```

The operating system listens for incoming connections and forwards them to the correct application based on the port.

---

# Production Perspective

Production servers often host multiple services.

For example:

| Service | Port |
|---------|-----:|
| Nginx | 443 |
| Backend API | 8080 |
| PostgreSQL | 5432 |
| Redis | 6379 |

Users only interact with ports **80** or **443**.

Internal services usually communicate through private ports that aren't exposed to the public internet.

This improves both security and architecture.

---

# Common Mistakes

### ❌ IP Address and Port Are the Same

They work together, but they solve different problems.

- IP Address → Which device?
- Port → Which application?

---

### ❌ Every Application Uses Port 80

Only web servers typically use port 80.

Databases, caches, and other services use different ports.

---

### ❌ Open Every Port

Only expose the ports that are actually needed.

Keeping unnecessary ports closed reduces the attack surface of your server.

---

# Key Takeaways

- An IP address identifies a device.
- A port identifies an application running on that device.
- Multiple applications can share one IP address by listening on different ports.
- Browsers automatically use standard ports like 80 and 443.
- Internal services usually communicate through private ports.

---

## 🚀 What's Next?

Now we know:

- Which server to contact ✅
- Which application to contact ✅

But...

**How does the data actually travel between two devices?**

Should every packet be guaranteed to arrive?

Or is speed more important than reliability?

➡️ **Next Chapter:** TCP vs UDP