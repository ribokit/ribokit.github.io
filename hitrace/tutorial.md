---
layout: docs
permalink: /hitrace/tutorial/
root: /hitrace/

title: HiTRACE
description: "<u>Hi</u>gh-<u>T</u>hroughput <u>R</u>obust <u>A</u>nalysis for <u>C</u>apillary <u>E</u>lectrophoresis"
repo: hitrace/hitrace
author: Siqi Tian
---

## Example Files
Example scripts and data are included in the **HiTRACE** [repository](https://github.com/hitrace/hitrace/). For a new analysis, start with these example scripts and replace relevant values with yours:

* 1D Analysis: _[Script](https://github.com/hitrace/hitrace/blob/master/TestData/example_pfl_1D.m), [Data](https://github.com/hitrace/hitrace/blob/master/TestData/data_pfl_1D.zip)_

* 2D Analysis: _[Script](https://github.com/hitrace/hitrace/blob/master/TestData/example_pfl_2D.m), [Data](https://github.com/hitrace/hitrace/blob/master/TestData/data_pfl_2D.zip)_

* Color Diagram: _[Script](https://github.com/hitrace/hitrace/blob/master/TestData/example_pfl_color.m), [Image](https://github.com/hitrace/hitrace/blob/master/TestData/pfl_secstr.tif)_

<hr/>
## Analysis Pipeline

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

* ### #8: [Save your Work](step_8/) <small>*(optional)*</small>
Print well-annotated figures of your analysis for archiving.

* ### #9: [Output RDAT File](step_9/)
Write analyzed result to file in RDAT format, for use of _Z-score_ and prediction.

* ### #10: [Calculate Z-score](step_10/) <small>*(for 2D data only)*</small>
Transfrom 2D chemical mapping data into _Z-score_ for use as 2D pseudo-free energy bonus for RNAstructure.

* ### #11: [Predict Secondary Structure](/biers/rnastructure/)
Run structural prediction using [RNAstructure](http://rna.urmc.rochester.edu/RNAstructure.html) based on chemical mapping reactivity data, with bootstrapping for helix-wise confidence score.

* ### #12: [Visualize Secondary Structure](/biers/varna/) <small>*(optional)*</small>
Draw secondary structure using [VARNA](http://varna.lri.fr/) with nucleotides color-coded by reactivity, and mark difference between secondary structure models.

<hr/>
## Bonus Graphic Tools

* ### [Color 2D Diagram](bonus_2d/)
Make publication-ready diagram of secondary structures with nucleotides color-coded by reactivity.

* ### [Color 3D Model](bonus_3d/)
Make publication-ready 3D models with nucleotides color-coded by reactivity.

<hr/>
## Share your Data

* ### Submit to RMDB
Share your chemical mapping results to [RNA Mapping Database](https://rmdb.stanford.edu).
