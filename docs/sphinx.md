---
permalink: /docs/sphinx/
level: 2
prev: ../jekyll/
---

# Sphinx

_Sphinx_ is used to generate Documentation **.html** pages from docstrings embedded in the **.py** files for a _Python_ package.

<hr/>
## Get Started

> The following tutorial is supplementary to _Sphinx_ [official](http://www.sphinx-doc.org/en/stable/tutorial.html) for Das Lab practise.

* Install _Sphinx_ via `pip`:

```bash
pip install sphinx
```

* Command `sphinx-quickstart` should be available if properly installed.

> For unknown reasons, you may not have `sphinx-quickstart` executable anywhere. No solution was found online for this case. As a temporary fix, go to the GitHub repository [Sphinx](https://github.com/sphinx-doc/sphinx), download the `sphinx-build.py` file to local, and manually link it by:

```bash
chmod +x /path/to/sphinx-build.py
sudo ln -s /path/to/sphinx-build.py /usr/local/bin/sphinx-build
```


Now creates a `docs/` folder inside the directory tree:

```
├── PackageName/
│   ├── package_name/
│   ├── docs/ 
│   ├── examples/
│   ├── setup.py
│   └── README
```
{: style="line-height:1em"}

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
{: style="line-height:1em"}

* You can run `make html` while under `docs/` to compile from your `source/*.rst` to `build/html/*.html`.

<hr/>
## Theme

* Clone or download the [**RiboKit Theme**](https://github.com/ribokit/ribokit-Sphinx-theme) and place under your project directory. Create a `_theme/` folder:

```
├── docs/
│   ├── source/ 
│   │   ├── _theme/
│   │   │   └── ribokit-Sphinx-theme/
...
```
{: style="line-height:1em"}

Now in your `source/conf.py`, add the following lines:

```python
html_theme = 'ribokit-Sphinx-theme'
html_theme_path = ['_theme']
html_theme_options = {
    'description': 'PCR Assembly Primer Design',
    'author': author.split(',')[0].strip(),
    'github_repo': 'ribokit/Primerize',
    'ga_tracker': 'UA-12345678-9'
}
html_additional_pages = {'404': '404.html'}
```

There are several options that are passed from `conf.py` into _Sphinx_ when making **.html**. Their default values are defined in `source/_theme/ribokit-Sphinx-theme/theme.conf`:

| Key | Value |
| --- | --- |
| `description` | The subtitle for display. For acronyms, mark the initials with `<u>` for highlighting (on hover). |
| `author` | The creator of the page. It will be displayed in the footer. |
| `github_repo` | The repository name in format of `organization/repository`. This powers the "View on GitHub" and "Download" buttons. |
| `ga_tracker` | Google Analytics tracker ID. |
| `collapse_navigation` | Boolean flag for whether the `<ul>` of sidebar are expanded; default is `true`. |
| `display_version` | Boolean flag for whether to display current package version next to search box; default is `true`. |

* Copy the `sphinx_make.sh` from **Theme** repository into `docs/sphinx_make.sh`. This script is used for final submission to RiboKit website.

> When testing, call `make clean && make html` instead, to exclude file removal.

<hr/>
## Configuration

> For an example `source/conf.py`, see [here](conf/).

You might also want to exclude certain **Theme** and Docs related files from your repository. Here is an example of `.gitignore`:

```bash
build/
dist/
docs/build
docs/source/_theme

package.egg-info/
*.pyc
```

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
# Submit to RiboKit

## Mechanism

The GitHub Pages are hosted either at organization level via a `organization/organization.github.io` repository, or at each repository level as a `gh-pages` branch.

**For _Sphinx_ docs, we use `gh-pages` branch to keep the doc together with the code**; while _Jekyll_ tutorials are using the other option.

> This choice adds overhead for branch switching and copy of RiboKit theme for each repository. The other option should work well too. But we choose this way only for keeping docs with code in same repository.

**The above overhead is due to:**{: style="color:#ff5c2b;"}

* GitHub Pages require `gh-pages` branch; `master` does not work;

* The **.html** files has to be at root (`/`) of `gh-pages`, inside `build/html/` does not work;

* _Sphinx_ output **.html** to `build/html` and you can't change the default path;

* The docstrings are inside **.py** files, so they live in `master`.

> It would work if you have a `.sh` script that moves `build/html/` to `/` after `make html`; and you keep `gh-pages` in sync with `master`. However, having a lot of **.html** files at the root(`/`) of your code base is **UGLY**{: style="color:#ff5c2b;"}! We do not recommend this option.

<hr/>
## Integration

<br/>

### First Time

For first time setup, you also need to create a `.nojekyll` and `_config.yml` file:

* `.nojekyll`: to tell GitHub Pages do not parse your **.html** files using the _Jekyll_ engine;

* `_config.yml`: GitHub Pages (powered by _Jekyll_) ignores all folders that start wiht underscore (`_`) by default. Sadly, _Sphinx_ creates `_static`, _etc._ folder and the name is not configurable.

Thus, we create a `_config.yml` file to force include those folders. Otherwise, the static resources (_JS_, _CSS_, images) will return _404_ response. 

```yaml
include:
    - _images
    - _sources
    - _static
    - _modules
    - _templates
```

<br/>

### Submit

Before submitting to RiboKit, make sure you check against [**Doc Standards**](../). Once satisfactory:

> **First `commit` and `push` all your changes to `master`!**

> Run `docs/sphinx_make.sh` at root folder (`/`). 

Here is a break-down for what it does:

* In `master` branch, execute `make clean && make html`.

* Remove unnecessary files in `build/html/_static/`.

* **Switch to `gh-pages` branch**, i.e. `git checkout gh-pages`.

* Copy over the entire `build/html/` folder as root (see below).

* Push the changes of `gh-pages` to GitHub. **The website should be updated automatically** (may be with some delay _[< 30s]_).

* Switch back to `master` for everyday use.

> To take advantage of this automated script, you need to further edit your `.gitignore` file to exclude files from the other branch. For example, this is the `.gitignore` for `master` branch:

```
build/
dist/
docs/build
docs/source/_theme

primerize.egg-info/
*.pyc

/.nojekyll
/*.html
/*.js
/objects.inv
_static/
_sources/
_images/
```

And for `gh-pages`, its `.gitignore` is:

```
build/
dist/
docs/
MATLAB/

primerize/
primerize.egg-info/
setup.py
requirements.txt
```

> The above setup saves you from the hassle of manually switch branches and keeping files. The `.gitignore` makes it easy that you do not lose any the ignored files, e.g. the `build/` and `dist/`. Otherwise, when you switch back to `master`, the previous built _Python_ packge is gone.

> Some more readings: [this](https://gist.github.com/chrisjacob/833223) and [this](https://talk.jekyllrb.com/t/whats-the-best-way-to-update-github-pages/2100/3).

<br/>

### Double Check


**After `make html`, your `master` should like like this**:

```
[master]
├── PackageName/
│   ├── package_name/
│   │   ├── __init__.py
│   │   └── ...
│   │
│   ├── docs/ 
│   │   ├── build/
│   │   │   ├── doctree/
│   │   │   └── html/
│   │   │       ├── _images/
│   │   │       ├── _sources/
│   │   │       ├── _static/
│   │   │       └── index.html
│   │   ├── source/ 
│   │   │   ├── _static/
│   │   │   ├── _templates/
│   │   │   ├── conf.py
│   │   │   └── index.rst
│   │   └── Makefile
│   │
│   ├── examples/
│   ├── setup.py
│   └── README
```
{: style="line-height:1em"}

**Move the entire `build/html/` to your `gh-pages`**:

```
[gh-pages]
├── PackageName/
│   ├── _images/
│   ├── _sources/
│   ├── _static/
│   ├── index.html
│   │
│   ├── .nojekyll
│   └── _config.yml

```
{: style="line-height:1em"}

