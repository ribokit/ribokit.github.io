---
permalink: /LIFFT/
title: "LIFFT"
description: "<u>LI</u>kelihood-based <u>F</u>its of <u>F</u>olding <u>T</u>ransitions"
---

# LIFFT


LIkelihood-based Fits of Folding Transitions (**LIFFT**) models thermodynamic relationships vs. temperature, ionic, or ligand condition from chemical mapping measurement data. By using a likelihood function, no ad hoc assumptions are necessary for error estimation, normalizaion, or for the choice of residues to fit.


<hr/>
## Installation

To install **LIFFT**, simply:

- From GitHub, download the zip or tar file of the repository and unpack; or 

```bash
git clone https://github.com/ribokit/LIFFT.git
```

-  Add the 'scripts' directory to your MATLAB path: Click 'Set Path', and 'Add with Subfolders...', then select 'scripts'.


<hr/>
## Documentation

* #### Documentation is available in: [**docs/README.md**](docs/README.md).
* #### An example is available in: [**examples/eterna_fit_FMN_binding/**](examples/eterna_fit_FMN_binding/).
* #### To get more detailed documentation, in MATLAB type:
```MATLAB
help lifft
```

<hr/>
## License

Copyright &copy; of **LIFFT** _Source Code_ is described in [LICENSE.md](https://github.com/ribokit/LIFFT/blob/master/LICENSE.md).

## Reference
>For fitting Mg(2+)-dependent folding transitions (incl. Hill fits)<br/>
><br/>
>Frederiksen, J.K., Li, N.S., Das, R., Herschlag, D., and Piccirilli, J.A. (**2012**)<br/>
>Metal-ion rescue revisited: Biochemical detection of site-bound metal ions important for RNA folding<br/>
>*RNA* **18 (6)** : 1123 - 1141. | [Paper](https://daslab.stanford.edu/site_data/pub_pdf/2012_Frederiksen_RNA.pdf)  |  [Link](http://rnajournal.cshlp.org/content/18/6/1123)

>Standard Hill fits to single ligands<br/>
><br/>
>Lee, J., Kladwang, W., Lee, M., Cantu, D., Azizyan, M., Kim, H., Limpaecher, A., Yoon, S., Treuille, A., Das, R., and EteRNA Participants (**2014**)<br/>
>RNA design rules from a massive open laboratory<br/>
>*Proceedings of the National Academy of Sciences U.S.A.* **111 (6)** : 2122 - 2127. |  [Paper](https://daslab.stanford.edu/site_data/pub_pdf/2014_Lee_PNAS.pdf)  |  [Link](http://www.pnas.org/content/111/6/2122)

>For fitting two-ligand binders (e.g., glycine riboswitch)<br/>
><br/>
>Kladwang, W., Chou, F.-C., and Das, R. (**2012**)<br/>
>Automated RNA structure prediction uncovers a kink-turn linker in double glycine riboswitches<br/>
>*Journal of the American Chemical Society* **134 (3)** : 1404 - 1407  |  [Paper](https://daslab.stanford.edu/site_data/pub_pdf/2012_Kladwang_JACS.pdf)  |  [Link](http://pubs.acs.org/doi/abs/10.1021/ja2093508)

<hr/>
## Related Packages

HiTRACE

<hr/>
Developed by **Das lab**, _Leland Stanford Junior University_.

README by Johan, *May 2016*.

