---
permalink: /HiTRACE/tutorial/step_0/
level: 2
next: step_1/
---

# Step 0: Get Started

<br/>

## MATALB environment

* Please follow the [**installation**](../../install/) guidelines to download HiTRACE scripts, and register to _MATLAB_ path.

* For all of the commands used, use `help func_name` to retrieve help information on syntax usage.

<hr/>

## Best Practice
{: style="color:#ff5c2b;"}

For a standard HiTRACE analysis, we recommend the following files as conclusive end-points:

* A saved workspace **.mat** file for analysis reuse.

* A saved script **.m** file for command records.

* A saved text-based **.rdat** file for sharing.

* Annotated figures for raw (gel) data and sequence assignment (see `print_xsel_split` in [**Step #8**](../step_8/)).

In other words, you should have the **.mat** workspace, **.m** script and **.eps** figures on your disk once you finished analysis, just like the ones from the provided [example](https://github.com/hitrace/HiTRACE/tree/master/Examples) and shown in this tutorial series.

Thus please **save your work frequently!** Also organize your scripts. We recommend running `save` command often to save your workspace into **.mat** files in case of unexpected _MATLAB_ termination. Please familiarize with commands like `load`, `clear`, `close`, `which` too.


<hr/>

## Data Display

* Note that throughout the analysis, the electrophoretic traces are aligned vertically, so that higher mobility products (which pass the sequencer detector first) show up at the top. 

This is basically historical; note that most biochemical papers take a different convention where the faster products are at the bottom, and in some of our papers, we show the traces aligned horizontally (this wasted the least space for early data sets like [this mutate/map study](https://daslab.stanford.edu/site_data/pub_pdf/2011_Kladwang_NatChem.pdf)).

<hr/>

## Citations

* Papers describing the HiTRACE method [(Yoon _et al._ 2011)](https://daslab.stanford.edu/site_data/pub_pdf/2011_Yoon_Bioinfo.pdf), background subtraction, 'overmodification' correction, and error analyses [(Kladwang _et al._ 2014)](https://daslab.stanford.edu/site_data/pub_pdf/2014_Kladwang_Biochem.pdf), online version of HiTRACE [(Kim _et al._ 2013)](https://daslab.stanford.edu/site_data/pub_pdf/2013_Kim_NAR.pdf), and new auto-assign algorithm [(Lee _et al._ 2015)](https://daslab.stanford.edu/site_data/pub_pdf/2015_Lee_Bioinfo.pdf) are listed as [**reference**](/HiTRACE#reference). Please cite accordingly.

* Please report problems to [rhiju@stanford.edu](mailto:rhiju@stanford.edu). So we can fix them!
