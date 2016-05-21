---
permalink: /RNAdesign/
level: 2
title: "RNA Design"
description: "<u>RNA</u> <u>Design</u> for Fixed-Backbone Optimization"
author: Kalli Kappel
---

# RNAdesign

**RNAdesign** is a Rosetta application for redesigning the sequence of a given RNA structure. This method can be used to predict the primary sequence preferences of RNA structures and suggest mutations to stabilize a particular 3D motif.

<hr/>
## Installation

There is a server for this application at [**RNA Redesign**](http://rnaredesign.stanford.edu/).

Alternatively, rna_design is available as part of Rosetta. To download and install Rosetta:

- Request a license and download the software at [**rosettacommons**](https://www.rosettacommons.org/software/license-and-download).

- See the Rosetta installation documentation at [**rosettacommons**](https://www.rosettacommons.org/docs/latest/getting_started/Getting-Started).

- Once Rosetta is installed, **RNAdesign** can be run from the command line, e.g.:

```bash
rna_design -s chunk001_uucg_RNA.pdb   -nstruct 3  -ex1:level 4 -dump -score:weights farna/rna_hires.wts
```

<hr/>
## Documentation

* Documentation is available at: [**rosettacommons**](https://www.rosettacommons.org/docs/latest/application_documentation/rna/rna-design).

* Documentation for the server can be found at [**RNA Redesign**](http://rnaredesign.stanford.edu/res/html/Tutorial.html).

<hr/>
## License

Copyright &copy; of **RNAdesign** _Source Code_ is described in [**license-and-download**](https://www.rosettacommons.org/software/license-and-download).

<hr/>
## References

>Yesselman, J.D., and Das, R. (**2015**)<br/>
>**RNA-Redesign: A web server for fixed-backbone 3D design of RNA**{: style="color:#3399cc"}<br/>
>*Nucleic Acid Research* **43 (W1)**: W498 - W501. | [Paper](https://daslab.stanford.edu/site_data/pub_pdf/2015_Yesselman_NAR.pdf) | [Link](http://nar.oxfordjournals.org/content/43/W1/W498) | [Server](http://rnaredesign.stanford.edu/)

>Das, R., Karanicolas, J., and Baker, D. (**2010**)<br/>
>**Atomic accuracy in predicting and designing noncanonical RNA structure**{: style="color:#3399cc"}<br/>
>*Nature Methods* **7**: 291 - 294. | [Paper](https://daslab.stanford.edu/site_data/pub_pdf/2010_Das_NatMeth.pdf) | [Link](http://www.nature.com/nmeth/journal/v7/n4/abs/nmeth.1433.html)

<hr/>
## Related Packages

* [**Stepwise**](/Stepwise/)
* [**RNA _de novo_**](/RNAdenovo/)
* [**ERRASER**](/ERRASER/)
* [**RNAmake**](/RNAMake/)
* [**RiboVis**](/RiboVis/)

<hr/>
## Workflows

* [I want to design a new RNA molecule](/workflow/design/)

<hr/>
Developed by **Rosetta Commons**.

README by [**Kalli Kappel**](https://github.com/kkappel1), *May 2016*.

