---
permalink: /RDATKit/install/
level: 2
next: docs/
---

# Installation

## MATLAB

- From GitHub or [**RMDB**](https://rmdb.stanford.edu/tools/), download the zip or tar file of the repository and unpack; or 

```bash
git clone https://github.com/hitrace/RDATKit.git
```

- In *MATLAB*, go to "**Set Path**". Then "**Add with Subfolders**" of the target `path/to/RDATKit/MATLAB/`.

<hr/>
## Python

To install **RDATKit**, simply:

- Copy `path.py.example` into `rdatkit/path.py`. Edit `rdatkit/path.py` following the instructions in the file to point to local installations of [RNAstructure](http://rna.urmc.rochester.edu/RNAstructure.html), [ViennaRNA](https://www.tbi.univie.ac.at/RNA/), and [VARNA](http://varna.lri.fr/).

- Run:

```bash
cd path/to/RDATKit/
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