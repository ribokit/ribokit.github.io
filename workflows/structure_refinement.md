---
permalink: /workflows/structure_refinement/
description: "3D Structure Refinement Workflow"
prev: 3D_modeling/
next: folding_energetics/
---

# I have crystallographic/cryoEM data

<hr/>

## About this workflow

Stereochemical & backbone building errors are common in medium-resolution experimental structures of RNAs due to the difficulty and tedium of manually fitting coordinates into density maps. We maintain tools to help correct these errors automatically.

## Workflow

1. **Prepare** your map from cryoEM or crystallography and starting coordinates. 

2. Carry out **[ERRASER](/ERRASER/)** either via server, on your laptop with Rosetta, or as part of PHENIX.

3. *[Coming soon: Test that your structure are consistent with one-dimensional chemical accessibility data easily acquired with this [basic workflow](/workflows/from-scratch/). E-mail us if interested.]*

## Limitations

+ The publicly available version of ERRASER does not handle RNA interfaces with proteins, ions, and small molecules & nonnatural nucleotides and does not take advantage of multiple processes for speed, but these functionalities are coming soon. *E-mail us if you are interested in testing.*

+ ERRASER carries out one-at-a-time remodeling of each nucleotide in the structure, and cannot refine stretches of nucleotides that have major errors. Again, we are working on updates to handle such cases. *E-mail us if you have an interesting test case.*

## References

>Chou, F.-C., Echols, N., Terwilliger, T.C., and Das, R. (**2016**) <br/>
>**RNA structure refinement using the ERRASER-Phenix pipeline**{: style="color:#3399cc"}<br/>
>*Methods in Molecular Biology* **1320**: 269 - 282. | [Paper](https://daslab.stanford.edu/site_data/pub_pdf/2016_Chou_MIMB.pdf) | [Link](http://link.springer.com/protocol/10.1007%2F978-1-4939-2763-0_17)

>Chou, F.-C., Sripakdeevong, P., Dibrov, S.M, Hermann, T., and Das, R. (**2013**) <br/> 
>**Correcting pervasive errors in RNA crystallography through enumerative structure prediction**{: style="color:#3399cc"}<br/>
*Nature Methods* **10**: 74 - 76. | [Paper](https://daslab.stanford.edu/site_data/pub_pdf/2013_Chou_NatMeth.pdf) | [Link](http://www.nature.com/nmeth/journal/v10/n1/full/nmeth.2262.html)
