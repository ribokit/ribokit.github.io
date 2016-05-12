---
permalink: /ERRASER/
---

# <samp>ERRASER</samp>

[![Example Image](https://daslab.stanford.edu/site_data/pub_img/2013_Chou_NatMeth.jpg "Example Image")](https://daslab.stanford.edu/site_data/pub_img/2013_Chou_NatMeth.jpg)

**ERRASER** (Enumerative Real-space Refinment ASsisted by Electron-density under Rosetta) is an application for improving RNA crystal structures based on Rosetta and Phenix. For a quick preview:

| Function | Description |
| --- | --- |
| `erraser.py` | Run ERRASER. |
| `erraser-single-res.py` | Run ERRASER on single residues. |
| `erraser-analysis.py` | Analyze ERRASER run. |

And more! ...

<hr/>
## Installation

To run ERRASER, Rosetta and Phenix must be installed.

To download and install Rosetta:

- Request a license and download the software [**here**](https://www.rosettacommons.org/software/license-and-download)

- See the Rosetta installation documentation [**here**](https://www.rosettacommons.org/docs/latest/getting_started/Getting-Started)

To download and install Phenix:

- Download the software [**here**](http://www.phenix-online.org/). Phenix is free for academic users.

Finish setup:

- Ensure you have correctly setup Phenix. As a check, make sure the following command works:
```bash
phenix.rna_validate
```

- Make sure you have a Python v2.7 (`python --version`). If not, go to the `rosetta/tools/ERRASER/` folder and run:
```bash
./convert_to_phenix.python
```
This will change the default python used by the code to phenix-built-in python, instead of using system python.

- Set an environment variable `$ROSETTA` to the path to Rosetta. If you use bash, append the following lines to `~/.bashrc`:
```bash
ROSETTA=/path/to/Rosetta/; export ROSETTA;
```
Also add the ERRASER script folder to your `$PATH`. Here is a bash example:
```bash
PATH=$PATH:/path/to/Rosetta/tools/ERRASER/
```

Once Rosetta and Phenix have been installed, ERRASER can be run from the command line, e.g.:

```bash
erraser.py -pdb 1U8D_cut.pdb -map 1U8D_cell.ccp4 -map_reso 1.95 -fixed_res A33-37 A61 A65 
```


<hr/>
## Documentation

* *Rosetta* Documentation is available, [**here**](https://www.rosettacommons.org/docs/latest/application_documentation/rna/erraser).
* *Phenix* Documentation is available, [**here**](https://www.phenix-online.org/documentation/reference/erraser.html).

<hr/>
## License

Copyright &copy; of **ERRASER** _Source Code_ is described in [license-and-download](https://www.rosettacommons.org/software/license-and-download).

<hr/>
## References

>Chou, F.-C., Sripakdeevong, P., Dibrov, S.M, Hermann, T., and Das, R. (**2013**)<br/>
>"Correcting pervasive errors in RNA crystallography through enumerative structure prediction"<br/>
>*Nature Methods* **10**: 74 - 76. [For ERRASER].<br/> 
>[**Paper**](https://daslab.stanford.edu/site_data/pub_pdf/2013_Chou_NatMeth.pdf) [**Link**](http://www.nature.com/nmeth/journal/v10/n1/full/nmeth.2262.html) [**ERRASER Server**](http://rosie.rosettacommons.org/erraser/)

>Sripakdeevong, P., Kladwang, W., and Das, R. (**2012**)<br/>
>"An enumerative stepwise ansatz enables atomic-accuracy RNA loop modeling"<br/>
>*Proceedings of the National Academy of Sciences U.S.A.* **108 (51)** : 20573 - 20578. [For stepwise assembly (SWA) algorithm]<br/>  
>[**Paper**](https://daslab.stanford.edu/site_data/pub_pdf/2012_Sripakdeevong_PNAS.pdf) [**Link**](http://www.pnas.org/content/108/51/20573)

<hr/>
## Related Packages

* [**Rosetta rna_denovo**](/RNADenovo/)
* [**Rosetta stepwise**](/Stepwise/)
* [**Rosetta rna_design**](/RNADesign/)
* [**RNAMake**](/RNAMake/)
* [**RiboVis**](/RiboVis/)


<hr/>
Developed by **Das lab**, _Leland Stanford Junior University_.

README by [**calebgeniesse**](https://github.com/calebgeniesse), *May 2016*.
