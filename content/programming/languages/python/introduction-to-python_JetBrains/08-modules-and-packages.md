---
title: 08 Modules and Packages
comments:
---

Modules and packages help you **organize code**, **reuse functionality**, and **build scalable projects**.

---

## 1️⃣ Import Module

A **module** is a Python file (`.py`) containing code.

```python
import math

math.sqrt(16)  # 4.0
```

Rules:

- Module name = file name
- Use dot (`.`) to access members

---

## 2️⃣ Import Module (Part 2)

### Import with alias

```python
import math as m

m.pi
```

### Import multiple modules

```python
import math, random
```

Best practice:

- Use aliases only when common (`np`, `pd`)

---

## 3️⃣ Built-in Modules

Python ships with many useful modules.

Common examples:

```python
import math
import random
import datetime
import os
import sys
```

Examples:

```python
random.randint(1, 10)
math.floor(3.7)
os.getcwd()
```

---

## 4️⃣ `from ... import ...`

Import specific objects from a module.

```python
from math import sqrt, pi

sqrt(25)
```

Import everything (⚠️ not recommended):

```python
from math import *
```

Why avoid `*`?

- Pollutes namespace
- Makes code harder to read

---

## 5️⃣ Packages

A **package** is a folder containing modules.

Example structure:

```bash
my_package/
│── __init__.py
│── utils.py
│── helpers.py
```

Import from a package:

```python
from my_package import utils
from my_package.helpers import tool
```

`__init__.py` marks the directory as a package.

---

## 6️⃣ Executing Modules as Scripts

Check if a file is run directly or imported:

```python
if __name__ == "__main__":
    main()
```

Why this matters:

- Prevents code from running on import
- Enables reusable modules

Example:

```python
# file: app.py

def main():
    print("App running")

if __name__ == "__main__":
    main()
```

---

## 🧠 Key Takeaways

- Modules = single `.py` files
- Packages = folders of modules
- Built-in modules save time
- Avoid `from module import *`
- `__name__ == "__main__"` controls execution
