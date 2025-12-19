---
title: 04 Condition Expressions
comments:
---


## 1️⃣ Boolean Operators

Boolean operators are used to combine or modify conditions.

|Operator|Meaning|Example|
|---|---|---|
|`and`|True if both are True|`a > 0 and b > 0`|
|`or`|True if at least one is True|`a > 0 or b > 0`|
|`not`|Reverses the value|`not is_logged_in`|

Examples:

```python
age = 20
is_student = False

age >= 18 and not is_student   # True
```

---

## 2️⃣ Boolean Operators Order (Precedence)

Python evaluates boolean expressions in a specific order:

1. `not`
    
2. `and`
    
3. `or`
    

Example:

```python
True or False and False
```

Evaluation:

```python
False and False  → False
True or False    → True
```

Use parentheses for clarity:

```python
(True or False) and False
```

---

## 3️⃣ `if` Statement

The `if` statement executes code only if the condition is True.

```python
age = 18

if age >= 18:
    print("You are an adult")
```

Rules:

- Condition must evaluate to `True` or `False`
    
- Code block must be indented
    

---

## 4️⃣ `else` and `elif` Parts

### `else`

Runs when the `if` condition is False.

```python
if age >= 18:
    print("Adult")
else:
    print("Minor")
```

### `elif`

Used to check multiple conditions.

```python
score = 75

if score >= 90:
    print("A")
elif score >= 70:
    print("B")
else:
    print("C")
```

Python checks conditions **top to bottom**.

---

## 5️⃣ Single-line `if-else` (Ternary Expression)

A compact way to write simple conditions.

```python
status = "Adult" if age >= 18 else "Minor"
```

Another example:

```python
max_value = a if a > b else b
```

Use only when it improves readability.

---

## 6️⃣ Indentation

Indentation defines code blocks in Python (usually 4 spaces).

```python
if True:
    print("Correct")
    print("Still inside if")
print("Outside if")
```

⚠️ Incorrect indentation causes errors:

```python
if True:
print("Error")  # ❌ IndentationError
```

Best practice:

- Use **4 spaces**
    
- Never mix tabs and spaces
    

---

## 🧠 Key Takeaways

- Conditions control program flow
    
- Boolean operators follow strict precedence
    
- `elif` avoids nested `if`s
    
- Indentation is part of Python syntax
    
- Ternary expressions are concise but optional
    