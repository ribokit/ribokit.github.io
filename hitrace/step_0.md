---
layout: docs
permalink: /hitrace/tutorial/step_0/
root: /hitrace/
next: step_1/

title: HiTRACE
description: "<u>Hi</u>gh-<u>T</u>hroughput <u>R</u>obust <u>A</u>nalysis for <u>C</u>apillary <u>E</u>lectrophoresis"
repo: hitrace/hitrace
author: Siqi Tian
---

# Step 0: Get Started

<br/>

* ### Please follow the [**installation**](/hitrace#installation) guidelines to download HiTRACE scripts, and register to _MATLAB_ path.

* ### For all of the commands used, use `help func_name` to retrieve help information on syntax usage.

* ### Save your work frequently! Also organize your scripts.

We recommend running `save` command often to save your workspace into **.mat** files in case of unexpected _MATLAB_ termination. Please familiarize with commands like `load`, `clear`, `close`, `which` too.

* ### Note that throughout the analysis, the electrophoretic traces are aligned vertically, so that higher mobility products (which pass the sequencer detector first) show up at the top. 

This is basically historical; note that most biochemical papers take a different convention where the faster products are at the bottom, and in some of our papers, we show the traces aligned horizontally (this wasted the least space for early data sets like [this mutate/map study](https://daslab.stanford.edu/site_data/pub_pdf/2011_Kladwang_NatChem.pdf)).

* ### Please report problems to [rhiju@stanford.edu](mailto:rhiju@stanford.edu). So we can fix them!

* ### Papers describing the HiTRACE method [(Yoon _et al._ 2011)](https://daslab.stanford.edu/site_data/pub_pdf/2011_Yoon_Bioinfo.pdf), background subtraction, 'overmodification' correction, and error analyses [(Kladwang _et al._ 2014)](https://daslab.stanford.edu/site_data/pub_pdf/2014_Kladwang_Biochem.pdf), online version of HiTRACE [(Kim _et al._ 2013)](https://daslab.stanford.edu/site_data/pub_pdf/2013_Kim_NAR.pdf), and new auto-assign algorithm [(Lee _et al._ 2015)](https://daslab.stanford.edu/site_data/pub_pdf/2015_Lee_Bioinfo.pdf) are listed as [**reference**](/hitrace#reference). Please cite accordingly.

