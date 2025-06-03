# Publishing Your Package to PyPI

## Step 1: Prepare your package structure

Make sure your package folder looks something like this:

```
mytools/
    __init__.py
    string_ops.py
    number_ops.py
setup.py
README.md
LICENSE
```

- `setup.py` is a script that tells Python how to build and distribute your package.
- `README.md` describes your package.
- `LICENSE` is the license for your package (e.g., MIT, Apache 2.0).

---

## Step 2: Write your `setup.py`

Here’s a basic example of `setup.py` using `setuptools`:

```py
from setuptools import setup, find_packages

setup(
    name='mytools',  # Your package name, must be unique on PyPI
    version='0.1.0',
    author='Your Name',
    author_email='you@example.com',
    description='A package for string and number operations',
    long_description=open('README.md').read(),
    long_description_content_type='text/markdown',
    url='https://github.com/yourusername/mytools',  # Optional
    packages=find_packages(),
    classifiers=[
        'Programming Language :: Python :: 3',
        'License :: OSI Approved :: MIT License',
        'Operating System :: OS Independent',
    ],
    python_requires='>=3.6',
)
```

---

## Step 3: Build your package

Install build tools if you don’t have them:

```bash
pip install build
```

Run this to build your package:

```bash
python -m build
```

It creates `dist/` folder with `.tar.gz` and `.whl` files.

---

## Step 4: Upload your package to PyPI

1.  **Install twine**:

    ```bash
    pip install twine
    ```

2.  **Upload package**:

    ```bash
    twine upload dist/*
    ```

    You’ll need a PyPI account (create one at [pypi.org](#)).

---

## Step 5: Install your package with pip

Once uploaded, anyone can install your package with:

```bash
pip install mytools
```
