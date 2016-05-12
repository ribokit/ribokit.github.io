---
permalink: /RiboVis/
---

# <samp>RiboVis</samp>

[![1q9a Example Image](https://raw.github.com/ribokit/RiboVis/master/1q9a.png "1q9a Example Image"){: .half}](https://raw.github.com/ribokit/RiboVis/master/1q9a.png)
{: .center}

**RiboVis** is a set of useful and short *Python* functions for making pictures of RNA and proteins in pymol in our 'lab style'. For a quick preview:

| Function | Description |
| --- | --- |
| `rr()` | For RNA: with 2&prime; OH as spheres, bases as filled rings, and backbone as cartoon ribbons, rainbow colored from 5&prime; to 3&prime;. No hydrogens, white background. |
| `rd()` | For proteins: side chains are all-atom and colored _CPK_, backbone is rainbow cartoon from N to C terminus. |
| `sa()` | Superimposes all models to the first one. _Thanks to Kyle Beauchamp for this one_ |

And more! ...

<hr/>
## Installation

To install **RiboVis**, simply:

- From GitHub, download the zip or tar file of the repository and unpack; or 

```bash
git clone https://github.com/ribokit/RiboVis.git
```

- In _PyMol_, type:

```python
run ribovis.py
```

Tested quickly with:

```python
fetch 1q9a
rr()
```

- _(Optional)_ Create or edit a `.pymolrc` file in your home directory, add these lines:

```python
import sys
sys.path.append('/path/to/RiboVis')
run /path/to/RiboVis/ribovis.py
```

> Replce with your `/path/to/ribovis`.

This will automatically load `ribovis` upon start every time.

<hr/>
## Documentation

* #### *Python* Documentation is available at: [**docs/**](docs/).

<hr/>
## License

Copyright &copy; of **RiboVis** _Source Code_ is described in [LICENSE.md](https://github.com/ribokit/RiboVis/blob/master/LICENSE.md).

<hr/>
## Related Packages

* [**HiTRACE**](https://hitrace.github.io/HiTRACE/)


<hr/>
Developed by **Das lab**, _Leland Stanford Junior University_.

README by [**t47**](http://t47.io/), *April 2016*.

