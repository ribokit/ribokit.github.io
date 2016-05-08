
---
permalink: /docs/jekyll/
level: 2
prev: image/
next: sphinx/
---

# Jekyll

This site is hosted on [GitHub Pages](https://pages.github.io/), powered by [Jekyll](https://jekyllrb.com/). The **.md** files inside the repository are automatically discovered. 

<hr/>
## Front Matter

For _Markdown_ files, _Jekyll_ uses a [**Front Matter**](https://jekyllrb.com/docs/frontmatter/) block for configurations.

In your **.md** file, use a header like this:

```go
---
layout: docs
permalink: /HiTRACE/tutorial/bonus_2d/
root: /HiTRACE/
prev: ../../Biers/varna/
next: bonus_3d/

title: HiTRACE
description: "<u>Hi</u>gh-<u>T</u>hroughput <u>R</u>obust <u>A</u>nalysis for <u>C</u>apillary <u>E</u>lectrophoresis"
repo: hitrace/HiTRACE
author: Siqi Tian
---
```

> Remember that all URL path (`permalink`, `root`, `prev`, `next`) are **CASE SENSITIVE**. Use spellings that match the actuall repository name!

* **System Fields**:

| Key | Value |
| --- | --- |
| `layout` | The layout template for the page. Use `default` for all pages; use `redirect` for redirecting a `permalink` to a new address (with a 301 page, see `redirect_to`). |
| `level` | The level for the page. This controls the navigation banner: `0` displays "Visit Lab" button; used for domain index page only (e.g. `https://ribokit.github.io`). `1` displays "View GitHub" and download package for repository; used for landing page of each package (e.g. `https://ribokit.github.io/RiboVis/`). `2` displays "up", "prev", "next" navigation buttons; used for tutorial series (e.g. `https://hitrace.github.io/HiTRACE/tutorial/step_0/`). |
| `permalink` | The URL that the page responds to. Always start and end with `/`. |

* **Descriptive Fields**:

| Key | Value |
| --- | --- |
| `title` | The display title for the page. It will be displayed after the "RiboKit :" prefix; before the "\| RiboKit" suffix in browser title. |
| `description` | The subtitle for display. For acronyms, mark the initials with `<u>` for highlighting (on hover). |
| `repo` | The repository name in format of `organization/repository`. This powers the "View on GitHub" and "Download" buttons. If left out, those buttons are hidden. |
| `author` | The creator of the page. It will be displayed in the footer. |
| `ga_tracker` | Google Analytics tracker ID. This should only be set once globally as defaults. |

* **Navigation Fields**:

| Key | Value |
| --- | --- |
| `root` | The root parent of the page. This will be used by the _up arrow_ button. |
| `prev` | The previous page, used for tutorial series. This will be used by the _left arrow_ button. The final (relative) URL is prepended with `../` (so you don't need to type it). |
| `next` | The next page, used for tutorial series. This will be used by the _right arrow_ button. The final (relative) URL is prepended with `../` (so you don't need to type it). |
| `redirect_to` | New address to redirect a page. Only works when `layout` is `redirect`. Either relative or absolute path works. |

Example of link redirection:

```go
---
permalink: /biers/
redirect_to:  https://daslab.github.io/Biers/
---
```

<hr/>
## Defaults

Within the same package, the `title`, `description`, `repo`, `root`, _etc._ are usually the same across all pages. In the `_config.yml`, you can define default values globally:

```go
defaults:
  -
    scope:
      path: ""
    values:
      layout: "default"
      level: 1
      title: 
      author: "Siqi Tian"
      ga_tracker: UA-12345678-9
```

> The settings are global when `path: ""` is empty.

Also, you can define defaults for a package:

```go
defaults:
  -
    scope:
      path: "repos/ribovis"
    values:
      title: "RiboVis"
      description: "PyMol Commands by the Das Lab Style"
      repo: "ribokit/RiboVis"
      author: "Siqi Tian"
      root: "/RiboVis/"
```

Now for your individual **.md** files, you don't need to repeat the default variables.

<hr/>
# Submit to RiboKit

## Mechanism

The GitHub Pages are hosted either at organization level via a `organization/organization.github.io` repository, or at each repository level as a `gh-pages` branch.

**For _Markdown_ tutorials, we centralize the documents** into `organization/organization.github.io` repository; while _Sphinx_ docs are using the other option.

> This choice is due to complicated `baseurl` setup for `gh-pages`. The URL root (`/`) for each repository's `gh-pages` is actually `/package` in the browser, thus making it difficult to refer to static resources (_JS_, _CSS_, images). Also updating the RiboKit theme is more cumbersome since you need to go over each repository. Since the tutorials are unlikely to change frequently, the shared `organization/organization.github.io` repository is OK.

<hr/>
## Integration

Depending on your repository, it might go under `hitrace/hitrace.github.io`, `DasLab/daslab.github.io`, or other places.

> The repository is organized that each package has its own folder. Use lower case with underscores (`_`) for folder names. The landing page should be named as `index.md`. Please follow this rule when contributing!

* Double check the `permalink`, `root`, _etc._ paths with case sensitive.

* **Place images in a `res/` folder** inside your package folder. Images and other resources for a tutorial should stay with its package **.md** files. This helps the repository organization.

* If necessary, update the `organization/organization.github.io` index page for links to your new writing.

* Push the changes to GitHub. **The website should be updated automatically** (may be with some delay _[< 30s]_).
