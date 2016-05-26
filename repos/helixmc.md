ermalink: /helixmc/
title: RNAMake
author: Joseph Yesselman
---

# <samp>RNAMake</samp>

**HelixMC** is a software package for Monte-Carlo (MC) simulations of DNA/RNA helices 
using the base-pair level model. It provides a powerful tool to understand the flexibility of
DNA/RNA helices through numerical simulations.


<hr/>

## Dependencies 

* Python Dependencies: The required dependencies to build the software are Python >= 2.7, Numpy >= 1.6, Matplotlib >= 1.1.0, simplejson >= 3.8.

* C++ Dependencies: Either g++ or clang installed on system and also Ninja (https://ninja-build.org/) and CMake (https://cmake.org/)
	
	
<hr/>

## Installation

The easiest way to install is to use pip install::

    $ pip install helixmc

Alternatively, one can download the source code from the latest GitHub
repository. Simply run::

    $ git clone https://github.com/fcchou/HelixMC.git

Or you can go to https://github.com/fcchou/HelixMC/ and download the source
code by clicking the "Download ZIP" button.

After this, you can instal HelixMC using `setup.py`::

    $ python setup.py build
    $ sudo python setup.py install

Instead of installing using setup.py, you can just add your HelixMC folder
into the system's ``$PATH`` and ``$PYTHONPATH``. In bash this can be done by
adding the following lines to your ``~/.bashrc``::

    export PATH=$PATH:<HelixMC Path>
    export PYTHONPATH=$PYTHONPATH:<HelixMC Path>

Then build the Cython extension. Under the ``helixmc/`` folder, run::

    $ python _cython_build.py build_ext --inplace

Note that this requires you to have Cython installed. Otherwise you can choose
to build the c source file, then you do not need Cython::

    $ python _c_build.py build_ext --inplace

Now you should be all set. To test the install, simply run::

    $ helixmc-run --help


<hr/>
## Documentation

* #### *Python* Documentation is available at: [**http://helixmc.readthedocs.io/**](http://helixmc.readthedocs.io/).

<hr/>
## License

Copyright &copy; of **RNAMake** _Source Code_ is described in [LICENSE.md](https://github.com/ribokit/RiboVis/blob/master/LICENSE.md).

<hr/>
## Related Packages

* [**HiTRACE**](https://hitrace.github.io/HiTRACE/)


<hr/>
Developed by **Das lab**, _Leland Stanford Junior University_.

