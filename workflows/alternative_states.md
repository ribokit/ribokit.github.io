---
permalink: /workflows/alternative_states/
level: 2
description: "Alternative states workflow"
title: "Workflow"
author: "Rhiju Das"
---

# I have just discovered an RNA molecule

<hr/>

## About this workflow
This is the <b>most common workflow</b> that RiboKit tools are used for. The goal is to take a new RNA sequence, quickly synthesize it, map its chemical profile, and test if it has a dominant secondary structure. 

It can take as little as 1-2 days if the capillary electrophoresis sequencer and reagents are in hand (see work on RNA puzzles and Eterna).

This workflow is similar to excellent methods developed by other labs for SHAPE-directed secondary structure modeling, but emphasizes uncertainty estimation. Evaluating uncertainties prevents misleading structure inferences and allows assessment of whether multidimensional chemical mapping analysis is necessary. 

Examples of successful application include solving numerous structures <i>de novo</i> for the community-wide blind trials RNA-puzzles, inferring structures for new RNA regulons that allow for <i>in vivo</i> compensatory rescue, and testing sequences designed to form target secondary structures in the <a href="http://www.eternagame.org">Eterna project</a>.

## Workflow

1. <b>Synthesize</b> your RNA using the instructions in [Primerize](Primerize/). 
2. <b>Carry out one-dimensional (1D) chemical mapping</b> using SHAPE, DMS, and CMCT probes. See [Protocols](/protocol/).
3. <b>Carry out RNA secondary structure prediction</b> guided by these data, with bootstrapping. 
4. Does your secondary structure model have high bootstrap confidence for all helices? 
 + __Yes__. Then you've likely achieved the answer! If you think your RNA has a stereotyped 3D structure, check out the RiboKit [workflow for 3D modeling](/workflows/3D_modeling/)
 + __No__. You don't have the answer. Carry out multidimensional chemical mapping to [nail the RNA secondary structure](2D_modeling) and/or look for multiple secondary structures.

 
## References
>	
Kladwang, W., VanLang, C.C., Cordero P., and Das, R.  (**2011**) <br/>
[Understanding the errors of SHAPE-directed RNA structure modeling](http://pubs.acs.org/doi/abs/10.1021/bi200524n) 
*Biochemistry* **50 (37)** : 8049 - 8056. [Paper](http://pubs.acs.org/doi/abs/10.1021/bi200524n)

>	
Miao, Z., Adamiak, R.W., Blanchet, M-F., Boniecki, M., Bujnicki, J.M., Chen, S-J., et al. (**2015**) <br/>
[RNA-Puzzles Round II: Assessment of RNA structure prediction programs applied to three large RNA structures](http://rnajournal.cshlp.org/content/21/6/1066) *RNA* **21 (6)** : 1066 - 1084. [Paper](https://daslab.stanford.edu/site_data/pub_pdf/2015_Miao_RNA.pdf)


