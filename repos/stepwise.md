---
permalink: /Stepwise/
---

# <samp>Stepwise</samp>

**Stepwise** is a Rosetta application for generating highly accurate de novo 3D models of small RNA and protein motifs. It can be used for both structure prediction and design. 

<hr/>
## Installation

To run stepwise, Rosetta must be installed:

- Request a license and download the software [**here**](https://www.rosettacommons.org/software/license-and-download)

- See the Rosetta installation documentation [**here**](https://www.rosettacommons.org/docs/latest/getting_started/Getting-Started)

- Once Rosetta is installed, stepwise can be run from the command line, e.g.:

```bash
stepwise -fasta my_rna_sequence.fasta -s start_helix.pdb  -out:file:silent swm_rebuild.out
```

<hr/>
## Documentation

* Documentation is available at: [**https://www.rosettacommons.org/docs/latest/application_documentation/stepwise/stepwise_monte_carlo/stepwise**](https://www.rosettacommons.org/docs/latest/application_documentation/stepwise/stepwise_monte_carlo/stepwise)

<hr/>
## License

Copyright &copy; of **stepwise** _Source Code_ is described in [**license-and-download**](https://www.rosettacommons.org/software/license-and-download)

<hr/>
## References
Stepwise monte carlo is unpublished as of May 2016. References for the stepwise assembly method:

Sripakdeevong, P., Kladwang, W., and Das, R. (2011) "An enumerative stepwise ansatz enables atomic-accuracy RNA loop modeling", PNAS 108:20573-20578. [for loop modeling] [**Paper**](http://web.stanford.edu/~rhiju/Sripakdeevong_StepwiseAnsatz_2011.pdf) [**Link**](http://www.pnas.org/content/108/51/20573)

Das, R. (2013) "Atomic-accuracy prediction of protein loop structures enabled by an RNA-inspired ansatz", PLoS ONE 8(10): e74830. doi:10.1371/journal.pone.0074830 [**Link**](http://journals.plos.org/plosone/article?id=10.1371/journal.pone.0074830)

<hr/>
## Related Packages

* rna_denovo
* rna_design
* ERRASER
* RNAmake
* RiboVis


<hr/>
Developed by **Rosetta Commons**

README by kkappel, *May 2016*.

