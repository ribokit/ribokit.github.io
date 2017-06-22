---
permalink: /Biers/install/
level: 2
next: dependency/
---

# Installation

**Biers** requires *MATLAB* installation. Unlike **HiTRACE**, it has no restrictions on versions.

To install **Biers**, simply:

- From GitHub or [**RMDB**](https://rmdb.stanford.edu/tools/), download the zip or tar file of the repository and unpack; or 

```bash
git clone https://github.com/DasLab/Biers.git
```

- In *MATLAB*, go to "**Set Path**". Then "**Add with Subfolders**" of the target `path/to/Biers/Scripts/`.

- Make a copy of `Scripts/get_exe_dir.m.example` and `Scripts/get_varna.m.example` and rename to `Scripts/get_exe_dir.m` and `Scripts/get_varna.m`.

- Edit the new `Scripts/get_exe_dir.m` and `Scripts/get_varna.m` following the instructions in these files.

<hr/>

In order to get **Biers** running with RNAstructure in _MATLAB_, **you have to launch _MATLAB_ from terminal every time**{: style="color:#ff5c2b;"}. 

> This is due to the inheritance of `DATAPATH` environment variable. To launch _MATLAB_ from terminal, run:

```bash
/Applications/MATLAB_R20XXa.app/bin/matlab
```

> Replace your _MATLAB_ version in the command.

We recommend creating an alias to save us some time in the future. Edit the `~/.bash_profile`, add a line:

```bash
alias matlab=/Applications/MATLAB_R20XXa.app/bin/matlab
```

Again, restart your terminal to take effect. Now you only need to type `matlab` to launch _MATLAB_!

<hr/>

#### **A complete guide on the whole setup**{: style="color:#ff5c2b;"}, including `gcc`, RNAstructure, VARNA, is described [here](../dependency/).

