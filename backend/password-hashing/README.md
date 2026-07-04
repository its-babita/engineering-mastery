# Password Hashing

> Part of the **Engineering Mastery** handbook.

## ⏱️ Quick Facts

| | |
|---|---|
| **Read Time** | 10–12 minutes |
| **Difficulty** | 🟢 Beginner |
| **Prerequisites** | Authentication, Authorization |

---

## 📍 Where We Are in the Authentication Flow

```text
User Registers
      │
      ▼
Enter Password
      │
      ▼
Password Hashing ← You are here
      │
      ▼
Store Hash in Database
      │
      ▼
User Logs In
      │
      ▼
Verify Password Against Hash
```

---

## Imagine This...

Suppose you own a locker room.

Would you keep a copy of everyone's locker key?

Probably not.

Instead, you would keep a lock that only works with the correct key.

Password hashing works in a similar way.

The server doesn't store the password—it stores a value created from the password.

---

# 💡 Why This Matters

Imagine a database is compromised.

If passwords are stored as plain text:

```text
alice123
password
qwerty
```

Anyone with access to the database can immediately read every password.

Now imagine the database stores:

```text
$2b$12$...
$2b$12$...
$2b$12$...
```

These are password hashes.

The original passwords are not directly visible.

---

# What Is Password Hashing?

Password hashing is the process of converting a password into a fixed-length value using a **one-way hashing algorithm**.

```text
"MySecretPassword"

        │
        ▼

Hash Function

        │
        ▼

$2b$12$A8k...
```

The important property is:

You can generate the hash from the password,

but you cannot realistically recover the original password from the hash.

---

# Hashing Is Not Encryption

These terms are often confused.

| Hashing | Encryption |
|----------|------------|
| One-way | Two-way |
| Cannot be reversed | Can be decrypted with a key |
| Used for passwords | Used for protecting data |

Passwords should be **hashed**, not encrypted.

---

# Registration Flow

When a user signs up:

```text
Password

↓

Hash Password

↓

Store Hash
```

Example:

```text
Password:

MySecret123
```

Stored in the database:

```text
$2b$12$XvL8...
```

The original password is never stored.

---

# Login Flow

When the user logs in:

```text
Enter Password

↓

Hash Entered Password

↓

Compare With Stored Hash

↓

Match?

↓

Login Success
```

The server doesn't compare plain-text passwords.

It compares hashes.

---

# Common Hashing Algorithms

| Algorithm | Recommended? |
|-----------|--------------|
| MD5 | ❌ No |
| SHA-1 | ❌ No |
| bcrypt | ✅ Yes |
| scrypt | ✅ Yes |
| Argon2 | ✅ Recommended |

Modern applications commonly use **bcrypt** or **Argon2** because they are designed specifically for password hashing.

---

# Example (Node.js)

Using `bcrypt`:

```javascript
import bcrypt from "bcrypt";

const password = "MySecret123";

const hash = await bcrypt.hash(password, 12);

console.log(hash);
```

Verifying a password:

```javascript
const isValid = await bcrypt.compare(
  "MySecret123",
  hash
);

console.log(isValid);
```

Notice that you never compare plain-text passwords directly.

---

# Production Perspective

Suppose Alice registers.

Database:

| Email | Password |
|--------|----------|
| alice@example.com | `$2b$12$...` |

Later, Alice logs in.

The backend:

1. Retrieves the stored hash.
2. Uses the hashing algorithm to verify the entered password.
3. Grants access if they match.

At no point does the backend need the original password.

---

# Best Practices

- Never store plain-text passwords.
- Use `bcrypt` or `Argon2`.
- Use a strong work factor (cost factor).
- Always use HTTPS during login.
- Never log passwords.

---

# Common Mistakes

### ❌ Storing passwords directly

Always store hashes instead.

---

### ❌ Using MD5 or SHA-1

These algorithms are no longer considered suitable for password storage.

Use password-specific algorithms such as bcrypt or Argon2.

---

### ❌ Comparing passwords manually

Always use the verification function provided by the hashing library.

It safely compares the entered password with the stored hash.

---

# 💡 Did You Know?

If two users choose the same password, modern hashing algorithms still produce different hashes because they use a **salt**.

This makes precomputed attack techniques much less effective.

We'll explore salts in more detail in the advanced security section.

---

# Key Takeaways

- Never store plain-text passwords.
- Password hashing is a one-way process.
- Hashing is different from encryption.
- Use bcrypt or Argon2 for password storage.
- During login, compare the entered password with the stored hash.

---

## 🚀 What's Next?

The user has successfully logged in.

Now...

**How can the server remember the user without asking for a password on every request?**

➡️ **Next Chapter:** JSON Web Tokens (JWT)