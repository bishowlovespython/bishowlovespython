# JavaScript vs Python side-by-side cheat sheet

Here's a handy **JavaScript vs Python side-by-side cheat sheet** — perfect for quick comparisons as you switch gears.

---

## 📝 1. Variable Declaration

| Concept            | JavaScript                     | Python  |
| ------------------ | ------------------------------ | ------- |
| Declare a variable | `let x = 5;` or `const x = 5;` | `x = 5` |
| Dynamic typing     | Yes                            | Yes     |

---

## 🧮 2. Data Types

| Type          | JavaScript             | Python                 |
| ------------- | ---------------------- | ---------------------- |
| Number        | `let x = 42;`          | `x = 42`               |
| String        | `"hello"` or `'hello'` | `"hello"` or `'hello'` |
| Boolean       | `true`, `false`        | `True`, `False`        |
| Null / None   | `null`                 | `None`                 |
| Array / List  | `[1, 2, 3]`            | `[1, 2, 3]`            |
| Object / Dict | `{a: 1}`               | `{"a": 1}`             |
| Undefined     | `undefined`            | _No equivalent_        |

---

## 🔁 3. Conditionals

| JavaScript                     | Python       |
| ------------------------------ | ------------ |
| `if (x > 10) { ... }`          | `if x > 10:` |
| `else if`                      | `elif`       |
| `===` (strict equality)        | `==`         |
| `!==`                          | `!=`         |
| Logical AND / OR: `&&`, `\|\|` | `and`, `or`  |

---

## 🔄 4. Loops

| JavaScript                    | Python               |
| ----------------------------- | -------------------- |
| `for (let i = 0; i < 5; i++)` | `for i in range(5):` |
| `for (let item of list)`      | `for item in list:`  |
| `while (x < 10)`              | `while x < 10:`      |
| `break`, `continue`           | Same                 |

---

## 🔧 5. Functions

| JavaScript                             | Python                        |
| -------------------------------------- | ----------------------------- |
| `function add(a, b) { return a + b; }` | `def add(a, b): return a + b` |
| Arrow function: `(a, b) => a + b`      | Lambda: `lambda a, b: a + b`  |
| `function greet(name = "John")`        | `def greet(name="John")`      |

---

## 🧰 6. Objects vs Dictionaries

| JavaScript                        | Python                     |
| --------------------------------- | -------------------------- |
| `let person = {name: "Ana"}`      | `person = {"name": "Ana"}` |
| `person.name` or `person["name"]` | `person["name"]`           |

---

## 📦 7. Arrays/Lists

| JavaScript               | Python                                                |
| ------------------------ | ----------------------------------------------------- |
| `arr.length`             | `len(arr)`                                            |
| `arr.push(4)`            | `arr.append(4)`                                       |
| `arr.map(x => x * 2)`    | `map(lambda x: x * 2, arr)` or `[x * 2 for x in arr]` |
| `arr.filter(x => x > 0)` | `filter(...)` or list comprehension                   |

---

## 📚 8. Classes & OOP

| JavaScript                       | Python                                |
| -------------------------------- | ------------------------------------- |
| `class Dog { constructor() {} }` | `class Dog:\n    def __init__(self):` |
| `this.name = name`               | `self.name = name`                    |
| Method call: `dog.bark()`        | Same: `dog.bark()`                    |

---

## 🎯 9. Common Built-ins

| Task               | JavaScript         | Python       |
| ------------------ | ------------------ | ------------ |
| Print to console   | `console.log(x)`   | `print(x)`   |
| Length of item     | `arr.length`       | `len(arr)`   |
| Get keys of object | `Object.keys(obj)` | `obj.keys()` |
| Convert to string  | `String(5)`        | `str(5)`     |

---

## ⚠️ 10. Error Handling

| JavaScript                     | Python                                  |
| ------------------------------ | --------------------------------------- |
| `try { ... } catch(e) { ... }` | `try:\n    ...\nexcept Exception as e:` |

---

## 🧠 Pythonic Tips (vs JS Thinking)

| JS Habit                   | Pythonic Way                                   |
| -------------------------- | ---------------------------------------------- |
| Use `for` loop with index  | `for i, item in enumerate(list)`               |
| Create arrays manually     | Use list comprehensions                        |
| `==` vs `===` confusion    | Just use `==` (Python handles type well)       |
| Arrow functions everywhere | Prefer `def`, but use `lambda` for short cases |
| `let` vs `const` decisions | Python variables are reassigned freely         |
