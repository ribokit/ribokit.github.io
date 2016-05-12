---
permalink: /RnaDenovo/
---

# <samp>rna_denovo</samp>

**rna_denovo** is a Rosetta application for making 3D models of RNA using the Fragment Assembly of RNA with Full Atom Refinement (FARFAR) method.

<hr/>
## Installation

To run rna_denovo, Rosetta must be installed:
* Request a license and download the software [**here**](https://www.rosettacommons.org/software/license-and-download)
* See the Rosetta installation documentation [**here**](https://www.rosettacommons.org/docs/latest/getting_started/Getting-Started)
* Once Rosetta is installed, rna_denovo can be run from the command line, e.g.:
```bash
rna_denovo -fasta my_rna_sequence.fasta -nstruct 100 -minimize_rna -out::file::silent my_rna_structures.out
```
* The helper script rna_denovo_setup.py, also found within Rosetta, may be useful in setting up rna_denovo runs, see documentation [**here**](https://www.rosettacommons.org/docs/latest/application_documentation/rna/rna-denovo-setup)

<hr/>
## Documentation

* Documentation is available at: [**https://www.rosettacommons.org/docs/latest/application_documentation/rna/rna-denovo/**](www.rosettacommons.org/docs/latest/application_documentation/rna/rna-denovo/).

<hr/>
## License

Copyright &copy; of **rna_denovo** _Source Code_ is described in [**license-and-download**](https://www.rosettacommons.org/software/license-and-download)

<hr/>
## References
Das, R. and Baker, D. (2007), "Automated de novo prediction of native-like RNA tertiary structures", PNAS 104: 14664-14669. [for fragment assembly]. [**Paper**](http://web.stanford.edu/~rhiju/Das_Baker_PNAS_2007.pdf)[**Link**](http://www.pnas.org/content/104/37/14664.long)

Das, R., Kudaravalli, M., et al. (2007) "Structural inference of native and partially folded RNA by high throughput contact mapping", PNAS, 4144-4149. [for modeling large RNAs with constraints]. [**Paper**](http://web.stanford.edu/~rhiju/das_MOHCA08.pdf)[**Link**](http://www.pnas.org/content/105/11/4144.long)

Das, R., Karanicolas, J., and Baker, D. (2010), "Atomic accuracy in predicting and designing noncanonical RNA structure". Nature Methods 7:291-294. [for high resolution refinement]. [**Paper**](http://web.stanford.edu/~rhiju/DasKaranicolasBaker2010ALL.pdf)[**Link**](http://www.nature.com/nmeth/journal/v7/n4/abs/nmeth.1433.html)

Sripakdeevong, P., Kladwang, W., and Das, R. (2011) "An enumerative stepwise ansatz enables atomic-accuracy RNA loop modeling", PNAS 108:20573-20578. [for loop modeling]. [**Paper**](http://web.stanford.edu/~rhiju/Sripakdeevong_StepwiseAnsatz_2011.pdf)[**Link**](http://www.pnas.org/content/108/51/20573)

<hr/>
## Related Packages

* stepwise
* rna_design
* ERRASER
* RNAmake
* RiboVis


<hr/>
Developed by **Rosetta Commons**

README by kkappel, *May 2016*.

