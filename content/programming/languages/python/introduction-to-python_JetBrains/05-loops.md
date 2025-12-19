---
title: 05 Loops in Python
comments:
---

## 1️⃣ `for` Loop

Used to iterate over a sequence (list, string, range, etc.).

```python
for i in range(5):
    print(i)
```

Example with a list:

```python
names = ["Loko", "Alex", "Sam"]
for name in names:
    print(name)
```

---

## 2️⃣ Loop Over a String

Strings are iterable (character by character).

```python
word = "Python"
for char in word:
    print(char)
```

Useful for:

- Validation
- Character counting
- Parsing text

---

## 3️⃣ Nested `for` Loop

A loop inside another loop.

```python
for i in range(3):
    for j in range(2):
        print(i, j)
```

Example with nested lists:

```python
matrix = [[1, 2], [3, 4]]
for row in matrix:
    for value in row:
        print(value)
```

---

## 4️⃣ List Comprehension

A concise way to create lists.

```python
squares = [x ** 2 for x in range(5)]
```

With condition:

```python
even = [x for x in range(10) if x % 2 == 0]
```

Equivalent to:

```python
even = []
for x in range(10):
    if x % 2 == 0:
        even.append(x)
```

---

## 5️⃣ Nested List Comprehension

List comprehensions inside others.

```python
matrix = [[i * j for j in range(3)] for i in range(3)]
```

Flatten a matrix:

```python
flat = [num for row in matrix for num in row]
```

Use carefully — readability matters.

---

## 6️⃣ `while` Loop

Runs as long as the condition is True.

```python
count = 0
while count < 5:
    print(count)
    count += 1
```

Use when:

- Number of iterations is unknown
- Waiting for a condition

---

## 7️⃣ `break` Keyword

Stops the loop immediately.

```python
for n in range(10):
    if n == 5:
        break
    print(n)
```

---

## 8️⃣ Fix Infinite Execution

Infinite loops happen when the condition never becomes False.

❌ Example:

```python
while True:
    print("Running forever")
```

Fix with:

- `break`
- Updating condition variables

```python
while True:
    cmd = input()
    if cmd == "exit":
        break
```

---

## 9️⃣ `else` with Loops

Executed **only if loop finishes normally** (no `break`).

```python
for n in range(3):
    print(n)
else:
    print("Loop finished")
```

With `break`:

```python
for n in range(3):
    if n == 1:
        break
else:
    print("Won't run")
```

---

## 🔟 `else` with Loops (Use Case)

Often used for searching.

```python
nums = [1, 3, 5]

for n in nums:
    if n == 2:
        print("Found")
        break
else:
    print("Not found")
```

---

## 1️⃣1️⃣ `continue` Keyword

Skips the current iteration and moves to the next.

```python
for n in range(5):
    if n == 2:
        continue
    print(n)
```

Output:

```cmd
0
1
3
4
```

---

## 🧠 Key Takeaways

- `for` loops iterate over sequences
- `while` loops depend on conditions
- `break` exits, `continue` skips
- `else` runs only without `break`
- List comprehensions are powerful but should stay readable
