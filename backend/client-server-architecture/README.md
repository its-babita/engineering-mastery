# Client–Server Architecture

> Part of the **Engineering Mastery** handbook.

## ⏱️ Quick Facts

| | |
|---|---|
| **Read Time** | 10–12 minutes |
| **Difficulty** | 🟢 Beginner |
| **Prerequisites** | Backend Overview |

---

## Imagine This...

You open Netflix.

The homepage loads with movies.

You search for **Interstellar**.

Results appear instantly.

Where did those movies come from?

Your browser doesn't store Netflix's entire movie catalog.

Instead, it **asks another computer** for the information.

That computer is called a **server**.

This interaction is known as **Client–Server Architecture**.

---

## 💡 Why This Matters

Almost every modern application follows this architecture.

Examples include:

- Instagram
- YouTube
- WhatsApp
- Amazon
- Spotify
- Gmail

Understanding this architecture helps you understand how web applications communicate.

---

# What Is Client–Server Architecture?

Client–Server Architecture is a model where:

- A **client** requests information or performs an action.
- A **server** processes the request and returns a response.

It's simply a conversation between two computers.

---

# Meet the Two Main Players

## 🖥️ Client

The client is the application used by the user.

Examples:

- Web browser
- Mobile app
- Desktop application

Responsibilities:

- Display the user interface
- Collect user input
- Send requests
- Show responses

---

## 🏢 Server

The server is responsible for processing requests.

Responsibilities:

- Validate requests
- Execute business logic
- Read or update data
- Return responses
- Protect sensitive information

The server is where the backend runs.

---

# A Simple Request Flow

```text
Client
   │
   │ Request
   ▼
Server
   │
Process
   │
   ▼
Database
   ▲
Data
   │
Server
   │
Response
   ▼
Client
```

Every web application repeats this cycle thousands or even millions of times each day.

---

# A Real-World Analogy

Imagine a restaurant.

| Restaurant | Web Application |
|------------|-----------------|
| Customer | Client |
| Kitchen | Server |
| Ingredients | Database |

The customer places an order.

The kitchen prepares the meal.

The customer receives the food.

The customer never enters the kitchen.

Likewise, the client never talks directly to the database.

The server acts as the middle layer.

---

# Step-by-Step Example

Imagine logging into Spotify.

### Step 1

You enter:

```
Email
Password
```

---

### Step 2

The client sends a request.

```text
Login Request
      │
      ▼
Server
```

---

### Step 3

The server:

- Checks the email
- Verifies the password
- Looks up your account

---

### Step 4

If everything is correct:

```text
Server
   │
Login Successful
   ▼
Client
```

The app now lets you access your playlists.

---

# Why Not Connect Directly to the Database?

Imagine if users could directly access your database.

They could:

- Delete products
- Read everyone's passwords
- Change prices
- Access private information

That would be a disaster.

Instead:

```text
Client
   │
   ▼
Server ✅
   │
   ▼
Database
```

The server decides what users are allowed to do.

---

# Real-World Example

Imagine ordering food.

You press **Place Order**.

The client sends your order to the server.

The server:

- Validates the order
- Calculates the total
- Applies discounts
- Processes payment
- Saves the order
- Sends a confirmation

The client simply displays the result.

---

# Production Perspective

When you refresh your Instagram feed:

1. Your phone sends a request.
2. Instagram's servers receive it.
3. The backend gathers posts.
4. It may read from a cache.
5. It fetches new data from databases.
6. It ranks the posts.
7. It sends the final feed back.

All this usually happens in a fraction of a second.

The client only sees the final result.

---

# Advantages

- Clear separation of responsibilities
- Better security
- Easier maintenance
- Supports millions of users
- Easier to scale

---

# Common Mistakes

### ❌ Thinking the client stores everything

The client usually stores only temporary data.

The server remains the source of truth.

---

### ❌ Connecting directly to the database

Always communicate through the backend.

---

### ❌ Putting business logic in the frontend

Business rules belong on the server where they are secure and consistent.

---

# Key Takeaways

- A client requests.
- A server responds.
- The server contains the backend.
- The server communicates with the database.
- The client should never access the database directly.
- Most modern applications use the Client–Server model.

---

## 🚀 What's Next?

You now understand **how browsers and servers communicate**.

But another question remains...

**How does your request travel across the internet to reach the correct server?**

➡️ **Next Chapter:** How the Internet Works