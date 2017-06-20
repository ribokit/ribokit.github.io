---
permalink: /HiTRACE/tutorial/
level: 2
prev: install/
---

## Example Files
Example scripts and data are included in the **HiTRACE** [repository](https://github.com/hitrace/HiTRACE/). For a new analysis, start with these example scripts and replace relevant values with yours:

* 1D Analysis: _[Script](https://github.com/hitrace/HiTRACE/blob/master/Examples/example_pfl_1D.m), [CE Data](https://github.com/hitrace/HiTRACE/blob/master/Examples/data_pfl_1D.zip), [Workspace](https://github.com/hitrace/HiTRACE/blob/master/Examples/example_pfl_1D.mat)_

* 2D Analysis: _[Script](https://github.com/hitrace/HiTRACE/blob/master/Examples/example_pfl_2D.m), [CE Data](https://github.com/hitrace/HiTRACE/blob/master/Examples/data_pfl_2D.zip), [Workspace](https://github.com/hitrace/HiTRACE/blob/master/Examples/example_pfl_2D.mat)_

* [**NEW**{: style="color:#ff5c2b;"}] For further practice, we provide 12 more examples. They are previous 1D and 2D datasets annotated by our experts. Download [Script &amp; Data](https://rmdb.stanford.edu/site_data/HiTRACE_more_practice.zip), and follow these [instructions](practice/).

> Workspace files are provided for comparison only, when you want to double check if your results are the same (especially for [**Step #4**](step_4/)). They are not needed for trying out and starting fresh.

<hr/>
## Analysis Pipeline

[![HiTRACE.org Flow Chart](/hitrace/res/flowchart.png "HiTRACE.org Flow Chart"){: .full}](http://hitrace.org/page/view/about)
{: .center}

The complete HiTRACE analysis pipeline is composed of the following steps.

* ### #0: [Get Started](step_0/)
Checklist before kick off.

* ### #1: [Load and Preview Data](step_1/)
Read in data and provide a quick look.

* ### #2: [Further Alignment](step_2/) <small>*(optional)*</small>
Perform additional finer alignments.

* ### #3: [Parameter Input](step_3/)
Input experiment details and basic RNA construct information.

* ### #4: [Sequence Assignment](step_4/)
Annotate the position of each nucleotide position on the gel matching bands.

* ### #5: [Peak Fitting](step_5/)
Integrate band intensities into nucleotide peak readings.

* ### #6: [Data Corrections](step_6/) <small>*(for 1D data only)*</small>
Perform unsaturation, attenuation correction, background subtraction, and normalization for 1D data.

* ### #7: [Error Estimates](step_7/) <small>*(for 1D data only)*</small>
Evaluate data and estimate errors across replicates.

* ### #8: [Save your Work](step_8/)
Print well-annotated figures of your analysis for archiving.

* ### #9: [Output RDAT File](step_9/)
Write analyzed result to file in RDAT format, for use of _Z-score_ and prediction.

* ### #10: [Calculate Z-score](step_10/) <small>*(for 2D data only)*</small>
Transfrom 2D chemical mapping data into _Z-score_ for use as 2D pseudo-free energy bonus for RNAstructure.

* ### #11: [Predict Secondary Structure](https://daslab.github.io/Biers/rnastructure/)
Run structural prediction using [RNAstructure](http://rna.urmc.rochester.edu/RNAstructure.html) based on chemical mapping reactivity data, with bootstrapping for helix-wise confidence score.

* ### #12: [Visualize Secondary Structure](https://daslab.github.io/Biers/varna/) <small>*(optional)*</small>
Draw secondary structure using [VARNA](http://varna.lri.fr/) with nucleotides color-coded by reactivity, and mark difference between secondary structure models.

<hr/>
## Bonus Graphic Tools

* ### [Color 2D Diagram](https://ribokit.github.io/RiboPaint/tutorial/)
Make publication-ready diagram of secondary structures with nucleotides color-coded by reactivity.

* ### [Color 3D Model](https://ribokit.github.io/RiboVis/tutorial/)
Make publication-ready 3D models with nucleotides color-coded by reactivity.

<hr/>
## Share your Data

* ### Submit to RMDB
Share your chemical mapping results to [RNA Mapping Database](https://rmdb.stanford.edu).
