---
layout: default
permalink: /biers/
root: /biers/

title: Biers
description: "<u>B</u>est <u>I</u>nference <u>E</u>ngine for <u>R</u>NA <u>S</u>tructure"
repo: daslab/biers
author: Siqi Tian
---


# Biers

**Biers** is a set of *MATLAB* scripts that wrap around the [RNAstructure](http://rna.urmc.rochester.edu/RNAstructure.html) suite of executables to infer secondary structure models guided by chemical mapping data. Features include:

- Secondary structure modeling guided by SHAPE and DMS probing, as well as data from mutate-and-map experiments.

- Secondary structure modeling guided by MOHCA data.

- Calculation of helix-wise confidence values using bootstrapping.

- Plotting utilities using *MATLAB* and [VARNA](http://varna.lri.fr/).

<hr/>
## Installation

To install **Biers**, simply:

- Download the zip or tar file of the repository and unpack; or 

```bash
git clone https://github.com/DasLab/biers.git
```

- In *MATLAB*, go to "**Set Path**". Then "**Add with Subfolders**" of the target `path/to/biers/Scripts/`.

- Copy `Scripts/get_exe_dir.m.example` and `Scripts/get_varna.m.example` into `Scripts/get_exe_dir.m` and `Scripts/get_varna.m`. Edit `Scripts/get_exe_dir.m` and `Scripts/get_varna.m` following the instructions in these files.

<hr/>
## Usage 

### *MATLAB* Tutorial is available for: 

* [Predict Secondary Structure](rnastructure/)

* [Visualize Secondary Structure](varna/)

<hr/>
## License

Copyright &copy; of **Biers** _Source Code_ is described in [LICENSE.md](https://github.com/DasLab/biers/blob/master/LICENSE.md).

<hr/>
## Related Packages

* ### [**HiTRACE**](/hitrace/)

* ### [**MAPSeeker**](/mapseeker/)

* [**RDATKit**](/rdatkit/)

<hr/>
Developed by **Das lab**, _Leland Stanford Junior University_.

README by [**t47**](http://t47.io/), *April 2016*.
