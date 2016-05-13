---
permalink: /workflows/mutation_rescue/
description: "Compensatory Mutation/Rescue Workflow"
prev: 2D_modeling/
next: alternative_states/
---

# I want to test an RNA secondary structure model

<hr/>

## About this workflow

Compensatory mutation/rescue is a classic methodology that can give strong confidence in modeled Watson/Crick base pairs. Chemical mapping offers a general readout for this method that does not require having a functional assay to readout rescue.

## Workflow

1. **Design primers** for each candidate base pair with [Primerize](/Primerize/).

2. Carry out the **chemical mapping** measurements.  

3. Look to see if single mutants exhibit distorted chemical mapping profiles compared to the starter sequence, and if double mutants restore the original profile.

## Limitations

+ The analysis above to score the likelihood of each tested base pair is not yet automated.

+ For helices that are short or that are involved in tertiary contacts, compensatory base changes may not 'rescue' chemical profiles. Lack of rescue does not rule out the present of the base pair in the original state. (On the other hand, observation of rescue is strong evidence for a pairing and disfavors alternative pairings that involve the probed nucleotides.)
 
## References

>Tian, S., and Das, R. (**2016**)<br/>
>**RNA structure through multidimensional chemical mapping**{: style="color:#3399cc"}<br/>
>*Quarterly Review of Biophysics* **49 (e7)**: 1 - 30. | [Paper](https://daslab.stanford.edu/site_data/pub_pdf/2016_Tian_QRB.pdf) | [Link](http://journals.cambridge.org/action/displayAbstract?fromPage=online&aid=10242118&fulltextType=RV&fileId=S0033583516000020)

>Tian, S., Cordero, P., Kladwang, W., and Das, R. (**2014**)<br/> 
>**High-throughput mutate-map-rescue evaluates SHAPE-directed RNA structure and uncovers excited states**{: style="color:#3399cc"}<br/>
>*RNA* **20 (11)**: 1815 - 1826. | [Paper](https://daslab.stanford.edu/site_data/pub_pdf/2014_Tian_RNA.pdf) | [Link](http://rnajournal.cshlp.org/content/20/11/1815)
