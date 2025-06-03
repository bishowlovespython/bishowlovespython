# Package

- A package is a folder containing one or more modules and a special file named `__init__.py`.
- The `__init__.py` file can be empty or contain initialization code for the package.
- Packages can also contain sub-packages (folders inside folders).

---

## How to create a package:

Suppose you want a package named `mytools` with ==two modules==, `string_ops.py` and `number_ops.py`.

**Folder structure**:

```
mytools/
    __init__.py
    string_ops.py
    number_ops.py
```

**Example content**:

```py
# string_ops.py
def to_upper(text):
    return text.upper()

# number_ops.py
def multiply(a, b):
    return a * b
```

---

## How to use the package:

```py
from mytools import string_ops, number_ops

print(string_ops.to_upper("hello"))  # Output: HELLO
print(number_ops.multiply(4, 5))     # Output: 20
```

Or import individual functions:

```py
from mytools.string_ops import to_upper

print(to_upper("world"))  # Output: WORLD
```

---

## What does `__init__.py` do?

- It tells Python that the directory is a package.
- It can be empty.
- It can also be used to specify what is available when you import the package, by defining the `__all__ `list or importing submodules inside it.

Example:

```py
# __init__.py
from .string_ops import to_upper
from .number_ops import multiply
```

Now, you can directly import functions from the package:

```py
from mytools import to_upper, multiply

print(to_upper("hey"))
print(multiply(3, 7))
```

---

## Summary

- **Module** = single `.py` file.
- **Package** = folder with `__init__.py` + modules/sub-packages.
- Use packages to organize related modules for cleaner, modular code.
