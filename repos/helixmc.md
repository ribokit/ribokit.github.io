---
permalink: /HelixMC/
repo: DasLab/HelixMC
title: "HelixMC"
description: "<u>M</u>onte-<u>C</u>arlo Simulation of DNA/RNA <u>Helices</u>"
author: Joseph Yesselman
---

# HelixMC

**HelixMC** is a software package for Monte-Carlo (MC) simulations of DNA/RNA helices using the base-pair level model. It provides a powerful tool to understand the flexibility of DNA/RNA helices through numerical simulations.

<hr/>
## Dependencies 

* A working C/C++ compiler. Here we used `gcc` (4.6.3)

* Python (2.7.3) with packages:

```js
numpy >= 1.6.1
matplotlib >= 1.1.0
```
	
<hr/>
## Installation

The easiest way to install is to use `pip`:

```bash
pip install helixmc
```

Alternatively, one can download the source code from the latest GitHub
repository. Simply run:

```bash
git clone https://github.com/DasLab/HelixMC.git
```

After this, you can instal **HelixMC** using `setup.py`::

```bash
python setup.py build
sudo python setup.py install
```

Instead of installing using `setup.py`, you can just add your **HelixMC** folder into the system's `$PATH` and `$PYTHONPATH`. In bash this can be done by adding the following lines to your `~/.bashrc`:

```bash
export PATH=$PATH:/path/to/HelixMC/
export PYTHONPATH=$PYTHONPATH:/path/to/HelixMC/
```

Then build the Cython extension. Under the `helixmc/` folder, run::

```bash
python _cython_build.py build_ext --inplace
```

Note that this requires you to have Cython installed. Otherwise you can choose to build the c source file, then you do not need Cython:

```bash
python _c_build.py build_ext --inplace
```

Now you should be all set. To test the install, simply run::

```
helixmc-run --help
```

<hr/>
## Documentation

* #### *Python* Documentation is available at: [**http://helixmc.readthedocs.io/**](http://helixmc.readthedocs.io/).

<hr/>
## License

Copyright &copy; of **HelixMC** _Source Code_ is described in [LICENSE.md](https://github.com/DasLab/HelixMC/blob/master/LICENSE.md).

<hr/>
## Related Packages

* [**HiTRACE**](https://ribokit.github.io/HiTRACE/)

<hr/>
Developed by **Das lab**, _Leland Stanford Junior University_.

