---
permalink: /docs/image/
level: 2
prev: text/
next: jekyll/
---

# Image Format

<hr/>
## Alignment Class
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

<hr/>
## Size and Optimazation

Last but not the least, please process your image before committing:

* **Use .png or .jpg format**.

* **Resize your image**. Images are displayed with a fixed size thus ultra-high resolution images are unnecessary. All images should be **72 _dpi_** for web browsing. Higher _dpi_ is a waste of resources.

* **Optimize your image**{: style="color:#ff5c2b;"}! Please use the tool [**ImageOptim**](https://imageoptim.com/mac) to compress your image first. Screenshots usually have their size reduced by _> 20%_.

<hr/>
## Placement

* **Place in a `res/` folder** inside your package folder. Images and other resources for a tutorial should stay with its package **.md** or **.html** files. This helps the repository organization.
