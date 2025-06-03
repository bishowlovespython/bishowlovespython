# Overview

To master Python, knowing its built-in functions is like having a toolbox where you understand every tool — when and how to use it. Python has 70+ built-in functions, but here are the **most important and frequently used ones** every serious Python programmer should know well.

---

## 🧠 Core Built-ins You Must Master

### 🔍 Inspecting & Debugging

- `type()` – Get the type of a value.
- `id()` – Unique ID of an object (useful for identity checks).
- `dir()` – See what’s inside an object.
- `help()` – Get documentation on an object or function.
- `vars()` – See `__dict__` (attributes) of an object.

### 🔄 Type Conversion & Casting

- `int()`, `float()`, `str()`, `bool()` – Convert between data types.
- `list()`, `set()`, `tuple()`, `dict()` – Create or convert between containers.
- `ord()` / `chr()` – Character-code conversions.
- `bin()`, `hex()`, `oct()` – Convert integers to binary/hex/oct strings.

### 🔁 Loops and Iterables

- `range()` – Create number ranges for loops.
- `enumerate()` – Loop with index and value.
- `zip()` – Combine multiple iterables element-wise.
- `map()` – Apply a function to all items in an iterable.
- `filter()` – Filter items using a condition.
- `reversed()` – Reverse an iterable.
- `sorted()` – Sort anything.
- `len()` – Length of an object.

### 🧮 Math & Numbers

- `sum()` – Sum of a list of numbers.
- `min()` / `max()` – Find smallest/largest.
- `abs()` – Absolute value.
- `round()` – Round a number.
- `pow()` – Power (can also use `**`).

### 📦 Containers & Collections

- `all()` – True if all elements are true.
- `any()` – True if at least one is true.
- `isinstance()` – Check if something is of a certain type.
- `slice()` – Create slice objects (used for indexing).

### 🔧 Functional Programming

- `lambda` – Create anonymous functions.
- `callable()` – Check if an object can be called like a function.
- `eval()` – Evaluate a string as Python code (careful!).
- `exec()` – Execute dynamically created Python code (dangerous!).

### 🗃️ Object Handling

- `getattr()`, `setattr()`, `hasattr()`, `delattr()` – Dynamic attribute access.
- `staticmethod()`, `classmethod()` – Used in classes.
- `property()` – Define managed attributes in classes.

### ⛏️ I/O (Input/Output)

- `print()` – Output to console.
- `input()` – Get user input.

### 🧱 Structure and Flow

- `compile()` – Turn source code into code objects.
- `globals()` / `locals()` – Access global/local symbol tables.
- `__import__()` – Dynamic import of a module.

---

## 🧰 Optional but Useful

- `next()` – Get next item from an iterator.
- `iter()` – Turn something into an iterator.
- `memoryview()` – Access byte-level data efficiently.
- `format()` – String formatting.

---

## ✅ What You Should Do

1.  **Read the docs**: [Python Built-in Functions](https://docs.python.org/3/library/functions.html)
2.  **Practice in real code**: Use them in small projects or exercises.
3.  **Explore via** `dir(__builtins__)`: Try this in Python to see them all.

Would you like a cheat sheet or practice problems to go with these?
