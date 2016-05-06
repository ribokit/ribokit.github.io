---
permalink: /docs/
---

# Documentation Standards

This page is intended to standarize documentation and tutorial writing format for **RiboKit** website. 

> The repository is organized that each package has its own folder. The landing page should be named as `index.md` or `index.html`. Please follow this rule when contributing! 

<hr/>
## Markdown

> A simple guide on how to use _Markdown_ syntax is [here](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet).

Here are some best practices:

* Only `<h1>` and `<h2>` level headers are registered to the side navbar by _Jekyll_.

* Always use syntax highlighting for code blocks.

* Use blockquotes `> ` for advanced tips and explanations.

* Always separate sections with `<hr/>`.

> An example of tutorial made by _Markdown_ is `hitrace`, see [here](/hitrace/tutorial/step_6/).


<hr/>
## Jekyll

This site is hosted on [GitHub Pages](https://pages.github.io/), powered by [Jekyll](https://jekyllrb.com/). The **.md** and **.html** files inside the repository are automatically discovered. For _Markdown_ files, _Jekyll_ uses a [**Front Matter**](https://jekyllrb.com/docs/frontmatter/) block for configurations.

In your **.md** file, use a header like this:

```go
---
layout: docs
permalink: /hitrace/tutorial/bonus_2d/
root: /hitrace/
prev: ../../biers/varna/
next: bonus_3d/

title: HiTRACE
description: "<u>Hi</u>gh-<u>T</u>hroughput <u>R</u>obust <u>A</u>nalysis for <u>C</u>apillary <u>E</u>lectrophoresis"
repo: hitrace/hitrace
author: Siqi Tian
---
```

* **System Fields**:

| Key | Value |
| --- | --- |
| `layout` | The layout template for the page. Choose from `default` (landing page for each package) and `docs` (leaf level page with navigation buttons). |
| `permalink` | The URL that the page responds to. Always start and end with `/`. |

* **Descriptive Fields**:

| Key | Value |
| --- | --- |
| `title` | The display title for the page. It will be displayed after the "RiboKit :" prefix; before the "\| RiboKit" suffix in browser title. |
| `description` | The subtitle for display. For acronyms, mark the initials with `<u>` for highlighting (on hover). |
| `repo` | The repository name in format of `organization/repository`. This powers the "View on GitHub" and "Download" buttons. If left out, those buttons are hidden. |
| `author` | The creator of the page. It will be displayed in the footer. |

* **Navigation Fields**:

| Key | Value |
| --- | --- |
| `root` | The root parent of the page. This will be used by the _up arrow_ button. |
| `prev` | The previous page, used for tutorial series. This will be used by the _left arrow_ button. The final (relative) URL is prepended with `../` (so you don't need to type it). |
| `next` | The next page, used for tutorial series. This will be used by the _right arrow_ button. The final (relative) URL is prepended with `../` (so you don't need to type it). |

<hr/>
## Sphinx

> The **.html** files made by _Sphinx_ should be using the [**RiboKit Theme**](https://github.com/t47io/ribokit-Sphinx-theme). Please see more details on configurations here: [**_Sphinx_ Integration**](/std/sphinx/).

For basic _Python_ docstring standards, see [PEP 257](https://www.python.org/dev/peps/pep-0257/). When using `sphinxcontrib-napoleon`, see this [example](http://sphinxcontrib-napoleon.readthedocs.io/en/latest/example_google.html) and [module](http://www.sphinx-doc.org/en/stable/ext/napoleon.html) for **Google Style** writing.

> The docstring is based on _reStructuredText_, see tutorials [here](http://www.sphinx-doc.org/en/stable/rest.html) and [here](https://gist.github.com/dupuy/1855764).

* To color label the "**Parameters**" and "**Attributes**", use `:` for separation and double `` ` `` for type (`<code>`) label. For example:

```md
"""Result of a ``primerize.Primerize_1D.design()`` run.

Args:
    init_dict: A ``dict`` with the following keys:

    sequence: ``str``: Sequence of assembly design.
    name: ``str``: Construct prefix/name.
    is_success: ``bool``: Flag for whether ``primerize.Primerize_1D.design()`` run successfully found a solution.
    primer_set: ``list(str)``: List of primers for assembly.
    params: ``dict``: Dictionary of parameters used for this result.
    data: ``dict``: Dictionary of result data.

Attributes:
    sequence: ``str``: Sequence of assembly design.
    name: ``str``: Construct prefix/name.
    is_success: ``bool``: Flag for whether a solution is found.
    primer_set: ``list(str)``: Strings of solution primers.
    _params: Input parameters, in format of ``dict: { 'MIN_TM': float, 'NUM_PRIMERS': int, 'MIN_LENGTH': int, 'MAX_LENGTH': int, 'N_BP': int, 'COL_SIZE': int, 'WARN_CUTOFF': int }``.
    _data: Data of assembly solution, in format of ``dict: { 'misprime_score': [str, str], 'warnings': list(list(int)), 'assembly': primerize.util.Assembly }``.
"""
```

* It is recommended to use double `` ` `` around values and class instances. Use `**` around arguments for color matching:

```md
"""Get result parameters.

Args:
    key: ``str``: Keyword of parameter. Valid keywords are ``'MIN_TM'``, ``'NUM_PRIMERS'``, ``'MIN_LENGTH'``, ``'MAX_LENGTH'``, ``'COL_SIZE'``, ``'WARN_CUTOFF'``, ``'WARNING'``, ``'PRIMER'``, ``'MISPRIME'``; case insensitive.

Returns:
    value of specified **key**.

Raises:
    AttributeError: For illegal **key**.
"""
```

* Exception classes will be colored red. 

* When you need a block, end the line with ``::``:

```md
Attributes:
    ...
    _data: Data of assembly solution, in format of ::

            dict: {
                'constructs': primerize.util.Construct_List,
                'plates': list(list(primerize.util.Plate_96Well)),
                'assembly': primerize.util.Assembly,
                'illustration': { 'labels': list(str), 'fragments': list(str), 'lines': tuple(str) }
            }

        For ``primerize.Primerize_2D.design()`` results, it also has ``'bps': list(tuple(int, int))``.
```

* For _Optional_ arguments, italicize with `` `(Optional)` ``:

```md
"""Print result in rich-text.

Args:
    ref_primer: ``list(str)``: `(Optional)` List of Wild-type **primer_set** for highlighting. If nonspecified, highlighting is disabled.

Returns: 
    ``str``
"""
```

> An example of _Python_ documentation made by _Sphinx_ is `primerize`, see [here](/primerize/primerize.wrapper).


<hr/>
## Images

Similar to what is described in [here](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet), the syntax for inserting an image in your write-up is:

```md
[![alt text](/path/to/image "hover text"){: .half}](/url/of/click)
{: .center}
```

* The _url/of/click_ should point to a `href` for this image's parent `<a>`. Or just use the same as _/path/to/image_.

* Append the `{: .center}` line to align the image at center.

* Add the `{: .half}` class for image sizing. Here are the options:

| Class | Description |
| --- | --- |
| `full` | One image per line. The image will be displayed with `width: 90%;`. |
| `half` | Two images per line. The image will be displayed with `width: 45%;`. |
| `right` | The image will be displayed with `float: right;` with a `width: 150px;`. You may need to add several `<br/>` to lengthen the page for the floating element. |

Last but not the least, please process your image before committing:

* **Use .png or .jpg format**.

* **Resize your image**. Images are displayed with a fixed size thus ultra-high resolution images are unnecessary. All images should be **72 _dpi_** for web browsing. Higher _dpi_ is a waste of resources.

* **Optimize your image**{: style="color:#ff5c2b;"}! Please use the tool [**ImageOptim**](https://imageoptim.com/mac) to compress your image first. Screenshots usually have their size reduced by _> 20%_.

* **Place in a `res/` folder** inside your package folder. Images and other resources for a tutorial should stay with its package **.md** or **.html** files. This helps the repository organization.

