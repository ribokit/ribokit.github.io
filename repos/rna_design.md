---
permalink: /RNADesign/
---

# <samp>rna_design</samp>

**rna_design** is a Rosetta application for redesigning the sequence of a given RNA structure. This method can be used to predict the primary sequence preferences of RNA structures and suggest mutations to stabilize a particular 3D motif.

<hr/>
## Installation

There is a server for this application at [**http://rnaredesign.stanford.edu/**](http://rnaredesign.stanford.edu/).

Alternatively, rna_design is available as part of Rosetta. To download and install Rosetta:

- Request a license and download the software [**here**](https://www.rosettacommons.org/software/license-and-download)

- See the Rosetta installation documentation [**here**](https://www.rosettacommons.org/docs/latest/getting_started/Getting-Started)

- Once Rosetta is installed, rna_design can be run from the command line, e.g.:

```bash
rna_design -s chunk001_uucg_RNA.pdb   -nstruct 3  -ex1:level 4 -dump -score:weights farna/rna_hires.wts
```

<hr/>
## Documentation

* Documentation is available at: [**https://www.rosettacommons.org/docs/latest/application_documentation/rna/rna-design**](https://www.rosettacommons.org/docs/latest/application_documentation/rna/rna-design).

* Documentation for the server can be found [**here**](http://rnaredesign.stanford.edu/res/html/Tutorial.html)

<hr/>
## License

Copyright &copy; of **rna_design** _Source Code_ is described in [**license-and-download**](https://www.rosettacommons.org/software/license-and-download)

<hr/>
## References

Yesselman, J.D., and Das, R. (2015) "RNA-Redesign: A web server for fixed-backbone 3D design of RNA." Nucleic Acid Research 43 (W1): W498 - W501. [**Paper**](https://daslab.stanford.edu/site_data/pub_pdf/2015_Yesselman_NAR.pdf) [**Link**](http://nar.oxfordjournals.org/content/43/W1/W498) [**Server**](http://rnaredesign.stanford.edu/)

Das, R., Karanicolas, J., and Baker, D. (2010), "Atomic accuracy in predicting and designing noncanonical RNA structure". Nature Methods 7:291-294. [**Paper**](http://web.stanford.edu/~rhiju/DasKaranicolasBaker2010ALL.pdf) [**Link**](http://www.nature.com/nmeth/journal/v7/n4/abs/nmeth.1433.html)

<hr/>
## Related Packages

* [**Stepwise**](http://ribokit.github.io/Stepwise/)
* [**rna_denovo**](http://ribokit.github.io/RNADenovo/)
* [**ERRASER**](http://ribokit.github.io/ERRASER/)
* [**RNAmake**](http://ribokit.github.io/RNAMake/)
* [**RiboVis**](http://ribokit.github.io/RiboVis/)


<hr/>
Developed by **Rosetta Commons**

README by kkappel, *May 2016*.

