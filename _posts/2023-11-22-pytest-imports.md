---
layout: post
title: Making sense of PyTest imports
date: 2023-11-22 15:10:00-0300
description: Importing things from sibling directories
tags: python
giscus_comments: false
related_posts: false
---

Python imports can get weird, specially when dealing with tests that are to be kept separate from the application code (i.e., in sibling directories).

This is a quick guide on how you can organize your tests with `pytest` so that everything works as expected.
If `pytest` is new for you, check out their [docs](https://docs.pytest.org/en/). PyTest is a framework for
writing small, readable tests for python programs.

I've kept this article as a note to myself and friends, and now I am publishing it online. It is made to be
brief, with minimal explanations, because it shows you an example of how to do something pretty simple.

Do note that while this is not the only way to make things work, it's my favorite out of everything I've come across before.


# Organizing `pytest` tests
## The code
Your code should be organized in packages, and the directory with all the tests should be right next to the package directories.

This might sound counterintuitive because the test code from the `tests` directory should not be able to reach your package, since it is not in a child directory. The reason this works, in a nutshell, is that `pytest` operates on a broader scope.

### Directory structure
```
pkg/
  code.py
tests/
  __init__.py
  test_code.py
```

### File structure
As for your files, you can basically use imports as you would feel the most comfortable doing: from each package you can import a module, or something from this module.

The `tests` package needs an `__init__` file.

```python
# pkg/code.py
def f(x):
    return x+2
```

```python
# tests/__init__.py
# (may be left empty)
```

```python
# tests/test_code.py
from pkg.code import f


def test_f():
    assert f(2) == 4
```

# The testing
Now you can run your tests with the `pytest` command. That's it! 😊
