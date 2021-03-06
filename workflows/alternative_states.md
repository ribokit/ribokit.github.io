---
permalink: /workflows/alternative_states/
description: "Alternative States (Multi-State) Workflow"
prev: ../mutation_rescue/
next: ../3D_modeling/
---

# I think my RNA has interesting alternative states

<hr/>

## About this workflow

RNA sequences often form multiple secondary structures, some of which are functionally important, and others that need to be avoided in the biological milieu. Evidence for alternative structures often comes from single-molecule biophysics measurements or NMR, but it's hard to model the structures, even at nucleotide resolution. This new workflow allows for rapid detection and structure modeling of secondary structure ensembles.

<br/>

## Workflow

1. **Carry out the mutate-and-map** experiment described in this [workflow](/workflows/2D_modeling/). 

2. **Model sets of possible base pairs** in [REEFFIT](/REEFFIT/) and <b>determine which single mutants</b> might stabilize putative alternative structures. *[Coming soon: fast cluster analysis in [Biers](/Biers/)]*

3. **Test alternative structures** through compensatory mutation/rescue, read out through chemical mapping. See notes at [Primerize](/Primerize/).

4. Make predictions or the behavior of **the structure-stabilizing mutants** in your alternative functional assay (e.g., single molecule FRET measurements), and **test them**.

<br/>

## Limitations

+ REEFFIT is computationall expensive. It is not yet well optimized for RNAs beyond about 50-100 nts in length; computations for molecules of that size or with numerous mutants remain challenging, even on high-performance clusters.

+ REEFFIT typically detects helices that are present at >10% population in the starting sequence. Make sure to get bootstrapping error estimates to evaluate the significance of low population helices. 

<hr/>
## References

>Tian, S., and Das, R. (**2016**)<br/>
>**RNA structure through multidimensional chemical mapping**{: style="color:#3399cc"}<br/>
>*Quarterly Review of Biophysics* **49 (e7)**: 1 - 30. | [Paper](https://daslab.stanford.edu/site_data/pub_pdf/2016_Tian_QRB.pdf) | [Link](http://journals.cambridge.org/action/displayAbstract?fromPage=online&aid=10242118&fulltextType=RV&fileId=S0033583516000020)

>Cordero, P., and Das, R. (**2015**)<br/>
>**Rich structure landscapes in both natural and artificial RNAs revealed by mutate-and-map analysis**{: style="color:#3399cc"}<br/>
>*PLOS Computational Biology* **11 (11)**: e1004473. | [Paper](https://daslab.stanford.edu/site_data/pub_pdf/2015_Cordero_PLOSComptBiol.pdf) | [Link](http://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1004473)

>Tian, S., Cordero, P., Kladwang, W., and Das, R. (**2014**)<br/> 
>**High-throughput mutate-map-rescue evaluates SHAPE-directed RNA structure and uncovers excited states**{: style="color:#3399cc"}<br/>
>*RNA* **20 (11)**: 1815 - 1826. | [Paper](https://daslab.stanford.edu/site_data/pub_pdf/2014_Tian_RNA.pdf) | [Link](http://rnajournal.cshlp.org/content/20/11/1815)
