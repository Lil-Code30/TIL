---
title: Built-in variable called __name__.
comments:
---

## What does this mean?

```python
if __name__ == "__main__":
```

It means:

> **“Only run this code if this file is being executed directly, not if it’s being imported.”**

---

## Key idea: `__name__`

Every Python file has a built-in variable called `__name__`.

### Case 1: File is run directly

```bash
python app.py
```

Inside `app.py`:

```python
print(__name__)
```

Output:

```text
__main__
```

So this condition is **True**:

```python
if __name__ == "__main__":
```

➡️ Code inside the block **runs**

---

### Case 2: File is imported

```python
import app
```

Inside `app.py`:

```python
print(__name__)
```

Output:

```text
app
```

Now the condition is **False**:

```python
if __name__ == "__main__":  # False
```

➡️ Code inside the block **does NOT run**

---

## Why is this useful?

### 1️⃣ Prevent code from running on import

Imagine this file:

```python
def add(a, b):
    return a + b

print(add(2, 3))
```

If you import it:

```python
import math_utils
```

👉 It would immediately print `5` (bad practice ❌)

---

### 2️⃣ Correct way (with `__main__`)

```python
def add(a, b):
    return a + b

if __name__ == "__main__":
    print(add(2, 3))
```

Now:

- `python math_utils.py` → prints `5`
- `import math_utils` → prints **nothing**

✅ Clean  
✅ Reusable  
✅ Professional Python code

---

## Real-world use cases

You’ll see this a lot in:

- **Scripts**
- **CLI tools**
- **Backend apps**
- **Tests**
- **Entry points**

Example:

```python
def main():
    print("App started")

if __name__ == "__main__":
    main()
```

This is the **standard Python entry point pattern**.

---

## Simple mental model

Think of it like:

> “Run this only when I double-click the file, not when another file uses it.”

---
