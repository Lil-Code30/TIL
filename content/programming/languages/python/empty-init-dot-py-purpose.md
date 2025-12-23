---
title: Empty __init__.py Purpose
comments:
---

## Why does `__init__.py` exist even if it’s empty?

An empty `__init__.py` file tells Python:

> **“This folder is a Python package.”**

In this case:

```bash
functions/
└── greeting/
    ├── __init__.py
    └── goodbye.py
```

This means:

- `greeting` is a **package**
- `goodbye.py` is a **module inside that package**

Without `__init__.py`, Python (especially older versions and many tools) may **not treat the folder as a package**.

---

### What does Python use `__init__.py` for?

Even when empty, it enables:

✅ Importing modules

```python
from functions.greeting import goodbye
```

✅ Importing functions/classes cleanly

```python
from functions.greeting.goodbye import say_goodbye
```

✅ Package-level configuration (later)

---

### When does `__init__.py` contain code?

You add code **only if you need it**. Common uses:

#### 1️⃣ Re-export things (clean imports)

```python
# greeting/__init__.py
from .goodbye import say_goodbye
```

Now you can do:

```python
from functions.greeting import say_goodbye
```

#### 2️⃣ Run setup code once when the package is imported

```python
print("Greeting package loaded")
```

#### 3️⃣ Define `__all__`

```python
__all__ = ["say_goodbye"]
```

---

### Is it bad that it’s empty?

❌ No — it’s **best practice**  
✅ Many packages keep it empty until needed  
✅ It improves structure, tooling support, and readability

---

### Quick mental model 🧠

- **Folder without `__init__.py`** → just a folder
- **Folder with `__init__.py`** → Python package
- **Empty `__init__.py`** → “This package exists, nothing special yet”

---
