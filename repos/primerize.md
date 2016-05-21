---
permalink: /Primerize/
repo: DasLab/Primerize
title: "Primerize"
description: "PCR Assembly Primer Design"
author: Siqi Tian
---

# Primerize

**Primerize** (previously named **NA_thermo**), is an archive of *Python* and *MATLAB* scripts for primer design and nucleic acid thermodynamic scripts developed by the [Das Lab](https://daslab.stanford.edu/) at Stanford University for high-throughput RNA synthesis and design.

The algorithm designs *forward* (sense strand) and *reverse* (anti-sense strand) primers that minimize the total length, and therefore the total synthesis cost, of the oligonucleotides. Although developed independently, **Primerize** is a special case of the general ‘*Gapped Oligo Design*’ algorithm, optimizing the mispriming score and sequence span instead of *T<sub>m<sub>*.

An online user-friendly GUI is available as the [**Primerize Server**](https://primerize.stanford.edu/).

<hr/>
## Installation

**Primerize** can be downloaded for non-commercial use at the [**Primerize Server**](https://primerize.stanford.edu/license/). Commercial users, please [**contact us**](https://primerize.stanford.edu/about/#contact).

For instructions, see [daslab.github.io](https://daslab.github.io/Primerize/install).

<hr/>
## Documentation

* #### *Python* Documentation is available [**here**](https://daslab.github.io/Primerize/).

* #### *MATLAB* Documentation is available [**here**](https://daslab.github.io/Primerize/matlab).

<hr/>
## License

Copyright &copy; of **Primerize** _Source Code_ is described in [LICENSE.md](https://github.com/DasLab/Primerize/blob/master/LICENSE.md).

<hr/>
## Reference

>Tian, S., *et al.* (**2015**)<br/>
>**Primerize: Automated Primer Assembly for Transcribing Interesting RNAs**{: style="color:#3399cc"}<br/>
>*Nucleic Acid Research* **43 (W1)**: W522-W526. | [Paper](https://daslab.stanford.edu/site_data/pub_pdf/2015_Tian_NAR.pdf) | [Link](http://nar.oxfordjournals.org/content/43/W1/W522.full)


>Thachuk, C., and Condon, A. (**2007**)<br/>
>[**On the Design of Oligos for Gene Synthesis**](http://ieeexplore.ieee.org/xpls/abs_all.jsp?arnumber=4375554)<br/>
>*Proceedings of the 7th IEEE International Conference on Bioinformatics and Bioengineering* **2007**: 123-130.

<hr/>
## Workflows

* [I have just discovered an RNA molecule](/workflows/from_scratch/)
* [I want to learn an RNA’s secondary structure](/workflows/2D_modeling/)
* [I want to test an RNA secondary structure model](/workflows/mutation_rescue/)
* [I think my RNA has interesting alternative states](/workflows/alternative_states/)

<hr/>
Developed by **Das lab**, _Leland Stanford Junior University_.

README by [**t47**](http://t47.io/), *May 2016*.

