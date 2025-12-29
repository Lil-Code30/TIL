---
title: Refresh token rotation explained
---

## 🔄 What “refresh token rotation” means (1 line)

> **Every time a refresh token is used, it is destroyed and replaced with a new one.**

Only **one refresh token is ever valid at a time per session**.

---

## 🧠 Before rotation (mental setup)

- Access Token → short-lived (minutes)
- Refresh Token → long-lived (days)
- Refresh Token represents **the session**

---

## 🟢 Initial login (starting point)

```pgsql
User logs in
│
├── Access Token A1 (expires soon)
└── Refresh Token R1 (stored securely)
```

State:

- R1 = VALID
- A1 = VALID

---

## 🔁 Access token expires → refresh happens

```pgsql
A1 expires
│
└── Client sends R1 to refresh endpoint
```

The server now **expects exactly R1**.

---

## 🔄 Rotation happens HERE

### Server logic (conceptual)

```pgsql
Receive R1
│
├── Is R1 valid? ✅
├── Is R1 already used? ❌
│
├── Invalidate R1 ❌
├── Generate new Refresh Token → R2 ✅
├── Generate new Access Token → A2 ✅
```

---

## 🟢 After rotation (new state)

```pgsql
Old:
- R1 ❌ invalid
- A1 ❌ expired

New:
- R2 ✅ valid
- A2 ✅ valid
```

Only **R2** can now be used.

---

## 🔁 Next refresh cycle (same pattern)

```pgsql
A2 expires
│
└── Client sends R2
     │
     ├── R2 invalidated ❌
     ├── R3 created ✅
     └── A3 created ✅
```

This continues forever **until logout or expiration**.

---

## 🚨 Attack scenario (WHY rotation matters)

### Attacker steals an old refresh token (R1)

```pgsql
Attacker tries to use R1
│
└── Server checks:
     ├── R1 already invalidated ❌
     └── REJECT request 🚫
```

✅ Attack blocked
✅ Session remains safe
✅ User stays logged in

---

## 🧨 Without rotation (dangerous comparison)

```pgsql
Refresh Token R1
│
├── Used by real user ✅
├── Used by attacker ❌ (still works!)
```

Attacker can:

- Refresh forever
- Hijack session
- Stay invisible

❌ This is why rotation exists.

---

## 🧩 Visual summary (timeline)

```pgsql
Time →
Login     Refresh     Refresh     Refresh
│         │           │           │
A1,R1 → A2,R2 → A3,R3 → A4,R4
     ❌R1      ❌R2      ❌R3
```

Only the **latest refresh token survives**.

---

## 🧠 Key rules (memorize these)

✔ Refresh token is **single-use**
✔ Using it destroys it
✔ New refresh token replaces it
✔ Reuse = attack
✔ Backend controls everything

---

## 🔐 When to use refresh token rotation

You SHOULD use rotation if:

- You care about security
- You store refresh tokens in cookies
- You support long sessions
- You want to detect token theft

This is **modern best practice**.

---

## One-sentence takeaway

> **Refresh token rotation turns stolen tokens into dead tokens.**

---
