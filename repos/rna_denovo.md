---
permalink: /RNAdenovo/
level: 2
title: "RNA de novo"
description: "3D <u>de novo</u> Models of <u>RNA</u>"
author: Kalli Kappel
---

# RNA _de novo_

**RNA _de novo_** is a Rosetta application for making 3D models of RNA using the Fragment Assembly of RNA with Full Atom Refinement (FARFAR) method.

<hr/>
## Installation

To run **RNA _de novo_**, Rosetta must be installed:

- Request a license and download the software at [**rosettacommons**](https://www.rosettacommons.org/software/license-and-download).

- See the Rosetta installation documentation at [**rosettacommons**](https://www.rosettacommons.org/docs/latest/getting_started/Getting-Started).

- Once Rosetta is installed, rna_denovo can be run from the command line, e.g.:

```bash
rna_denovo -fasta my_rna_sequence.fasta -nstruct 100 -minimize_rna -out::file::silent my_rna_structures.out
```

- The helper script rna_denovo_setup.py, also found within Rosetta, may be useful in setting up rna_denovo runs, see documentation at [**rosettacommons**](https://www.rosettacommons.org/docs/latest/application_documentation/rna/rna-denovo-setup).

<hr/>
## Documentation

* Documentation is available at: [**rosettacommons**](www.rosettacommons.org/docs/latest/application_documentation/rna/rna-denovo/).

<hr/>
## License

Copyright &copy; of **RNA _de novo_** _Source Code_ is described in [**license-and-download**](https://www.rosettacommons.org/software/license-and-download).

<hr/>
## References

>Sripakdeevong, P., Kladwang, W., and Das, R. (**2011**)<br/>
>**An enumerative stepwise ansatz enables atomic-accuracy RNA loop modeling**{: style="color:#3399cc"}<br/>
>*Proceedings of the National Academy of Sciences U.S.A.* **108 (51)**: 20573 - 20578. | [Paper](https://daslab.stanford.edu/site_data/pub_pdf/2012_Sripakdeevong_PNAS.pdf) | [Link](http://www.pnas.org/content/108/51/20573)

>Das, R., Karanicolas, J., and Baker, D. (**2010**)<br/>
>**Atomic accuracy in predicting and designing noncanonical RNA structure**{: style="color:#3399cc"}<br/>
>*Nature Methods* **7**: 291 - 294. | [Paper](https://daslab.stanford.edu/site_data/pub_pdf/2010_Das_NatMeth.pdf) | [Link](http://www.nature.com/nmeth/journal/v7/n4/abs/nmeth.1433.html)

>Das, R. and Baker, D. (**2007**)<br/>
>**Automated de novo prediction of native-like RNA tertiary structures**{: style="color:#3399cc"}<br/>
>*Proceedings of the National Academy of Sciences U.S.A.* **104 (37)**: 14664 - 14669. | [Paper](https://daslab.stanford.edu/site_data/pub_pdf/2007_Das_PNAS.pdf) | [Link](http://www.pnas.org/content/104/37/14664.long)

>Das, R., Kudaravalli, M., Jonikas, M., Laederach, A., Fong, R., Schwans, J.P., Baker, D., Piccirilli, J.A., Altman, R.B., and Herschlag, D. (**2008**)<br/>
>**Structural inference of native and partially folded RNA by high throughput contact mapping**{: style="color:#3399cc"}<br/>
>*Proceedings of the National Academy of Sciences U.S.A.* **105 (11)**: 4144 - 4149. | [Paper](https://daslab.stanford.edu/site_data/pub_pdf/2008_Das_PNAS.pdf) | [Link](http://www.pnas.org/content/105/11/4144.long)

<hr/>
## Related Packages

* [**Stepwise**](/Stepwise/)
* [**RNAdesign**](/RNAdesign/)
* [**ERRASER**](/ERRASER/)
* [**RNAMake**](/RNAMake/)
* [**RiboVis**](/RiboVis/)

<hr/>
Developed by **Rosetta Commons**.

README by [**Kalli Kappel**](https://github.com/kkappel1), *May 2016*.

