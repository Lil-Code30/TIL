---
title: 03 Data Structures in Python
comments:
---

## 1️⃣ Lists — Introduction

A **list** is an ordered, mutable collection.

```python
numbers = [1, 2, 3]
names = ["Loko", "Alex", "Sam"]
mixed = [1, "hi", True]
```

Key properties:

- Ordered
- Mutable (can be changed)
- Allows duplicates

---

## 2️⃣ Lists Operations

### Access elements

```python
numbers[0]    # 1
numbers[-1]   # 3
```

### Modify elements

```python
numbers[1] = 20
```

### Common operations

```python
len(numbers)
1 in numbers
numbers + [4, 5]
numbers * 2
```

---

## 3️⃣ List Items (Add / Remove)

### Add items

```python
lst = [1, 2]
lst.append(3)
lst.insert(1, 10)
lst.extend([4, 5])
```

### Remove items

```python
lst.remove(10)
lst.pop()
lst.pop(0)
del lst[1]
```

---

## 4️⃣ Nested Lists

Lists inside lists.

```python
matrix = [
    [1, 2, 3],
    [4, 5, 6]
]

matrix[0][1]  # 2
```

Useful for:

- Tables
- Grids
- Game boards

---

## 5️⃣ Tuples

An **immutable** ordered collection.

```python
coords = (10, 20)
```

Why use tuples?

- Faster than lists
- Protect data from changes
- Used as dictionary keys

```python
coords[0]  # 10
```

---

## 6️⃣ Join Method

Used to join strings from a list.

```python
words = ["Python", "is", "fun"]
" ".join(words)  # 'Python is fun'
```

⚠️ Works only with strings.

---

## 7️⃣ Dictionaries

A **key–value** data structure.

```python
user = {
    "name": "Loko",
    "age": 25,
    "is_dev": True
}
```

Access values:

```python
user["name"]
user.get("age")
```

---

## 8️⃣ Add Items from Lists

### Add list items to another list

```python
a = [1, 2]
b = [3, 4]
a.extend(b)
```

### Create dictionary from lists

```python
keys = ["name", "age"]
values = ["Loko", 25]

dict(zip(keys, values))
```

---

## 9️⃣ Dictionary `keys()` and `values()`

```python
user.keys()    # dict_keys(['name', 'age', 'is_dev'])
user.values()  # dict_values(['Loko', 25, True])
user.items()   # key-value pairs
```

Loop example:

```python
for key, value in user.items():
    print(key, value)
```

---

## 🔟 Dictionary Keys

Rules for keys:

- Must be **immutable**
- Commonly strings or tuples

```python
valid = {(1, 2): "point"}
invalid = {[1, 2]: "point"}  # ❌
```

---

## 1️⃣1️⃣ `in` Keyword

Check existence.

### With lists

```python
3 in [1, 2, 3]  # True
```

### With dictionaries

```python
"name" in user      # checks keys
"Loko" in user      # False
"Loko" in user.values()  # True
```

---

## 🧠 Key Takeaways

- Lists are mutable, tuples are immutable
- Dictionaries store key–value pairs
- `in` behaves differently per structure
- Nested structures are very powerful
