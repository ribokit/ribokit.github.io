---
permalink: /docs/text/
level: 2
next: ../image/
---

# Text Format

<hr/>
## Markdown <small>(_Jekyll_ / _Tutorial_)</small>

> A simple guide on how to use _Markdown_ syntax is [here](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet).

Here are some best practices:

* Only `<h1>` and `<h2>` level headers are registered to the side navbar by _Jekyll_.

* Always use syntax highlighting for code blocks.

* Use blockquotes `> ` for advanced tips and explanations.

* Always separate sections with `<hr/>`.

* URL Links are **case sensitive**!

> An example of tutorial made by _Markdown_ is `hitrace`, see [here](/hitrace/tutorial/step_6/).

<hr/>
## Docstring <small>(_Python_ / _Sphinx Docs_)</small>

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

