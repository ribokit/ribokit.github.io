---
permalink: /Biers/varna/
level: 2
prev: rnastructure/
next: https://ribokit.github.io/RiboPaint/tutorial/
---

# Step 12: Visualize Secondary Structure _<small>(optional)</small>_

<br/>

This step requires proper setup of the package `biers`. Please follow the installation guides [there](/Biers/install). Note that this step only requires the Biers and VARNA part.

<hr/>

We use the `output_varna_html()` command to render **.html** files that utilize the VARNA applet. It draws the RNA sequence into the secondary structure, with nucleotides colored with their reactivity values, and showing helix-wise confidence estimate based on bootstrap `bpp`.

```matlab
output_varna_html('pfl_NA.html', sequence, structure_NA, structure, structure_NA, offset, [], [], [], bpp_NA);
```

In the above code, the `structure_NA`, which is the result of the prediction run, is used as display. It also compares between `structure` (reference structure that has been used in sequence assignment) with `structure_NA` and draw the differences in lines. 

> Since this run was using no data (thus no bootstrap), the values in `bpp_NA` are all 100%, and are not informative.

We can create **.html** pages for all the runs we have in [**Step 11**](../rnastructure/):

```matlab
output_varna_html('pfl_1D_Fold_SHAPE_minus.html', sequence, structure_1D_Fold_SHAPE_minus, structure, structure_1D_Fold_SHAPE_minus, offset, [], [], [d_SHAPE_minus; zeros(20, 1)], bpp_1D_Fold_SHAPE_minus);
output_varna_html('pfl_1D_Spkt_SHAPE_minus.html', sequence, structure_1D_Spkt_SHAPE_minus, structure, structure_1D_Spkt_SHAPE_minus, offset, [], [], [d_SHAPE_minus; zeros(20, 1)], bpp_1D_Spkt_SHAPE_minus);

output_varna_html('pfl_1D_Fold_SHAPE_plus.html', sequence, structure_1D_Fold_SHAPE_plus, structure, structure_1D_Fold_SHAPE_plus, offset, [], [], [d_SHAPE_plus; zeros(20, 1)], bpp_1D_Fold_SHAPE_plus);
output_varna_html('pfl_1D_Spkt_SHAPE_plus.html', sequence, structure_1D_Spkt_SHAPE_plus, structure, structure_1D_Spkt_SHAPE_plus, offset, [], [], [d_SHAPE_plus; zeros(20, 1)], bpp_1D_Spkt_SHAPE_plus);

output_varna_html('pfl_2D_Fold_SHAPE.html', sequence, structure_2D_Fold_SHAPE, structure, structure_2D_Fold_SHAPE, offset, [], [], [], bpp_2D_Fold_SHAPE);
output_varna_html('pfl_2D_Spkt_SHAPE.html', sequence, structure_2D_Spkt_SHAPE, structure, structure_2D_Spkt_SHAPE, offset, [], [], [], bpp_2D_Spkt_SHAPE);
```

For example, the blue lines are helices that are predicted by RNAstructure using data, but are not present in the reference structure (_false positive_). The orange lines are _false negative_, i.e. helices not captured by prediction.

[![output_varna_html Figure Fold SHAPE 1D plus](/biers/res/pfl_1D_pred_Fold_SHAPE_plus.png "output_varna_html Figure Fold SHAPE 1D plus"){: .half}](/biers/res/pfl_1D_pred_Fold_SHAPE_plus.png)
[![output_varna_html Figure ShapeKnot SHAPE 1D plus](/biers/res/pfl_1D_pred_Spkt_SHAPE_plus.png "output_varna_html Figure ShapeKnot SHAPE 1D plus"){: .half}](/biers/res/pfl_1D_pred_Spkt_SHAPE_plus.png)
{: .center}

> Right click on the VARNA applet to bring out the menu. You can change the drawing algorithm, rotate the graph, and other functions. Save to **.png** or **.eps** files for future use. **.eps** is vectorized and more suitable for publications.

To interpret the predictions,

* Compare to the prediction with no data.

You want to know how much your data influences the secondary structure prediction. The best way is to compare to the prediction with no data.

* Visual check for reactivity agreement.

Are predicted helices protected/unreactive? Are predicted loops/single-stranded regions reactive? 

> Are the _GAGUA_ reference hairpins predicted correctly?

* Pseudoknot

The `ShapeKnot` algorithm only allows one pseudoknot to be predicted. If your reference structure has more than 1, it cannot capture all. 

> You can use the reference structure as display structure to read out if any of the bootstrapping runs captured the missing pseudoknot. Or you can plot the `bpp`.

> When it fails to capture a pseudoknot, it usually makes up some other local helix instead. This is obvious that the made-up helix usually looks odd: reactive stems and/or protected loops.

* Bootstrap values

The higher the helix-wise confidence, the more robust the prediction. Usually > 90% is very good. Pseudoknots, if captured, still tend to have lower bootstrap numbers.

<hr/>

To visualize the `bpp`, we use the `print_bpp_Z()` command:

```matlab
print_bpp_Z(bpp_2D_cutoff_mean, Z_cutoff_mean, -15, '2D_cutoff_mean');
```

This command generates images of the `bpp` and `Z`. It asks for a scaling factor for the _Z-score_ figure. 

[![print_bpp_Z Figure 2D Z](/biers/res/pfl_2D_pred_Z_2D_cutoff_mean.png "print_bpp_Z Figure 2D Z"){: .half}](/biers/res/pfl_2D_pred_Z_2D_cutoff_mean.png)
[![print_bpp_Z Figure 2D bpp](/biers/res/pfl_2D_pred_bpp_2D_cutoff_mean.png "print_bpp_Z Figure 2D bpp"){: .half}](/biers/res/pfl_2D_pred_bpp_2D_cutoff_mean.png)
{: .center}
