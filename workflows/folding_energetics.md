---
permalink: /workflows/folding_energetics/
level: 2
description: "Energetic prediction workflow"
title: "Folding Energetics Workflow"
author: "Rhiju Das"
---

# I want to model RNA folding energetics
<hr/>

## About this workflow
Calculation of the folding energies and flexibilities 
of RNA structures is less well-developed than modeling the dominant (usually lowest energy) structure of a molecule. While Ribokit does not yet have a workflow *per se*, here are some things to try.

## Workflow
 + **For single-molecule force spectroscopists**, the [HelixMC](HelixMC) package allows prediction of mechanical properties of long double-stranded RNA and DNA using base-pair-level models derived from RNA crystallography.
 + **For 3D RNA folders**, the [RNAMake](RNAMake) package includes predictive models for estimating free energies of folding of tertiary assembly. As with [HelixMC](HelixMC/), contributions of helix flexibility, including large effects from helix sequence, are assessed through base-pair-level models.
 + **For molecular dynamicists and epitranscriptomicists**, the [RECCES](RECCES) module in Rosetta allows estimation of nearest-neighbor parameters for helix stacked pairs and dangling ends.
 
## Limitations

+ These packages are only recently being tested in blind predictions, and are not well integrated with each other yet. 

## References
>	
Chou, F.-C., Echols, N., Terwilliger, T.C., and Das, R. (**2016**) <br/>
[RNA structure refinement using the ERRASER-Phenix pipeline](http://link.springer.com/protocol/10.1007%2F978-1-4939-2763-0_17) 
*Methods in Molecular Biology*
**1320** : 269 - 282. [Paper](https://daslab.stanford.edu/site_data/pub_pdf/2016_Chou_MIMB.pdf)

>	
Chou, F.-C., Sripakdeevong, P., Dibrov, S.M, Hermann, T., and Das, R. 
(**2013**) <br/> 
[Correcting pervasive errors in RNA crystallography through enumerative structure prediction](http://www.nature.com/nmeth/journal/v10/n1/full/nmeth.2262.html) 
*Nature Methods* **10 : 74 - 76** 
 [Paper](https://daslab.stanford.edu/site_data/pub_pdf/2013_Chou_NatMeth.pdf)

