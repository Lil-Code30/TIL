---
title: 06 Functions in Python
comments:
---

Functions let you **organize code**, **reuse logic**, and **make programs readable and scalable**.

---

## 1️⃣ Function Definition

A function is defined using the `def` keyword.

```python
def greet():
    print("Hello!")
```

Calling the function:

```python
greet()
```

Rules:

- Function name should be descriptive
    
- Code inside must be indented
    

---

## 2️⃣ Parameters and Call Arguments

### Parameters

Variables listed in the function definition.

```python
def greet(name):
    print("Hello", name)
```

### Arguments

Values passed when calling the function.

```python
greet("Loko")
```

---

## 3️⃣ Return Value

Functions can return values using `return`.

```python
def add(a, b):
    return a + b

result = add(2, 3)
```

Key points:

- `return` ends the function
    
- A function without `return` returns `None`
    

---

## 4️⃣ Docstrings

Docstrings describe what a function does.

```python
def add(a, b):
    """Return the sum of a and b."""
    return a + b
```

Access docstring:

```python
help(add)
```

Best practice:

- Explain purpose, parameters, and return value
    

---

## 5️⃣ Default Parameters

Provide default values for parameters.

```python
def greet(name="Guest"):
    print("Hello", name)
```

```python
greet()          # Hello Guest
greet("Loko")   # Hello Loko
```

⚠️ Default parameters are evaluated once.

---

## 6️⃣ Keyword Arguments

Pass arguments using parameter names.

```python
def user_info(name, age):
    print(name, age)

user_info(age=25, name="Loko")
```

Benefits:

- Improves readability
    
- Order doesn’t matter
    

---

## 7️⃣ Argument Order

Correct order when calling functions:

1. Positional arguments
    
2. `*args`
    
3. Keyword arguments
    
4. `**kwargs`
    

❌ Invalid:

```python
func(x=1, 2)
```

---

## 8️⃣ `*args` and `**kwargs`

### `*args`

Accepts multiple positional arguments (tuple).

```python
def total(*args):
    return sum(args)
```

### `**kwargs`

Accepts multiple keyword arguments (dictionary).

```python
def user(**kwargs):
    print(kwargs)
```

```python
user(name="Loko", role="Dev")
```

---

## 9️⃣ Recursion

A function calling itself.

```python
def factorial(n):
    if n == 1:
        return 1
    return n * factorial(n - 1)
```

Rules:

- Must have a base case
    
- Must move toward the base case
    

⚠️ Without a base case → infinite recursion.

---

## 🧠 Key Takeaways

- Functions make code reusable
    
- Parameters ≠ arguments
    
- `return` sends data back
    
- Docstrings document behavior
    
- `*args` and `**kwargs` enable flexibility
    
- Recursion requires discipline
    
