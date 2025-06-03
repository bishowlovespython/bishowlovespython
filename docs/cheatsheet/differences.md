# Differences

## 🚨 Key Differences Between Python and JavaScript

1.  **Whitespace Matters in Python**

    - JS: Uses `{}` to define blocks.
    - Python: Uses ==indentation== (tabs or spaces).

    ```js title="javascript"
    if (x > 0) {
      console.log("positive");
    }
    ```

    ```py title="python"
    if x > 0:
        print("positive")
    ```

2.  **Variable Declaration**

    - JS: `let`, `const`, `var`
    - Python: Just write the variable name (type is dynamic)

    ```js title="javascript"
    let x = 5;
    ```

    ```py title="python"
    x = 5
    ```

3.  **Function Syntax**

    ```js title="javascript"
    function add(a, b) {
      return a + b;
    }
    ```

    ```py title="python"
    def add(a, b):
        return a + b
    ```

4.  **No `this`, less confusion**

    - Python uses `self` explicitly in class methods.
    - No `this` binding nightmares like in JS.

5.  **No semicolons or parentheses**

    - Cleaner syntax; rarely uses semicolons.
    - Conditions don't need `()`.

6.  **Python is strongly typed**

    - JS lets you do `"5" + 1` → `"51"`
    - Python throws an error → `TypeError`

---

## 🔑 Concepts to Master in Python (Coming from JavaScript)

**🔤 1. Data Types and Structures**

- `list`, `dict`, `tuple`, `set`
- Immutability: tuples vs lists
- Comprehensions (`[x for x in items]`, `{k: v for ...}`)

**🔁 2. Loops and Iteration**

- `for x in list`, `enumerate()`, `zip()`, `range()`
- `map()`, `filter()`, `lambda`

**📦 3. Functions and Scope**

- `def`, `*args`, `**kwargs`
- Closures, decorators (like JS higher-order functions)

**🧱 4. OOP (Object-Oriented Programming)**

- Classes, `self`, inheritance
- `@classmethod`, `@staticmethod`, `@property`

**📚 5. Modules and Packages**

- `import math`, `from x import y`
- Using `pip`, `venv`, and Python environments

**🔧 6. Error Handling**

- Python: `try/except/finally`
- JS: `try/catch/finally`

**🧪 7. Testing and Tooling**

- `unittest`, `pytest`
- Linting with `flake8`, formatting with `black`

**💡 8. Idiomatic Python (a.k.a. “Pythonic” Code)**

- Readability first: "There should be one — and preferably only one — obvious way to do it."
- Use list comprehensions, unpacking, meaningful names, avoid over-engineering

---

## 🧗‍♂️ Next Steps

1.  **Write code daily** – Solve small problems.
2.  **Build projects** – Web apps (Flask, Django), scripts, automation.
3.  **Read others’ Python code** – Open source or GitHub.
4.  **Read the Zen of Python** – `import this`
