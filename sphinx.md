---
layout: docs
permalink: /std/sphinx/
root: /std/

title: Doc Standards
description: "Internal Guideline on Writing <u>St</u>an<u>d</u>ards"
author: Siqi Tian
---

# Sphinx Integration

<hr/>
## Get Started

> The following tutorial is supplementary to _Sphinx_ [official](http://www.sphinx-doc.org/en/stable/tutorial.html) for Das Lab practise.

* Install _Sphinx_ via `pip`:

```bash
pip install sphinx
```

* Command `sphinx-quickstart` should be available if properly installed.

Now creates a `docs/` folder inside the directory tree:

```
├── PackageName/
│   ├── package_name/
│   ├── docs/ 
│   ├── examples/
│   ├── setup.py
│   ├── README
```

Now at `PackageName/` (root), run `sphinx-quickstart`. It asks a lot of questions. All of them can be changed later in `conf.py`. Here are some important ones:

> Root path for the documentation [.]: **docs**

> Separate source and build directories (y/n) [n]: **y**

> autodoc: automatically insert docstrings from modules (y/n) [n]: **y**

> Create Makefile? (y/n) [y]: **y**

> Create Windows command file? (y/n) [y]: **n**

Now you should have:

```
├── docs/
│   ├── build/
│   ├── source/ 
│   │   ├── _static/
│   │   ├── _templates/
│   │   ├── conf.py
│   │   ├── index.rst
│   ├── Makefile
```

* You can run `make html` while under `docs/` to compile from your `source/*.rst` to `build/html/*.html`.

<hr/>
## Theme

