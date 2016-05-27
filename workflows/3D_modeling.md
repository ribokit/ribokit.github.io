---
permalink: /workflows/3D_modeling/
description: "3D Modeling Workflow"
prev: alternative_states/
next: structure_refinement/
---

# I think my RNA has a 3D structure

<hr/>

## About this workflow

While many RNA segments do not form stereotyped 3D structures, for the ones that do, the tertiary folds define the molecules' functions. Multidimensional chemical mapping offers a rapid approach to nucleotide-resolution fold determination as well as to detection of transient tertiary proximities in, e.g., ligand-free states of riboswitch aptamers.

<br/>

## Workflow

1. Make sure you can *synthesize* your RNA using this [basic workflow](/workflows/from-scratch/).

2. You may want to confirm your RNA's *secondary structure* using [mutate-and-map](/workflows/2d_modeling/) or [compensatory mutation-rescue](/workflows/mutation_rescue/). 

3. Carry out the **MOHCA-seq** measurement to infer tertiary proximities present in solution; using [MAPseeker](/MAPseeker/).

4. Carry out 3D Rosetta modeling with [FARFAR](/RNAdenovo/), guided by these secondary structure and tertiary proximity data.

5. Make sure to assess uncertainties based on intra-cluster RMSD; these can range from 0.5 to 2 nm, depending on the size of the RNA and the number of tertiary proximities.

<br/>

## Limitations

+ Unlike secondary structure modeling, there are not yet ways to prospectively and rapidly test tertiary contacts inferred from MOHCA-seq.

+ For RNA states that involve heterogenuous tertiary structures, the model ensembles above do not provide rigorous portraits of the solution flexibility of the RNA. Consider them initial visualizations to aid, e.g., further mutational experiments. 

<hr/>
## References

>Tian, S., and Das, R. (**2016**)<br/>
>**RNA structure through multidimensional chemical mapping**{: style="color:#3399cc"}<br/>
>*Quarterly Review of Biophysics* **49 (e7)**: 1 - 30. | [Paper](https://daslab.stanford.edu/site_data/pub_pdf/2016_Tian_QRB.pdf) | [Link](http://journals.cambridge.org/action/displayAbstract?fromPage=online&aid=10242118&fulltextType=RV&fileId=S0033583516000020)

>Cheng, C. Y., Chou, F.-C., Kladwang, W., Tian, S., Cordero, P. & Das, R. (**2015**) <br/>
>**Consistent global structures of complex RNA states through multidimensional chemical mapping**{: style="color:#3399cc"}<br/>
>*eLife* **4**: e07600. | [Paper](https://daslab.stanford.edu/site_data/pub_pdf/2015_Cheng_eLife.pdf) | [Link](http://elifesciences.org/content/4/e07600)

>Cheng, C. Y., Chou, F.-C., and Das, R. (**2015**) <br/> 
>**Modeling complex RNA tertiary folds with Rosetta]**{: style="color:#3399cc"}<br/>
>*Methods in Enzymology* **553**: 35 - 64. | [Paper](https://daslab.stanford.edu/site_data/pub_pdf/2015_Cheng_MethEnzym.pdf) | [Link](http://www.sciencedirect.com/science/article/pii/S0076687914000524)

