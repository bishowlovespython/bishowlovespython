# Module

A module in Python is a ==file== containing Python code, which can include definitions of `functions`, `classes`, `variables`, and runnable statements. The file name of the module is the module name with a `.py` extension appended.

You can create your own module by saving Python code in a `.py` file. For example, a file named `mymodule.py` might contain:

```py title="mymodule.py"
def greeting(name):
    print("Hello, " + name)
```

You can then use this module in another Python script by importing it with the `import` statement:

```py title="python"
import mymodule
mymodule.greeting("Jonathan")
```

When using functions or variables from a module, you refer to them with the syntax `module_name.function_name` or `module_name.variable_name`.

Python also includes many ==built-in modules==, such as `math` or `platform`, which you can import and use directly.

???+ tip "In summary:"

    - A module is a `.py` file containing Python code (functions, classes, variables).
    - Modules help organize code and promote reuse.
    - You import modules using the `import` keyword.
    - You access module contents using dot notation (`module_name.item`).

This modular approach is fundamental in Python programming for building scalable and maintainable codebases.

---

## What is a Module in Python?

In Python, a **module** is simply a ==file containing Python code==. It can define functions, classes, and variables, and it can also include runnable code. Modules allow you to **organize code into separate files** and **reuse code** across multiple programs.

Example:

A file named `math_utils.py`:

```py
# math_utils.py
def add(a, b):
    return a + b
```

You can use it in another script by importing it:

```py
import math_utils
print(math_utils.add(2, 3))  # Output: 5
```

---

## How to Know if Something is a Module

There are several ways to determine if something is a module:

### 1. Check the Type

Use the built-in `type()` function:

```py
import math
print(type(math))  # <class 'module'>
```

### 2. Use `inspect` Module

Python's `inspect` module can be used to check more precisely:

```py
import inspect
import math

print(inspect.ismodule(math))  # True
```

### 3. File Extension

A module is typically a `.py` file. When you import something and it points to a `.py` file or a compiled `.pyc` file (or a built-in module), it’s a module.

You can also find where a module comes from:

```py
import math
print(math.__file__)  # May show path if it's not a built-in module
```

Built-in modules like `sys` or `math` might not have a `__file__` because they are compiled into the Python interpreter.

## Summary

- A module is a `.py` file or built-in component containing Python definitions and code.
- Use `type(obj)`, `inspect.ismodule(obj)`, or check for `__file__` to identify if something is a module.
- Modules help **organize** and **reuse** code.

---

In Python, **modules** and **packages** are both tools for organizing code, but they’re slightly different:

## Module vs. Package — What's the Difference?

| Feature            | Module                             | Package                                                     |
| ------------------ | ---------------------------------- | ----------------------------------------------------------- |
| **Definition**     | A _single `.py` file_              | A _folder_ containing `__init__.py` and modules/subpackages |
| **Example**        | `math.py`, `os.py`                 | `numpy`, `pandas`, `myapp/`                                 |
| **Purpose**        | Organizes related code in one file | Organizes multiple modules/files in a directory             |
| **Import Example** | `import math`                      | `import numpy.linalg`                                       |

---

## 🔎 How to Tell If It's a Module or Package?

You can identify them in several ways:

**✅ 1. Use `type()` or `inspect`**

These won't directly tell you "module or package," but help confirm if something is a module:

```py
import os
import inspect

print(type(os))                  # <class 'module'>
print(inspect.ismodule(os))      # True
```

To go further...

**✅ 2. Check for `__path__` Attribute**

Only packages have the `__path__` attribute.

```py
import os
print(hasattr(os, '__path__'))  # False → it's a module

import numpy
print(hasattr(numpy, '__path__'))  # True → it's a package
```

**✅ 3. Check `__file__` Path**

You can inspect the `__file__` path to see if it's a single `.py` file (module) or a directory (package):

```py
print(os.__file__)      # ends in os.py → module
print(numpy.__file__)   # path within numpy/ → package
```

**✅ 4. Explore the Filesystem**

- If it's a **single `.py` file** → it's a module.
- If it's a **directory with an** `__init__.py` **file** (even if empty) → it's a package.

**📌 Summary**

| Check                      | Module             | Package                   |
| -------------------------- | ------------------ | ------------------------- |
| `type(obj)`                | `<class 'module'>` | `<class 'module'>`        |
| `hasattr(obj, '__path__')` | `False`            | `True`                    |
| `__file__`                 | Ends in `.py`      | Path inside a folder      |
| Filesystem                 | Single `.py` file  | Folder with `__init__.py` |
