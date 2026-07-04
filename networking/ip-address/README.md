# IP Address

> Part of the **Engineering Mastery** handbook.

## ⏱️ Quick Facts

| | |
|---|---|
| **Read Time** | 10 minutes |
| **Difficulty** | 🟢 Beginner |
| **Prerequisites** | DNS |

---

## Imagine This...

DNS has translated:

```
shopsphere.example
```

into

```
203.0.113.10
```

But...

What is this number?

Why can't computers simply use names?

---

# 💡 Why This Matters

Every device connected to the internet needs an address.

Without an address:

- A browser wouldn't know where to send a request.
- A server wouldn't know where to send a response.

An **IP address** makes communication possible.

---

# What Is an IP Address?

An **IP (Internet Protocol) Address** is a unique address assigned to a device on a network.

Think of it as a postal address.

Just as a delivery company needs your home address,

computers need an IP address to send and receive data.

---

# 🧠 Mental Model

Imagine sending a package.

The courier needs:

```
House Number
Street
City
Country
```

Without an address,

the package has nowhere to go.

The internet works the same way.

```
Domain Name

↓

IP Address

↓

Server
```

The domain name is for humans.

The IP address is for computers.

---

# IPv4 Example

A typical IPv4 address looks like this:

```
192.168.1.10
```

It consists of four numbers separated by dots.

Each number ranges from **0 to 255**.

---

# IPv6 Example

Because the internet has billions of devices,

IPv4 addresses are limited.

IPv6 provides a much larger address space.

Example:

```
2001:db8:85a3::8a2e:370:7334
```

Don't worry about remembering the format.

Just know that:

- IPv4 is older and still widely used.
- IPv6 is newer and solves address exhaustion.

---

# How IP Addresses Fit Into the Request Journey

When you visit:

```
https://shopsphere.example
```

the flow becomes:

```text
URL
 │
 ▼
DNS
 │
 ▼
IP Address
 │
 ▼
Connect to Server
```

DNS answers:

> "Which IP address should I use?"

The browser then connects to that address.

---

# Public vs Private IP Addresses

## Public IP

A public IP is visible on the internet.

Example:

```
203.0.113.10
```

Web servers usually have public IP addresses.

---

## Private IP

A private IP is used inside local networks.

Example:

```
192.168.1.25
```

Your laptop, phone, or printer often uses a private IP at home or in the office.

These addresses are not directly reachable from the internet.

---

# Static vs Dynamic IP Addresses

| Static IP | Dynamic IP |
|-----------|------------|
| Doesn't change often | Can change over time |
| Common for servers | Common for home internet connections |

Production servers often use static IPs because clients need a stable destination.

---

# Production Perspective

Modern applications rarely rely on a single server.

Instead:

```text
User

    │

    ▼

Load Balancer

    │

 ┌──┴──┐
 │     │
 ▼     ▼

Server A   Server B

 │           │
 └─────┬─────┘
       ▼
   Database
```

Each server has its own IP address.

Users usually never see these addresses because DNS and load balancers handle the routing.

---

# Common Misconceptions

### ❌ IP addresses identify people

An IP address identifies a network connection or device.

It does **not** uniquely identify a specific person.

---

### ❌ Every device has a public IP

Most personal devices use private IP addresses behind a router.

The router communicates with the internet using a public IP.

---

### ❌ Domain names replace IP addresses

No.

DNS simply helps humans avoid remembering numbers.

The underlying communication still happens using IP addresses.

---

# Key Takeaways

- Every device on a network has an IP address.
- Computers communicate using IP addresses, not domain names.
- DNS translates domain names into IP addresses.
- IPv4 and IPv6 are the two main versions.
- Public and private IPs serve different purposes.

---

## 🚀 What's Next?

Now we know **where** the server is.

But...

How does one server run many different services at the same IP address?

The answer is **Ports**.

➡️ **Next Chapter:** Ports