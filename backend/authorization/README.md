# Authorization

> Part of the **Engineering Mastery** handbook.

## ⏱️ Quick Facts

| | |
|---|---|
| **Read Time** | 8–10 minutes |
| **Difficulty** | 🟢 Beginner |
| **Prerequisites** | Authentication |

---

## 📍 Where We Are in the User Journey

```text
User Logs In
      │
      ▼
Authentication ✅
      │
      ▼
Authorization ← You are here
      │
      ▼
Access Granted or Denied
```

---

## Imagine This...

You've entered an office building.

The security guard has already verified your identity.

Now you try to enter the server room.

The system checks:

> "Are you allowed to enter this room?"

That's authorization.

---

# 💡 Why This Matters

Not every user should have the same permissions.

For example:

- Customers shouldn't access the admin dashboard.
- Employees shouldn't view payroll unless authorized.
- Students shouldn't modify grades.

Authentication identifies the user.

Authorization determines what the user can do.

---

# What Is Authorization?

**Authorization** is the process of determining whether an authenticated user has permission to perform a specific action.

It answers the question:

> **"What are you allowed to do?"**

---

# Authentication vs Authorization

| Authentication | Authorization |
|----------------|---------------|
| Confirms identity | Checks permissions |
| Happens first | Happens after authentication |
| "Who are you?" | "What can you do?" |

Both are essential, but they solve different problems.

---

# How Authorization Works

Suppose Alice is already logged in.

She requests:

```http
DELETE /users/25
```

The server checks:

```text
Is Alice authenticated?

        ✅

Does Alice have permission?

        ❓

Yes → Perform action

No → Return 403 Forbidden
```

---

# Common Authorization Models

## Role-Based Access Control (RBAC)

Permissions are assigned based on roles.

Example:

| Role | Permissions |
|------|-------------|
| Admin | Full access |
| Manager | Manage team |
| Customer | View own account |

RBAC is the most common authorization model.

---

## Permission-Based Access

Instead of roles, users receive specific permissions.

Example:

```text
create:user
edit:user
delete:user
view:reports
```

This provides more flexibility than simple roles.

---

# Production Example

Imagine an e-commerce platform.

### Customer

Can:

- View products
- Place orders
- View their own profile

Cannot:

- Delete users
- Manage inventory

---

### Admin

Can:

- Add products
- Remove products
- View all orders
- Manage users

The backend checks permissions before executing each protected action.

---

# Behind the Scenes

```text
User Request
      │
      ▼
Is User Authenticated?
      │
      ▼
Load User Role / Permissions
      │
      ▼
Permission Check
      │
 ┌────┴────┐
 │         │
 ▼         ▼
Allow     Deny
```

---

# Where Are Permissions Stored?

Depending on the application, permissions may come from:

- Database
- JWT Claims
- Session Data
- Identity Provider

Large applications often store roles and permissions in a database for easier management.

---

# Best Practices

- Apply the principle of least privilege.
- Always verify permissions on the server.
- Never rely only on frontend checks.
- Keep roles simple and meaningful.
- Audit sensitive operations.

---

# Common Mistakes

### ❌ Authentication is enough

Knowing who a user is doesn't mean they should have access to everything.

---

### ❌ Checking permissions only in the frontend

Frontend checks improve the user experience.

Backend checks provide security.

Always enforce authorization on the server.

---

### ❌ Giving every user broad permissions

Only grant the access required for a user's responsibilities.

---

# 💡 Did You Know?

Even if a user hides the "Delete" button using browser developer tools, they can still try to call the API directly.

That's why backend authorization checks are essential.

---

# Key Takeaways

- Authorization determines what a user can do.
- It happens after authentication.
- RBAC is one of the most common authorization models.
- Permissions should always be enforced on the server.
- Following the principle of least privilege improves security.

---

## 🚀 What's Next?

The application now knows:

- Who the user is ✅
- What they're allowed to do ✅

But...

**How can we store passwords securely without ever saving the original password?**

➡️ **Next Chapter:** Password Hashing