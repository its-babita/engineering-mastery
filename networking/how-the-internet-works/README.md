# How the Internet Works

> Part of the **Engineering Mastery** handbook.

## ⏱️ Quick Facts

| | |
|---|---|
| **Read Time** | 10 minutes |
| **Difficulty** | 🟢 Beginner |
| **Prerequisites** | Backend Overview, Client–Server Architecture |

---

## Imagine This...

You open your browser and type:

```
https://github.com
```

Within seconds, GitHub appears.

It feels almost magical.

But behind that simple action, your request travels across cities, countries, and even continents before reaching GitHub's servers.

Understanding that journey is the key to understanding modern web development.

---

## 💡 Why This Matters

Every website, mobile app, and API depends on the internet.

As a backend engineer, you'll constantly work with requests coming from users around the world. Knowing how those requests travel helps you build faster, more reliable, and more secure applications.

---

# What Is the Internet?

The **Internet** is a global network of computers connected together.

Instead of one giant computer storing everything, millions of computers communicate using common networking rules called **protocols**.

Think of the internet as the world's largest road network.

Instead of cars, it carries data.

---

# The Journey of a Request

When you visit a website, your request follows a series of steps.

```text
You
 │
 ▼
Browser
 │
 ▼
Internet
 │
 ▼
Website Server
 │
 ▼
Response
 │
 ▼
Browser
```

This entire process usually takes only a few milliseconds.

---

# How Data Travels

Imagine sending a parcel to a friend.

You don't build a private road.

The parcel travels through different roads, cities, and delivery centers before reaching its destination.

The internet works the same way.

Your data passes through multiple networks before arriving at the correct server.

---

# Who Makes This Possible?

Several components work together.

| Component | Responsibility |
|-----------|----------------|
| Browser | Sends the request |
| ISP | Connects you to the internet |
| Routers | Forward data to the next destination |
| Server | Processes the request |
| Browser | Displays the response |

Each has a small but important role.

---

# A Real Example

Imagine opening YouTube.

Your browser:

1. Sends a request.
2. The request travels through your Internet Service Provider (ISP).
3. Multiple routers forward it toward YouTube's servers.
4. YouTube processes the request.
5. The response travels back.
6. Your browser displays the page.

All of this happens so quickly that it feels instant.

---

# Why Doesn't Data Travel in One Jump?

The internet is too large for one direct connection.

Instead, data moves through many intermediate devices called **routers**.

```text
Your Laptop
      │
      ▼
Home Router
      │
      ▼
Internet Provider
      │
      ▼
Several Routers
      │
      ▼
Website Server
```

Each router simply decides:

> "What's the next best place to send this data?"

---

# Production Perspective

Companies like Google, Netflix, and Amazon have servers in multiple regions around the world.

Instead of sending every request to one location, they route users to the nearest or healthiest server.

Benefits include:

- Faster response times
- Lower latency
- Better reliability
- Improved user experience

This is one reason websites feel fast even with millions of users.

---

# Common Misconceptions

### ❌ The Internet and the Web are the same

They're different.

- **Internet** → The global network.
- **Web** → One service that runs on the internet.

Email, online games, and video calls also use the internet, but they are not the web.

---

### ❌ Websites live inside your browser

Browsers don't store entire websites.

They request the data from remote servers whenever you visit a page.

---

# Key Takeaways

- The internet is a global network of connected computers.
- Data travels through multiple networks, not one direct path.
- Routers help forward requests toward their destination.
- Servers process requests and return responses.
- Modern applications rely on this communication every second.

---

## 🚀 What's Next?

You now know **how a request travels across the internet**.

But one question remains...

When you type:

```
https://github.com
```

How does your computer know where **github.com** actually is?

➡️ **Next Chapter:** URL & URI