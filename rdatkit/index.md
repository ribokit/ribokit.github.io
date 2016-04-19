---
layout: default
permalink: /rdatkit/
root: /rdatkit/

title: RDATKit
description: "<u>R</u>NA <u>Dat</u>aset Tool<u>Kit</u>"
repo: hitrace/rdatkit
author: Siqi Tian
---


# RDATKit

**RDATkit** is a set of tools for parsing, analyzing, and publishing data of RNA chemical footprinting assays. It allows researchers to share their data using community standard formats, and helps them publish their results on indexable and shareable databases.

**RDATKit** is a package provides a set of *Python* and *MATLAB* scripts that facilitate saving and loading data to and from files with [**RDAT**](https://rmdb.stanford.edu/deposit/specs/) format. It also supports the [**ISATAB**](http://ribosnitch.bio.unc.edu/snrnasm/) file format.

<hr/>
## Installation

#### MATLAB

- Download the zip or tar file of the repository and unpack; or 

```bash
git clone https://github.com/hitrace/rdatkit.git
```

- In *MATLAB*, go to "**Set Path**". Then "**Add with Subfolders**" of the target `path/to/rdatkit/MATLAB/`.

#### Python

To install **RDATKit**, simply:

- Copy `path.py.example` into `rdatkit/path.py`. Edit `rdatkit/path.py` following the instructions in the file to point to local installations of [RNAstructure](http://rna.urmc.rochester.edu/RNAstructure.html), [ViennaRNA](https://www.tbi.univie.ac.at/RNA/), and [VARNA](http://varna.lri.fr/).

- Run:

```bash
cd path/to/rdatkit/repo
python setup.py install
```

For system-wide installation, you must have permissions and use with `sudo`.

**RDATKit** requires the following *Python* packages as dependencies, all of which can be installed through [`pip`](https://pip.pypa.io/).

```js
numpy >= 1.8.0
scipy >= 0.13.0
xlrd >= 0.9.2
xlwt >= 1.0.0
```

<hr/>
## Documentation

* #### *MATLAB* Tutorial is available [**here**](/hitrace/tutorial/step_9/).

* #### *Python* Documentation is available at: [**docs/**](docs/).

<hr/>
## License

Copyright &copy; of **RDATKit** _Source Code_ is described in [LICENSE.md](https://github.com/hitrace/rdatkit/blob/master/LICENSE.md).

<hr/>
## Related Packages

* ### [**HiTRACE**](/hitrace/)

* ### [**Biers**](/biers/)

* [**MAPSeeker**](/mapseeker/)

<hr/>
Developed by **Das lab**, _Leland Stanford Junior University_.

README by [**t47**](http://t47.io/), *March 2016*.
