---
layout: default
permalink: /primerize/
root: /primerize/

title: Primerize
description: "PCR Assembly Primer Design"
repo: DasLab/Primerize
author: Siqi Tian
---


# Primerize (NA_Thermo)

[![Primerize Logo](https://primerize.stanford.edu/site_media/images/logo_primerize.png "Primerize Logo"){: .half}](https://primerize.stanford.edu/site_media/images/logo_primerize.png)
{: .center}

**Primerize** (previously named **NA_thermo**), is an archive of *Python* and *MATLAB* scripts for primer design and nucleic acid thermodynamic scripts developed by the [Das Lab](https://daslab.stanford.edu/) at Stanford University for high-throughput RNA synthesis and design.

The algorithm designs *forward* (sense strand) and *reverse* (anti-sense strand) primers that minimize the total length, and therefore the total synthesis cost, of the oligonucleotides. Although developed independently, **Primerize** is a special case of the general ‘*Gapped Oligo Design*’ algorithm, optimizing the mispriming score and sequence span instead of *T<sub>m<sub>*.

An online user-friendly GUI is available as the [**Primerize Server**](https://primerize.stanford.edu/).

<hr/>
## Installation

To install **Primerize**, simply:

```bash
cd path/to/primerize/repo
python setup.py install
```

For system-wide installation, you must have permissions and use with `sudo`.

**Primerize** requires the following *Python* packages as dependencies, all of which can be installed through [`pip`](https://pip.pypa.io/).

```js
llvmlite == 0.8.0
matplotlib >= 1.5.0
numba == 0.23.1
numpy >= 1.10.1
xlwt >= 1.0.0
```

- Note that the [`numba`](http://numba.pydata.org/) is used for its [`@jit`](http://numba.pydata.org/numba-doc/0.23.1/user/jit.html) decorator on loop optimization. `numba` requires [`llvm`](http://llvm.org/), which can be installed through [`apt-get`](https://help.ubuntu.com/lts/serverguide/apt-get.html) on *Linux* or [`brew`](http://brew.sh/) on Mac *OSX*. It also requires `llvmlite`, which can be installed through `pip`. 

- The compatibility between `numba`, `llvmlite`, and `llvm` needs to pay special attention to. The above specified `numba` and `llvmlite` versions have been tested to work with `llvm 3.6.2` on *Linux* machines. 

<hr/>
## Usage

For simple Primer Design tasks, follow this example:

```python
import primerize

prm_1d = primerize.Primerize_1D()
job_1d = prm_1d.design('TTCTAATACGACTCACTATAGGCCAAAGGCGUCGAGUAGACGCCAACAACGGAAUUGCGGGAAAGGGGUCAACAGCCGUUCAGUACCAAGUCUCAGGGGAAACUUUGAGAUGGCCUUGCAAAGGGUAUGGUAAUAAGCUGACGGACAUGGUCCUAACCACGCAGCCAAGUCCUAAGUCAACAGAUCUUCUGUUGAUAUGGAUGCAGUUCAAAACCAAACCGUCAGCGAGUAGCUGACAAAAAGAAACAACAACAACAAC', MIN_TM=60.0, NUM_PRIMERS=None, MIN_LENGTH=15, MAX_LENGTH=60, prefix='P4P6_2HP')
if job_1d.is_success:
    print job_1d

prm_2d = primerize.Primerize_2D()
job_2d = prm_2d.design(job_1d, offset=-51, which_muts=range(102, 261 + 1), which_lib=1)
if job_2d.is_success:
    print job_2d
    job_2d.save()

prm_3d = primerize.Primerize_3D()
job_3d = prm_3d.design(job_1d, offset=-51, structures=['...........................((((((.....))))))...........((((((...((((((.....(((.((((.(((..(((((((((....)))))))))..((.......))....)))......)))))))....))))))..)).))))((...((((...(((((((((...)))))))))..))))...)).............((((((.....))))))......................'], N_mutations=1, which_lib=1, is_single=True, is_fillWT=True)
if job_3d.is_success:
    print job_3d
    job_3d.save()
```

For advanced users, the returned `Design_Single` and `Design_Plate` result classes offer methods for `get()`, `save()` and `echo()`:

```python
MIN_TM = job_1d.get('MIN_TM')
print job_1d.get('MISPRIME')
print job_1d.echo('WARNING')
if job_1d.is_success:
    job_1d.save(path='result/', name='Primer')

LIB = job_2d.get('which_lib')
N_PRIMER = job_2d.get('N_PRIMER')
print job_2d.get('CONSTRUCT')
if job_2d.is_success:
    print job_2d.echo('region')
    job_2d.save('assembly', path='result/', name='Lib')

N_PLATE = job_3d.get('N_PLATE')
if job_3d.is_success:
    print job_3d.echo('plate')
    print repr(job_3d)
```

Besides `design()`, the `Primerize_1D`, `Primerize_2D`, and `Primerize_3D` worker classes offer methods for `get()`, `set()`, and `reset()`:

```python
COL_SIZE = prm_1d.get('COL_SIZE')
prm_1d.set('MIN_LENGTH', 30)
prm_1d.reset()
```

There are also `Assembly`, `Mutation`, `Construct_List`, and `Plate_96Well` helper classes. For more details, please refer to the **Documentation**.

<br/>

> MATLAB Code (Deprecated)

Instructions on *MATLAB* usage is available at old [README.md](https://github.com/DasLab/Primerize/blob/master/MATLAB/README.md). Please note that *MATLAB* code is no longer actively under development or fully maintained.

<hr/>
## Documentation

Documentation is available at [https://primerize.stanford.edu/docs/](https://primerize.stanford.edu/docs/).

<hr/>
## License

Copyright &copy; of **Primerize** _Source Code_ is described in [LICENSE.md](https://github.com/DasLab/Primerize/blob/master/LICENSE.md).

<hr/>
## Reference

>Tian, S., *et al.* (**2015**)<br/>
>[Primerize: Automated Primer Assembly for Transcribing Interesting RNAs.](http://nar.oxfordjournals.org/content/43/W1/W522.full)<br/>
>*Nucleic Acid Research* **43 (W1)**: W522-W526.


>Thachuk, C., and Condon, A. (**2007**)<br/>
>[On the Design of Oligos for Gene Synthesis.](http://ieeexplore.ieee.org/xpls/abs_all.jsp?arnumber=4375554)<br/>
>*Proceedings of the 7th IEEE International Conference on Bioinformatics and Bioengineering* **2007**: 123-130.

<hr/>
Developed by **Das lab**, _Leland Stanford Junior University_.

README by [**t47**](http://t47.io/), *January 2016*.
