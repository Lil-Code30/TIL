---
title: 07 Classes and Objects
comments:
---

Object-Oriented Programming (OOP) helps structure programs using **objects** that bundle data and behavior together.

---

## 1️⃣ Class Definition

A **class** is a blueprint for creating objects.

```python
class Person:
    pass
```

Create an object (instance):

```python
p = Person()
```

---

## 2️⃣ Variable Access

Variables defined inside a class belong to objects.

```python
class Person:
    def __init__(self, name):
        self.name = name

p = Person("Loko")
print(p.name)
```

Use dot (`.`) notation to access variables.

---

## 3️⃣ Update Variables

Object variables can be updated after creation.

```python
p.name = "Alex"
```

Inside the class:

```python
def rename(self, new_name):
    self.name = new_name
```

---

## 4️⃣ The `self` Parameter

`self` refers to the **current object**.

```python
class Counter:
    def increment(self):
        self.value += 1
```

Rules:

- `self` must be the first parameter
- It is passed automatically

---

## 5️⃣ Call a Method from Another Method

Methods can call each other using `self`.

```python
class User:
    def login(self):
        self.log("User logged in")

    def log(self, message):
        print(message)
```

---

## 6️⃣ Special `__init__` Method

The constructor runs when an object is created.

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age
```

---

## 7️⃣ `__str__` vs `__repr__`

Control how objects are displayed.

```python
class User:
    def __init__(self, name):
        self.name = name

    def __str__(self):
        return f"User: {self.name}"

    def __repr__(self):
        return f"User(name={self.name!r})"
```

- `__str__` → readable (users)
- `__repr__` → unambiguous (developers)

---

## 8️⃣ Class Variables vs Instance Variables

### Instance variables

Belong to each object.

```python
self.name = name
```

### Class variables

Shared across all instances.

```python
class Car:
    wheels = 4
```

```python
Car.wheels
```

---

## 9️⃣ Class vs Instance Variables (Example)

```python
class Player:
    count = 0

    def __init__(self, name):
        self.name = name
        Player.count += 1
```

```python
p1 = Player("A")
p2 = Player("B")

Player.count  # 2
```

---

## 🔮 Magic Methods (Dunder Methods)

Magic methods start and end with double underscores `__`.

### Common magic methods

```python
__init__    # constructor
__str__     # user-friendly string
__repr__    # developer string
__len__     # len(obj)
__eq__      # obj1 == obj2
__lt__      # obj1 < obj2
__add__     # obj1 + obj2
```

Example:

```python
class Box:
    def __init__(self, size):
        self.size = size

    def __len__(self):
        return self.size
```

```python
b = Box(10)
len(b)  # 10
```

---

## 🧠 Key Takeaways

- Classes are blueprints, objects are instances
- `self` links methods and data
- `__init__` initializes objects
- Class variables are shared
- Magic methods integrate objects with Python syntax
