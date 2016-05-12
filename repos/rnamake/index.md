---
permalink: /RNAMake/
title: RNAMake
author: Joseph Yesselman
---

# <samp>RNAMake</samp>

**RNAMake** is a toolkit for designing and optimizing RNA 3D structure. It allows the alignment
 between RNA motifs. These motif are small modular peices of RNA that are believed to fold
 independently, thus attaching them together with helix flanking both sides allows users of
 RNAMake to build large segments of RNA with a high success rate of forming the predicted
 structure in vitro.

[![Aligning Motifs with RNAMake](/repos/rnamake/res/rnamake_aligning.png "Aligning Motifs with RNAMake"){: .full}](/repos/rnamake/res/rnamake_aligning.png)
{: .center}



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
export RNAMake=<RNAMake Path>
export PATH=$PATH:<RNAMake Path>
export PYTHONPATH=$PYTHONPATH:<RNAMake Path>
```

Afterwards make sure to source your bashrc file.

```bash
source ~/.bashrc
```

To make sure everything is working run the first example module

```bash
python <RNAMake Path>/examples/example_motif.py
```

## Compiling C++ Programs (Optional)

An additional optional step is to compile the c++ verision of RNAMake. All the functionality
is redundant but it is significantly faster. Performing large design jobs, its recommended to 
use the C++ programs instead of python.

```bash
cd <RNAMake Path>/rnamake/lib/RNAMake/cmake/build
python make_project.py
cmake -G Ninja
ninja
```

To test run:

```bash
python run_unittests.py
```

This will run all the unittests for the c++ code. This may take a few minutes but will ensure
everything is working properly.


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

