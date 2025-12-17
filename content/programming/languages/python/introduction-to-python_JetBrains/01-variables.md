---
title: 01 Variables in Python
comments:
---

## 1️⃣ Variable Definition

A **variable** is a name that refers to a value stored in memory.

```python
x = 10
name = "Loko"
```

- Python uses **dynamic typing** (no need to specify type)
- Variables are created at assignment time
- Naming rules:
  - Must start with a letter or `_`
  - Cannot start with a number
  - Case-sensitive (`age` ≠ `Age`)

✅ Good practice:

```python
user_age = 25
```

❌ Bad practice:

```python
1age = 25
```

---

## 2️⃣ Undefined Variable

Using a variable **before assignment** raises an error.

```python
print(x)  # NameError: name 'x' is not defined
```

Why?

- Python reads code **top to bottom**
- Variable must exist before use

Fix:

```python
x = 5
print(x)
```

---

## 3️⃣ Variable Types (Basic)

Python has built-in data types.

| Type  | Example         |
| ----- | --------------- |
| int   | `10`, `-3`      |
| float | `3.14`, `2.0`   |
| str   | `"hello"`       |
| bool  | `True`, `False` |

Check a variable’s type:

```python
type(10)        # int
type("hi")      # str
type(True)      # bool
```

---

## 4️⃣ Type Conversion (Casting)

Convert one type into another.

```python
x = "5"
y = int(x)   # 5
z = float(x) # 5.0
```

Common conversions:

```python
int("10")
float("3.5")
str(100)
bool(0)      # False
bool(1)      # True
```

⚠️ Invalid conversion:

```python
int("abc")  # ValueError
```

---

## 5️⃣ Arithmetic Operators

Used for mathematical operations.

| Operator | Meaning        | Example         |
| -------- | -------------- | --------------- |
| `+`      | Addition       | `5 + 2`         |
| `-`      | Subtraction    | `5 - 2`         |
| `*`      | Multiplication | `5 * 2`         |
| `/`      | Division       | `5 / 2` → `2.5` |
| `//`     | Floor division | `5 // 2` → `2`  |
| `%`      | Modulo         | `5 % 2` → `1`   |
| `**`     | Power          | `2 ** 3` → `8`  |

---

## 6️⃣ Assignments

Assign values using `=`.

```python
x = 10
y = x
```

### Multiple assignment

```python
a, b = 1, 2
```

### Augmented assignment

```python
x = 5
x += 2   # x = 7
x *= 3   # x = 21
```

---

## 7️⃣ Boolean Operators

Used with boolean values.

| Operator | Meaning           |
| -------- | ----------------- |
| `and`    | Both must be True |
| `or`     | At least one True |
| `not`    | Reverses value    |

Examples:

```python
True and False   # False
True or False    # True
not True         # False
```

Truthiness:

```python
bool(0)        # False
bool("")       # False
bool("text")   # True
bool(10)       # True
```

---

## 8️⃣ Comparison Operators

Used to compare values (returns `True` or `False`).

| Operator | Meaning          | Example  |
| -------- | ---------------- | -------- |
| `==`     | Equal            | `5 == 5` |
| `!=`     | Not equal        | `5 != 3` |
| `>`      | Greater than     | `5 > 3`  |
| `<`      | Less than        | `3 < 5`  |
| `>=`     | Greater or equal | `5 >= 5` |
| `<=`     | Less or equal    | `4 <= 5` |

Example:

```python
age = 18
age >= 18   # True
```

---

## 🧠 Key Takeaways

- Variables are created on assignment
- Python is dynamically typed
- Booleans control logic
- Comparisons return True/False
- Type conversion is explicit
