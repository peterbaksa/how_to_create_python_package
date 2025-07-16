# How to create python package

## example package name: py_package

```
py-package/
│
├── py_package/         # package (moduls, __init__.py,..)
│   └── __init__.py
│   └── core.py         # (optional, your main module)
│
├── README.md
├── pyproject.toml
├── .gitignore
└── tests/               # (optional, for pytest)
    └── test_basic.py
```

## pyproject.toml
```toml
[project]
name = "py_package"
version = "1.0.1"
description = "Package short description here"
authors = [
    { name="Author Name", email="author.email@email.com" }
]
license = { text = "License type" }
readme = "README.md"
requires-python = ">=3.12"
dependencies = [
    "requests",
    "beautifulsoup4",
    "pytest"
]

[project.urls]
Homepage = "https://github.com/your_github_name/py-package"

[tool.setuptools.packages.find]
where = ["."]

# Build system configuration (required for pip/poetry)
[build-system]
requires = ["setuptools>=61.0"]
build-backend = "setuptools.build_meta"
```

## core.py
```python
def split_html_by_items(...): # Some function
    ...
```

## __init__.py
```python
__version__ = "1.0.1"
from .core import split_html_by_items as split 
```


# First commit - initialization 
```bash
git init
git add .
git commit -m "Initial release v1.0.1"
git tag v1.0.1
git branch -M main
git remote add origin git@github.com:your_github_name/py-package.git
git push -u origin main --tags
```

# What to change for next release - update version:
1. Update `version` in `pyproject.toml`
```toml
version = "1.0.2"
```
2. Update `__init__.py` with the new version
```python
__version__ = "1.0.2"
from .core import split_html_by_items as split
```
3. Commit changes:
```bash
git add .
git commit -m "List of changes.. + Release v1.0.2"
git tag v1.0.2
git push origin main -- tags
```