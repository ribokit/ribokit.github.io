---
permalink: /RNAMake/
---

# <samp>RNAMake</samp>

**RNAMake** a toolkit for designing and optimizing RNA 3D structure.

And more! ...

<hr/>

## Dependencies 

* Python Dependencies: The required dependencies to build the software are Python >= 2.7, Numpy >= 1.6, Matplotlib >= 1.1.0, simplejson >= 3.8.

* C++ Dependencies: Either g++ or clang installed on system and also Ninja (https://ninja-build.org/) and CMake (https://cmake.org/)
	
	
<hr/>

## Installation of Python Module

To install **RNAMake**, simply:

- From GitHub, download the zip or tar file of the repository and unpack; or 

```bash
git clone https://github.com/jyesselm/RNAMake.git
```

To make sure you system can find the RNAMake folder into the system's $PATH and $PYTHONPATH. In bash this can be done by adding the following lines to your ~/.bashrc or ~/.bash_profile if you are using a mac:

```bash
export PATH=$PATH:<RNAMake Path>\n
export PYTHONPATH=$PYTHONPATH:<RNAMake Path>
```


- In _PyMol_, type:

```python
run pymol_daslab.py
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
run /path/to/RiboVis/pymol_daslab.py
```

> Replce with your `/path/to/pymol_daslab`.

This will automatically load `pymol_daslab` upon start every time.

<hr/>
## Documentation

* #### *Python* Documentation is available at: [**http://jyesselm.github.io/RNAMake/**](http://jyesselm.github.io/RNAMake/).
* #### *C++* Documentation is available at: [**http://jyesselm.github.io/RNAMake/html_cpp/index.html**](http://jyesselm.github.io/RNAMake/html_cpp/index.html).


<hr/>
## License

Copyright &copy; of **RNAMake** _Source Code_ is described in [LICENSE.md](https://github.com/ribokit/RiboVis/blob/master/LICENSE.md).

<hr/>
## Related Packages

* [**HiTRACE**](https://hitrace.github.io/HiTRACE/)


<hr/>
Developed by **Das lab**, _Leland Stanford Junior University_.

README by [**t47**](http://t47.io/), *April 2016*.

