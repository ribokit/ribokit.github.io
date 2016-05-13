---
permalink: /Stepwise/
level: 2
title: Stepwise
description: "<u>Stepwise</u> Monte Carlo for Modeling"
author: Kalli Kappel
---

# Stepwise

**Stepwise** is a Rosetta application for generating highly accurate de novo 3D models of small RNA and protein motifs. It can be used for both structure prediction and design. 

<hr/>
## Installation

To run **Stepwise**, Rosetta must be installed:

- Request a license and download the software at [**rosettacommons**](https://www.rosettacommons.org/software/license-and-download).

- See the Rosetta installation documentation at [**rosettacommons**](https://www.rosettacommons.org/docs/latest/getting_started/Getting-Started).

- Once Rosetta is installed, stepwise can be run from the command line, e.g.:

```bash
stepwise -fasta my_rna_sequence.fasta -s start_helix.pdb  -out:file:silent swm_rebuild.out
```

<hr/>
## Documentation

* Documentation is available at: [**rosettacommons**](https://www.rosettacommons.org/docs/latest/application_documentation/stepwise/stepwise_monte_carlo/stepwise).

<hr/>
## License

Copyright &copy; of **Stepwise** _Source Code_ is described in [**license-and-download**](https://www.rosettacommons.org/software/license-and-download).

<hr/>
## References

Stepwise monte carlo is unpublished as of May 2016. References for the stepwise assembly method:

> Das, R. (**2013**)<br/>
>**Atomic-accuracy prediction of protein loop structures enabled by an RNA-inspired ansatz**{: style="color:#3399cc"}<br/>
>*PLoS ONE* **8 (10)**: e74830. | [Paper](https://daslab.stanford.edu/site_data/pub_pdf/2013_Das_PLOSOne.pdf) | [Link](http://journals.plos.org/plosone/article?id=10.1371/journal.pone.0074830)

>Sripakdeevong, P., Kladwang, W., and Das, R. (**2011**)<br/>
>**An enumerative stepwise ansatz enables atomic-accuracy RNA loop modeling**{: style="color:#3399cc"}<br/>
>*Proceedings of the National Academy of Sciences U.S.A.* **108 (51)**: 20573 - 20578. | [Paper](https://daslab.stanford.edu/site_data/pub_pdf/2012_Sripakdeevong_PNAS.pdf) | [Link](http://www.pnas.org/content/108/51/20573)

<hr/>
## Related Packages

* [**RNAdesign**](/RNAdesign/)
* [**RNA _de novo_**](/RNAdenovo/)
* [**ERRASER**](/ERRASER/)
* [**RNAMake**](/RNAMake/)
* [**RiboVis**](/RiboVis/)

<hr/>
Developed by **Rosetta Commons**.

README by [**Kalli Kappel**](https://github.com/kkappel1), *May 2016*.

