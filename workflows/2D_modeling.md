---
permalink: /workflows/2D_modeling/
description: "Mutate-and-Map 2D Modeling Workflow"
---

# I want to learn an RNA's secondary structure

<hr/>

## About this workflow
The mutate-and-map experimental protocol gives rich data on an RNA's structure by measuring how the chemical accessibility of each nucleotide changes with respect to mutations of every other nucleotide.

## Workflow

1. Do the **basic characterization** of your RNA with this [workflow](/workflows/2D_modeling/). 
2. **Design primer plates** for mutate-and-map experiments with [Primerize](Primerize/).
3. Carry out the **[mutate-and-map](/protocols/)** measurements.  
4. **Analyze** the data to infer a dominant secondary structure, with bootstrapping, with [Biers](Biers/).
5. Does your secondary structure model have high bootstrap confidence for all helices? 
 + __Yes__. Then you've likely achieved the answer. If you think your RNA has a stereotyped 3D structure, check out the RiboKit [workflow for 3D modeling](/workflows/3D_modeling/)
 + __No__. Carry out compensatory mutation/rescue experiments to test each base pair possibility, using [this workflow](/workflows/mutation_rescue/).
6. Do several of the mutations dramatically change the RNA's chemical profile?  These may be revealing alternative states present at low frequency (but of possible biological interest) in the starting sequence. Check out the [workflow for probing alternative states](/workflows/alternative_states)

## Limitations
 + The edge base pairs of helices remain difficult to capture with mutate-and-map analysis (see references, including blind tests, below).  
 + The current protocol requires PCR assembly of your RNA, which works well for molecules up to about 200 nucleotides. A 'one-pot' protocol is under development which should allow mutate-and-map data on longer transcripts *E-mail us if interested.* In addition, the [MOHCA-seq](3D_modeling) experimental protocol can still detect stable secondary structure.


 
## References
>	
Tian, S., and Das, R. (**2016**)  
[RNA structure through multidimensional chemical mapping](http://journals.cambridge.org/action/displayAbstract?fromPage=online&aid=10242118&fulltextType=RV&fileId=S0033583516000020)
*Quarterly Review of Biophysics* **49 (e7)** : 1 - 30. [Paper](https://daslab.stanford.edu/site_data/pub_pdf/2016_Tian_QRB.pdf)

>	
Miao, Z., Adamiak, R.W., Blanchet, M-F., Boniecki, M., Bujnicki, J.M., Chen, S-J., et al. (**2015**) <br/>
[RNA-Puzzles Round II: Assessment of RNA structure prediction programs applied to three large RNA structures](http://rnajournal.cshlp.org/content/21/6/1066) *RNA* **21 (6)** : 1066 - 1084. [Paper](https://daslab.stanford.edu/site_data/pub_pdf/2015_Miao_RNA.pdf)

>		
Cordero, P., Kladwang, W., VanLang, C.C., and Das, R. (**2014**) <br/>
[The mutate-and-map protocol for inferring base pairs in structured RNA](http://link.springer.com/protocol/10.1007%2F978-1-62703-667-2_4)
*Methods in Molecular Biology* 
**1086: 53 - 77.** [Paper](https://daslab.stanford.edu/site_data/pub_pdf/2014_Cordero_MIMB.pdf)

