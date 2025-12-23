---
title: args and kwargs
comments:
---

---

## 1️⃣ `*args` (positional arguments)

`*args` lets a function accept **any number of positional arguments**.

```python
def add(*args):
    print(args)

add(1, 2, 3)
```

Output:

```text
(1, 2, 3)
```

🔹 `args` is a **tuple**  
🔹 Name `args` is a convention (you could use any name)

---

### Example: sum numbers

```python
def total(*args):
    return sum(args)

total(1, 2, 3, 4)
```

---

## 2️⃣ `**kwargs` (keyword arguments)

`**kwargs` lets a function accept **any number of keyword arguments**.

```python
def show(**kwargs):
    print(kwargs)

show(name="Loko", age=20)
```

Output:

```text
{'name': 'Loko', 'age': 20}
```

🔹 `kwargs` is a **dictionary**  
🔹 Keys are strings (parameter names)

---

## 3️⃣ Using `*args` and `\*\*kwargs together

```python
def demo(*args, **kwargs):
    print("args:", args)
    print("kwargs:", kwargs)

demo(1, 2, 3, name="Loko", level="junior")
```

Output:

```text
args: (1, 2, 3)
kwargs: {'name': 'Loko', 'level': 'junior'}
```

### ⚠️ Order rule (very important)

```python
def func(a, b, *args, **kwargs):
    ...
```

Correct order:

1. Regular parameters
2. `*args`
3. `**kwargs`

---

## 4️⃣ Why this is so useful (real-world use)

### ✅ Flexible APIs

```python
def create_user(username, **options):
    is_admin = options.get("is_admin", False)
    is_active = options.get("is_active", True)
```

---

### ✅ Decorators (very common)

```python
def logger(func):
    def wrapper(*args, **kwargs):
        print("Calling function")
        return func(*args, **kwargs)
    return wrapper
```

Without `*args` & `**kwargs`, decorators would break easily.

---

### ✅ Framework example (FastAPI style)

```python
@app.get("/users")
def get_users(limit: int = 10, offset: int = 0):
    ...
```

Internally, FastAPI uses `**kwargs` to inject values.

---

## 5️⃣ Unpacking with `*` and `**`

### Unpacking a list

```python
nums = [1, 2, 3]
add(*nums)
```

Equivalent to:

```python
add(1, 2, 3)
```

---

### Unpacking a dictionary

```python
data = {"name": "Loko", "age": 20}
show(**data)
```

Equivalent to:

```python
show(name="Loko", age=20)
```

---

## 6️⃣ Common mistakes

❌ Treating `args` like a list:

```python
args.append(4)  # ❌ tuple has no append
```

❌ Assuming kwargs order matters (Python 3.7+ preserves order, but don’t rely on it for logic)

---

## 7️⃣ Best practices (important 🔥)

✔ Use `*args` when:

- Number of positional arguments is unknown
- You want flexibility

✔ Use `**kwargs` when:

- Many optional parameters
- Config or settings objects
- Public APIs

🚫 Avoid overusing them — explicit parameters are better when possible.

---

## Mental model (easy to remember)

```text
*args   → extra positional values → tuple
**kwargs → extra named values → dict
```

---

## Summary

```python
def func(a, b, *args, **kwargs):
    pass
```

| Element    | Type     | Meaning          |
| ---------- | -------- | ---------------- |
| `a, b`     | required | fixed parameters |
| `*args`    | tuple    | extra positional |
| `**kwargs` | dict     | extra keyword    |

---
