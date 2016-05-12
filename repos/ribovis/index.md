---
permalink: /RiboVis/
---

# <samp>RiboVis</samp>

[![1q9a Example Image](https://raw.github.com/ribokit/RiboVis/master/1q9a.png "1q9a Example Image"){: .half}](https://raw.github.com/ribokit/RiboVis/master/1q9a.png)
{: .center}

**RiboVis** is a set of useful and short *Python* functions for rendering RNA and proteins in PyMOL in our 'lab style'. For a quick preview:

| Function | Description |
| --- | --- |
| `rr()` | For RNA: renders 2&prime;-OH as spheres, bases as filled rings, and backbone as cartoon ribbons, rainbow-colored from 5&prime; to 3&prime;. No hydrogens, white background. |
| `rd()` | For proteins: side chains are all-atom and colored _CPK_, backbone is rainbow cartoon from N to C terminus. |
| `sa()` | Superimposes all models to the first one. _Thanks to Kyle Beauchamp for this one_ |

And more, including coloring 3D structures by chemical mapping data and other rendering options!

<hr/>
## Installation

To install **RiboVis**, simply:

- From GitHub, download the zip or tar file of the repository and unpack; or 

```bash
git clone https://github.com/ribokit/RiboVis.git
```

- To use RiboVis, open _PyMOL_ and type:

```python
import sys
sys.path.append('/path/to/RiboVis')
run /path/to/RiboVis/ribovis.py
```

* Replace `/path/to/` with the actual path to your RiboVis folder.
* **Optionally,** you can create or edit a `.pymolrc` file in your home directory (on Mac; on Windows, create or edit `.pymolrc` in 'C:\Program Files\PyMOL\PyMOL\'), and add the above commands. This will automatically load `ribovis.py` whenever PyMOL is started.

To quickly test RNA rendering, run:

```python
fetch 1q9a
rr()
```

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

README by [**t47**](http://t47.io/), *April 2016*, edits by **Clarence Cheng**, *May 2016*.

