---
title: 09 Files Input and Output in Python
comments:
---

File I/O allows programs to **read from** and **write to files**, which is essential for data persistence, logs, and real applications.

---

## 1️⃣ Open File

Use the built-in `open()` function.

```python
file = open("data.txt", "r")
```

Common modes:

| Mode  | Meaning           |
| ----- | ----------------- |
| `"r"` | Read (default)    |
| `"w"` | Write (overwrite) |
| `"a"` | Append            |
| `"x"` | Create new file   |
| `"b"` | Binary mode       |

⚠️ Always close the file:

```python
file.close()
```

---

## 2️⃣ Read File

Read the entire file as a single string.

```python
file = open("data.txt")
content = file.read()
file.close()
```

Better approach (auto-close):

```python
with open("data.txt") as file:
    content = file.read()
```

---

## 3️⃣ Read All Lines

Read file line by line.

```python
with open("data.txt") as file:
    lines = file.readlines()
```

Each line ends with `\n`.

Looping through lines:

```python
with open("data.txt") as file:
    for line in file:
        print(line.strip())
```

---

## 4️⃣ Write to File

### Write mode (`w`)

Creates or overwrites a file.

```python
with open("output.txt", "w") as file:
    file.write("Hello world")
```

### Append mode (`a`)

Adds content to the end of a file.

```python
with open("output.txt", "a") as file:
    file.write("\nNew line")
```

---

## 🧠 Key Takeaways

- Use `with open(...)` to manage files safely
- `read()` → full content
- `readlines()` → list of lines
- `w` overwrites, `a` appends
- Always handle files carefully
