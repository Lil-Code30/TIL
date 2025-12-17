---
title: 02 Strings in Python
comments:
---

## 1️⃣ Concatenation

Joining strings together using `+`.

```python
first = "Hello"
second = "World"
message = first + " " + second
print(message)  # Hello World
```

⚠️ Only strings can be concatenated:

```python
"Age: " + 20   # ❌ TypeError
"Age: " + str(20)  # ✅
```

---

## 2️⃣ String Multiplication

Repeat a string using `*`.

```python
print("ha" * 3)  # hahaha
```

Useful for:

- Separators
- Debug output
- Simple patterns

---

## 3️⃣ String Indexing

Access individual characters using indexes (0-based).

```python
word = "Python"
word[0]  # 'P'
word[3]  # 'h'
```

⚠️ Strings are **immutable**:

```python
word[0] = 'J'  # ❌ TypeError
```

---

## 4️⃣ String Negative Indexing

Access characters from the end.

```python
word = "Python"
word[-1]  # 'n'
word[-2]  # 'o'
```

---

## 5️⃣ String Slicing

Extract a part of a string.

```python
text = "Python"
text[0:3]   # 'Pyt'
text[2:5]   # 'tho'
text[:4]    # 'Pyth'
text[2:]    # 'thon'
text[:]     # 'Python'
```

With step:

```python
text[::2]   # 'Pto'
text[::-1]  # 'nohtyP'
```

---

## 6️⃣ `in` Operator

Check if a substring exists.

```python
"Py" in "Python"      # True
"java" in "Python"    # False
```

Often used in conditions:

```python
if "@" in email:
    print("Valid email")
```

---

## 7️⃣ String Length

Use `len()` to count characters.

```python
len("Python")  # 6
```

Includes spaces:

```python
len("Hello World")  # 11
```

---

## 8️⃣ Character Escaping

Special characters use `\`.

```python
"He said \"Hello\""
"Line1
Line2"
"Tab	Space"
```

Raw strings (no escaping):

```python
r"C:\Users\Loko"
```

---

## 9️⃣ Basic String Methods

Common built-in methods:

```python
text = "  Python Rocks  "

text.lower()      # '  python rocks  '
text.upper()      # '  PYTHON ROCKS  '
text.strip()      # 'Python Rocks'
text.replace("Rocks", "Rules")
text.startswith("Py")
text.endswith("ks")
text.find("Rock")  # index or -1
```

Strings are immutable → methods return **new strings**.

---

## 🔟 String Formatting

### Old style

```python
"Hello %s" % name
```

### `format()`

```python
"Hello {}".format(name)
"{} + {} = {}".format(2, 3, 5)
```

---

## 1️⃣1️⃣ F-Strings (Recommended ⭐)

Clean and fast formatting.

```python
name = "Loko"
age = 25

f"My name is {name} and I am {age}"
```

With expressions:

```python
f"Next year: {age + 1}"
```

---

## 🧠 Key Takeaways

- Strings are **immutable**
- Indexing starts at 0
- Negative indexes count from the end
- Slicing is powerful and safe
- F-strings are the modern standard
