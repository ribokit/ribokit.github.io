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
│   └── README
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
│   │   └── index.rst
│   └── Makefile
```

* You can run `make html` while under `docs/` to compile from your `source/*.rst` to `build/html/*.html`.

<hr/>
## Theme

* Clone or download the [**RiboKit Theme**](https://github.com/t47io/ribokit-Sphinx-theme) and place under your project directory. Create a `_theme/` folder:

```
├── docs/
│   ├── source/ 
│   │   ├── _theme/
│   │   │   ├── ribokit-Sphinx-theme/
...
```
Now in your `source/conf.py`, add the following lines:

```python
html_theme = 'ribokit-Sphinx-theme'
html_theme_path = ['_theme']
html_theme_options = {
    'description': 'PCR Assembly Primer Design',
    'author': author.split(',')[0].strip(),
    'github_repo': 'DasLab/Primerize',
    'ribokit_flag': True
}
```

There are several options that are passed from `conf.py` into _Sphinx_ when making **.html**. Their default values are defined in `source/_theme/ribokit-Sphinx-theme/theme.conf`:

| Key | Value |
| --- | --- |
| `description` | The subtitle for display. For acronyms, mark the initials with `<u>` for highlighting (on hover). |
| `author` | The creator of the page. It will be displayed in the footer. |
| `github_repo` | The repository name in format of `organization/repository`. This powers the "View on GitHub" and "Download" buttons. |
| `collapse_navigation` | Boolean flag for whether the `<ul>` of sidebar are expanded; default is `true`. |
| `display_version` | Boolean flag for whether to display current package version next to search box; default is `true`. |
| `ribokit_flag` | Flag for testing or RiboKit deployment; default is `false`. When testing the docs locally, use `false`; when generating **.html** files for RiboKit site, use `true`. This toggles the _CSS_ and _JS_ static asset path only. |

> The `ribokit_flag` variable is very important. It dictates whether static _CSS_ and _JS_ files can be loaded successfully. The RiboKit server uses a different path to avoid repeated files in the repository.

* Copy the `sphinx_make.sh` from **Theme** repository into `docs/sphinx_make.sh`. This script is used for final submission to RiboKit website.

> The `sphinx_make.sh` script removes repeated/shared _CSS_ and _JS_ files from the `build/html` folder, so you can later copy the enitre folder to the RiboKit site.

> When testing, call `make clean && make html` instead, to exclude file removal.

<hr/>
## Configuration

> For an example `source/conf.py`, see [here](conf/).

<br/>

### Autodoc

The `autodoc` [extension](http://www.sphinx-doc.org/en/stable/ext/autodoc.html) from _Sphinx_ enables pulling out docstrings of your package code automatically. You need the following settings in your `source/conf.py`:

```python
extensions = [
    'sphinx.ext.autodoc',
    'sphinx.ext.autosummary',
    'sphinx.ext.napoleon',
    'sphinx.ext.todo',
    'sphinx.ext.mathjax',
    'sphinx.ext.githubpages',
]

autodoc_member_order = 'groupwise'
autodoc_default_flags = ['members', 'show-inheritance']
autosummary_generate = True
```

You will need to generate **.rst** (placeholder) files into your `source/` folder so that _Sphinx_ will traverse your **.py** files. Run with:

```bash
sphinx-apidoc -f -e -o docs/source/ package/
```

> Run this at your `PackageName/` (root) directory.

> **You only need to run this once.** Unless there are new **.py** files in your package later.

> Unfortunately, the `sphinx-apidoc` does not honor `autodoc_default_flags` setting. So you will need to manually edit the generated **.rst** files if needed.

<br/>

### Napoleon

The `napoleon` [extension](http://www.sphinx-doc.org/en/stable/ext/napoleon.html) from _Sphinx_ enables writing _Google Style_ docstrings (see [here](http://sphinxcontrib-napoleon.readthedocs.io/en/latest/example_google.html)). It may be more intuitive for some people.

Similarly, enable the extension, and add these settings:

```python
napoleon_google_docstring = True
napoleon_include_private_with_doc = False
napoleon_include_special_with_doc = True
napoleon_use_rtype = False
```

<hr/>
## Submit to RiboKit

Before submitting to RiboKit, make sure you check against [**Doc Standards**](../). Once satisfactory, follow these steps:

* Run `sphinx_make.sh`.

> Make sure that `ribokit_flag` is set to `True` in `source/conf.py` for submission!

* Clone or checkout `ribokit/ribokit.github.io` a copy to your local enviroment.

* Inside `ribokit/ribokit.github.io` repository, create a folder for your package.

> Use lower case letter of package name only. **No spaces. Replace `-` with `_` (underscore).**

* Copy the entire `build/html` folder into the package folder in `ribokit/ribokit.github.io`:

```
├── ribokit.github.io/
│   ├── _includes/
│   ├── _layouts/
│   ├── assets/
...
│   ├── package/
│   │   ├── _images/
│   │   ├── _sources/
│   │   ├── _static/
│   │   ├── index.html
...
│   └── _config.yml
```

* Push the changes to GitHub. The website should be updated automatically (may be with some delay _[< 30s]_).

