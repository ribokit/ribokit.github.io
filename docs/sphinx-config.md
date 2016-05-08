---
permalink: /docs/sphinx/config/
level: 2
---

# Example `conf.py` for _Sphinx_

<br/>

```python
from datetime import date
import sys
import os

sys.path.insert(0, os.path.abspath("../../"))

from primerize import __version__

extensions = [
    'sphinx.ext.autodoc',
    'sphinx.ext.autosummary',
    'sphinx.ext.napoleon',
    'sphinx.ext.todo',
    'sphinx.ext.mathjax',
    'sphinx.ext.githubpages',
]
templates_path = ['_templates']
html_static_path = ['_static']
exclude_patterns = ['_build', 'Thumbs.db', '.DS_Store']
source_suffix = '.rst'
master_doc = 'index'

# General information about the project.
project = u'Primerize'
copyright = u'2008-%s The Board of Trustees of the Leland Stanford Junior University. All Rights Reserved' % date.today().year
author = u'Siqi Tian, Rhiju Das'
language = 'en'

version = __version__
release = version


pygments_style = 'sphinx'
add_function_parentheses = True
add_module_names = True
show_authors = False
todo_include_todos = True
man_show_urls = True
modindex_common_prefix = []

html_domain_indices = True
html_use_smartypants = False
html_use_index = True
html_use_modindex = False
html_split_index = False
html_show_sourcelink = False
html_show_sphinx = True
html_show_copyright = True
html_copy_source = True
html_compact_lists = True
html_last_updated_fmt = '%b %d, %Y'
html_search_language = 'en'

html_title = project + version + ' : PCR Assembly Primer Design'
html_short_title = project + ' Documentation'
html_logo = None
html_extra_path = []
html_favicon = html_static_path[0] + '/primerize_icon.png'

html_sidebars = {}
html_context = {}
html_additional_pages = {}
html_style = []
html_theme = 'ribokit-Sphinx-theme'
html_theme_path = ['_theme']
html_theme_options = {
    'description': 'PCR Assembly Primer Design',
    'author': author.split(',')[0].strip(),
    'github_repo': 'DasLab/Primerize'
}

# Output file base name for HTML help builder.
htmlhelp_basename = 'Primerize_doc'


napoleon_google_docstring = True
napoleon_include_private_with_doc = False
napoleon_include_special_with_doc = True
napoleon_use_rtype = False
autodoc_member_order = 'groupwise'
autodoc_default_flags = ['members', 'show-inheritance']
autosummary_generate = True
```
