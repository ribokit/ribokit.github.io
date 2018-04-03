---
permalink: /Biers/install/
level: 2
next: ../dependency/
---

# Installation

**Biers** requires *MATLAB* installation. Unlike **HiTRACE**, it has no restrictions on versions.

To install **Biers**, simply:

- From GitHub, download the zip or tar file of the repository and unpack; or 

```bash
git clone https://github.com/ribokit/Biers.git
```

- In *MATLAB*, go to "**Set Path**". Then "**Add with Subfolders**" of the target `path/to/Biers/Scripts/`.

- Make sure you have set in your environment the variables `DATAPATH` (for RNAstructure) and `VARNA` (for VARNA). If you are on a Mac or Linux, put lines like the following in your `.bash_profile`:

```bash
export DATAPATH=$HOME/src/RNAstructure/data_tables/
export VARNA=$HOME/src/VARNA.jar
```
See also the [Biers Dependencies](/Biers/dependency/) page.


- Makes sure that you start MATLAB from terminal, as follows.

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

#### **A complete guide on the whole setup**{: style="color:#ff5c2b;"}, including **gcc**, RNAstructure, VARNA, is described at the [Biers dependencies page](../dependency/).

<hr/>

* Previous: [Biers](/Biers/)
* Next: [Dependencies](/Biers/dependency/)

<hr/>
