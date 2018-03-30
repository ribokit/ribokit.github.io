---
permalink: /workflows/folding_energetics/
description: "Folding Energetic Prediction Workflow"
prev: ../structure_refinement/
next: ../design/
---

# I want to model RNA folding energetics

<hr/>

## About this workflow

Calculation of the folding energies and flexibilities of RNA structures is less well-developed than modeling the dominant (usually lowest energy) structure of a molecule. While Ribokit does not yet have a workflow *per se*, here are some things to try.

<br/>

## Workflow

* **For 3D RNA folders**, the [RNAMake](/RNAMake/) package includes predictive models for estimating free energies of folding of tertiary assembly. Measuring such energetics of folding in large RNAs typically requires tracking multiple transitions, and chemical mapping methods can deconvolve those transitions. The [LIFFT](/LIFFT/) package enables likelihood-based analysis of these data.

* **For single-molecule force spectroscopists**, the [HelixMC](/HelixMC/) package allows prediction of mechanical properties of long double-stranded RNA and DNA using base-pair-level models derived from RNA crystallography.

<br/>

## Limitations

+ These packages are only recently being tested in blind predictions, and are not well integrated with each other yet. 

<hr/>
## References

>Chou, F.-C., Echols, N., Terwilliger, T.C., and Das, R. (**2016**) <br/>
>**RNA structure refinement using the ERRASER-Phenix pipeline**{: style="color:#3399cc"}<br/>
>*Methods in Molecular Biology* **1320**: 269 - 282. | [Paper](https://daslab.stanford.edu/site_data/pub_pdf/2016_Chou_MIMB.pdf) | [Link](http://link.springer.com/protocol/10.1007%2F978-1-4939-2763-0_17)

>Chou, F.-C., Sripakdeevong, P., Dibrov, S.M, Hermann, T., and Das, R. (**2013**) <br/> 
>**Correcting pervasive errors in RNA crystallography through enumerative structure prediction**{: style="color:#3399cc"}<br/>
*Nature Methods* **10**: 74 - 76. | [Paper](https://daslab.stanford.edu/site_data/pub_pdf/2013_Chou_NatMeth.pdf) | [Link](http://www.nature.com/nmeth/journal/v10/n1/full/nmeth.2262.html)
