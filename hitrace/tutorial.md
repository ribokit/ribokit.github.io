---
layout: docs
permalink: /hitrace/tutorial/

title: HiTRACE
description: "<u>Hi</u>gh-<u>T</u>hroughput <u>R</u>obust <u>A</u>nalysis for <u>C</u>apillary <u>E</u>lectrophoresis"
repo: hitrace/hitrace
author: Siqi Tian
---

## Script Template


<hr/>
## Analysis Pipeline

The complete HiTRACE analysis pipeline is composed of the following steps.

* ### #1: Load and Preview Data
Read in data and provide a quick look.

* ### #2: Further Alignment <small>*(optional)*</small>
Perform additional finer alignments.

* ### #3: Parameter Input
Input experiment details and basic RNA construct information.

* ### #4: Sequence Assignment
Annotate the position of each nucleotide position on the gel matching bands.

* ### #5: Peak Fitting
Integrate band intensities into nucleotide peak readings.

* ### #6: Data Corrections <small>*(for 1D data only)*</small>
Perform unsaturation, attenuation correction, background subtraction, and normalization for 1D data.

* ### #7: Save your Work <small>*(optional)*</small>
Print well-annotated figures of your analysis for archiving.

* ### #8: Output RDAT File
Write analyzed result to file in RDAT format, for use of Z-score and prediction.

* ### #9: Calculate Z-score <small>*(for 2D data only)*</small>
Transfrom 2D chemical mapping data into Z-score for use as 2D pseudo-free energy bonus for RNAstructure.

* ### #10: Visualize Secondary Structure <small>*(optional)*</small>
Draw secondary structure using [VARNA](http://varna.lri.fr/) with nucleotides color-coded by reactivity, and mark difference between secondary structure models.

* ### #11: Predict Secondary Structure
Run structural prediction using [RNAstructure](http://rna.urmc.rochester.edu/RNAstructure.html) based on chemical mapping reactivity data, with bootstrapping for helix-wise confidence score.

<hr/>
## Bonus Graphic Tools

* ### Color Secondary Structure Diagram
Make publication-ready diagram of secondary structures with nucleotides color-coded by reactivity.

* ### Color 3D Model
Make publication-ready 3D models with nucleotides color-coded by reactivity.

<hr/>
## Share your Data

* ### Submit to RMDB
Share your chemical mapping results to [RNA Mapping Database](https://rmdb.stanford.edu).
