# `dir()` function

The `dir()` function in Python is a ==built-in function== used to get a list of attributes of an object. It's a powerful tool for introspection, allowing you to explore the properties and methods available for various objects.

## Syntax:

```bash title="Python"
dir([object])
```

- `object`: (Optional) The object whose attributes you want to explore. If not provided, it returns the names in the current namespace.

---

## How it works:

### Without an argument:

When used without an argument, `dir()` returns a list of names in the current scope (local namespace). This includes variables, functions, and imported modules.

### With an object:

When used with an object as an argument, `dir()` returns a list of attributes and methods defined for that object. This includes attributes defined directly by the object, as well as those inherited from its class and base classes.

### Customization:

If an object has a `__dir__()` method, `dir()` will call this method to get the list of attributes. This allows objects with custom attribute access behavior to customize how `dir()` reports their attributes.

---

## Common Use Cases:

- **Exploring objects**: Discovering what methods and attributes are available for an object.
- **Inspecting modules**: Listing the functions and variables defined within a module.
- **Debugging**: Checking the names available in a specific scope.
- **Learning**: Understanding the functionality of an object or module.

---

## Examples:

```py title="Python"
# Without an object
print(dir())

# With a list object
my_list = [1, 2, 3]
print(dir(my_list))

# With a string object
my_string = "hello"
print(dir(my_string))

# With a module
import math
print(dir(math))
```

[More Advanced Example](https://www.pythoncheatsheet.org/builtin/dir)

## Key Points:

- The `dir()` function returns a list of strings, representing the names of attributes and methods.
- The returned list is sorted alphabetically.
- It's a valuable tool for understanding the structure and capabilities of Python objects and modules.

---

## Reference

- [pythoncheatsheet.org: Python dir() built-in function ](https://www.pythoncheatsheet.org/builtin/dir)
- [w3schools.com: Python dir() Function](https://www.w3schools.com/python/ref_func_dir.asp)
- [programiz.com: Python dir()](https://www.programiz.com/python-programming/methods/built-in/dir)
- [github.com: python-cheatsheet](https://github.com/wilfredinni/python-cheatsheet)
- [geeksforgeeks.org: Python: Difference between dir() and help()](https://www.geeksforgeeks.org/python-difference-between-dir-and-help/)
- [Python: Difference between dir() and help()](https://www.geeksforgeeks.org/python-difference-between-dir-and-help/)
