---
layout: docs
permalink: /std/
root: /std/

title: Doc Standards
description: "Internal Guideline on Writing <u>St</u>an<u>d</u>ards"
author: Siqi Tian
---

# Documentation Standards

This page is intended to standarize documentation and tutorial writing format for **RiboKit** website. 

> The repository is organized that each package has its own folder. The landing page should be named as `index.md` or `index.html`. Please follow this rule on contributing! 

<hr/>
## Markdown

A simple guide on how to use _Markdown_ syntax is [here](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet).

Here are some best practices:

* Only `<h1>` and `<h2>` level headers are registered to the side navbar by _Jekyll_.

* Always use syntax highlighting for code blocks.

* Use blockquotes `> ` for advanced tips and explanations.

* Always separate sections with `<hr/>`.

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

_[future]_

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

