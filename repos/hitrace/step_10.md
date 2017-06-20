---
permalink: /HiTRACE/tutorial/step_10/
level: 2
prev: step_9/
next: https://daslab.github.io/Biers/rnastructure/
---

# Step 10: Calculate Z-score _<small>(for 2D data only)</small>_

<br/>

This step requires proper setup of the package `rdatkit`. Please follow the installation guides [there](/RDATKit/install/). Note that we only using the _MATLAB_ components of `rdatkit`.

<hr/>

For **Mutate-and-Map** data, we care the most about 'release' events, i.e. a nucleotide becomes more reactive upon mutagenesis. Thus, the _Z-score_ is a great extraction of the traces. It compare a nucleotide's reactivity across all mutants, and score each one with how many standard deviation it 'stands out' from the mean.

> Nucleotide position that is originally reactive above certain cutoff is ignored, since we can't tell the 'release' for something already reactive.

> Final _Z-score_ are multiplied by -1.0 for the use as pseudo-free energies.

For more information, see these papers:

>Tian, S., Cordero, P., Kladwang, W., and Das, R. (**2014**)<br/>
>[High-throughput mutate-map-rescue evaluates SHAPE-directed RNA structure and uncovers excited states](http://rnajournal.cshlp.org/content/20/11/1815)<br/>
>*RNA* **20 (11)**: 1815 - 1826.

>Kladwang, W., VanLang, C.C., Cordero P., and Das, R. (**2011**)<br/>
>[A two-dimensional mutate-and-map strategy for non-coding RNA structure](http://www.nature.com/nchem/journal/v3/n12/abs/nchem.1176.html)<br/>
>*Nature Chemistry* **3**: 954 - 962.


To calculate _Z-score_, we use this command that reads in the _RDAT_ file:

```matlab
Z = output_Zscore_from_rdat('pfl_SHAPE_2Dbonus.txt', {filename});
```

It also saves the _Z-score_ matrix into a text file with the name you give. The reason that the data does not fill the entire figure (square) is that we only mutated along the region of interest, while the `sequence` contains flanking sequences. (So it's a rectangle window!)

[![output_Zscore_from_rdat Figure](/hitrace/res/pfl_2D_fig_Z.png "output_Zscore_from_rdat Figure"){: .half}](/hitrace/res/pfl_2D_fig_Z.png)
{: .center}

> If the `'mutation'` tag in `data_annotations` in you _RDAT_ file contains _T_ instead of _U_ (e.g. _A55T_ instead of _A55U_), the `output_Zscore_from_rdat()` can't function properly. Fix your _RDAT_ file.