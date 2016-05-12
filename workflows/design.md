---
permalink: /workflows/design/
description: "3D Design workflow"
---

# I want to design a new RNA molecule

<hr/>

## About this workflow
*[Under construction]* This workflow is being developed to allow creation of complex 3D RNA structures, built out of motifs and tertiary contacts drawn from natural molecules. The main use case at the moment is to design tethers connecting from one helix to another helix position, to stabilize existing 3D RNA structures.


## Workflow

1. **Design tertiary structure**. Do you already have a motif or tertiary contact structure that you want to stabilize?  
 + __Yes__. Use Rosetta [RNA Redesign](/RNADesign). 
 + __No__. Design a new RNA tether or nanostructure in [RNAMake](RNAmake/). The sequences of the internal junctions and tertiary contacts will be defined by the motifs, but the helices will be arbitrary. 
2. **Design secondary structure**  to optimize the sequences of the helices that are least likely to misfold with your motif sequences.  Use the [EternaBot server](http://eternabot.cmu.edu/) or its implementation within [RNAMake](RNAmake/)
3. **Experimentally test** that your designs are forming the correct structure, specifically checking for chemical protection of any tertiary contacts. Follow this [Workflow](/workflows/from_scratch/)

## Limitations
 + Automatic algorithms for 3D design are currently being tested through extensive experiments, but are not published yet.
 + Confidence estimation in 3D design is not available yet. 
 
## References
>
Lee, J., Kladwang, W., Lee, M., Cantu, D., Azizyan, M., Kim, H., Limpaecher, A., Yoon, S., Treuille, A., Das, R., and EteRNA Participants (**2014**) 
<br/>
[RNA design rules from a massive open laboratory](http://www.pnas.org/content/111/6/2122) 
*Proceedings of the National Academy of Sciences U.S.A.* **111 (6)** : 2122 - 2127. [Paper](https://daslab.stanford.edu/site_data/pub_pdf/2014_Lee_PNAS.pdf)
