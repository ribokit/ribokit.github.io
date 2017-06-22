---
permalink: /Biers/rnastructure/
level: 2
prev: https://hitrace.github.io/HiTRACE/tutorial/step_10/
next: varna/
---

# Step 11: Predict Secondary Structure

<br/>

This step requires proper setup of the package `biers`. Please follow the installation guides [there](/Biers/install). Note that this step only requires the RNAstructure and Biers part.

<hr/>

We use the [RNAstructure](http://rna.urmc.rochester.edu/RNAstructure.html) package to perform data-driven secondary structure predictions. The **1D** and/or **2D** data are transformed into pseudo-free energies that provide information to guide folding, on top of the built-in Nearest Neighbor thermodynamic parameters.

To estimate the confidence of the predicted result, we use nonparametric bootstrapping. In brief, it resamples the data with replacement to create mock datasets, and use these to run prediction again, and summarize the result of all mock runs. This resampling technique is relevant as experimental measurements may miss certain data points (imperfect dataset). It tests whether the prediction result is robust to (slight) data variations, e.g. if one nucleotide's reactivity dominates the outcome. For more information, see these papers:

>Tian, S., Cordero, P., Kladwang, W., and Das, R. (**2014**)<br/>
>[High-throughput mutate-map-rescue evaluates SHAPE-directed RNA structure and uncovers excited states](http://rnajournal.cshlp.org/content/20/11/1815)<br/>
>*RNA* **20 (11)**: 1815 - 1826.

>Kladwang, W., VanLang, C.C., Cordero P., and Das, R. (**2011**)<br/>
>[A two-dimensional mutate-and-map strategy for non-coding RNA structure](http://www.nature.com/nchem/journal/v3/n12/abs/nchem.1176.html)<br/>
>*Nature Chemistry* **3**: 954 - 962.

To run RNAstructure with bootstrapping, we use this command:

```matlab
[structure_pred, bpp_pred] = rna_structure(sequence, d_1D, offset, seqpos, d_2D, 100, 0);
```

The arguments are described in `help rna_structure`.

> You can feed it pseudo-free energy bonus of **1D** data, or **2D** data, or both. Make sure the dimensions of `sequence` match with `seqpos`, and `d_1D` or `d_2D`.

> You can change the number of bootstrap samplings (100 in the code above).

> You can choose which RNAstructure program to run, `Fold` (0 in the code above, see [here](http://rna.urmc.rochester.edu/Text/Fold.html)) or `ShapeKnot` (change to 1, see [here](http://rna.urmc.rochester.edu/Text/ShapeKnots.html)). The latter allows prediction of pseudoknot (1 only in each `sequence`), but it's significantly slower.

Once finished, the `rna_structure()` function returns the following variables:

| Variable | Type | Description |
| --- | --- | --- |
| `structure` | _1xS str_ | The predicted secondary strcture in _doc-bracket_ notation. |
| `bpp` | _SxS doubble_ | The base-pairing probability matrix. The percentage of each base-pair is calculated across all bootstrapping runs. |
| `SHAPE_out` | _1xS double_ | **1D** reactivity filtered. | 

We will demonstrate how to visualize the results in _next_ step.

<hr/>

Here is an example script for running RNAstructure with different inputs:

```matlab
% Prediction with no data, only thermodynamic parameters
% No need to bootstrap since there is no data to sample
[structure_NA, bpp_NA] = rna_structure(sequence, [], offset, seqpos_out, [], 0);

% Run Fold with 100x bootstrap on 1D SHAPE data
[structure_1D_Fold_SHAPE_minus, bpp_1D_Fold_SHAPE_minus] = rna_structure(sequence, d_SHAPE_minus, offset, seqpos_out, [], 100, 0);
[structure_1D_Fold_SHAPE_plus, bpp_1D_Fold_SHAPE_plus] = rna_structure(sequence, d_SHAPE_plus, offset, seqpos_out, [], 100, 0);

% Run ShapeKnot with 100x bootstrap on 1D SHAPE data
[structure_1D_Spkt_SHAPE_minus, bpp_1D_Spkt_SHAPE_minus] = rna_structure(sequence, d_SHAPE_minus, offset, seqpos_out, [], 100, 1);
[structure_1D_Spkt_SHAPE_plus, bpp_1D_Spkt_SHAPE_plus] = rna_structure(sequence, d_SHAPE_plus, offset, seqpos_out, [], 100, 1);

% Run Fold with 100x bootstrap on 2D SHAPE data
[structure_2D_Fold_SHAPE, bpp_2D_Fold_SHAPE] = rna_structure(sequence, [], offset, seqpos, Z, 100, 0);
% Run ShapeKnot with 100x bootstrap on 2D SHAPE data
[structure_2D_Spkt_SHAPE, bpp_2D_Spkt_SHAPE] = rna_structure(sequence, [], offset, seqpos, Z, 100, 1);
```

> Make sure you have an idea of the time the `ShapeKnot` run takes. Always run `ShapeKnot` with 0 bootstrap, and time it with `tic` and `toc`. Your _MATLAB_ do not respond to other operations while running `rna_structure()` (or any command).

> If 100x bootstrap for `ShapeKnot` takes too long (hours), you may consider run it overnight, or move to a cluster.

> Save the results of different runs to different variables to prevent overwriting each other.

You can also run with **1D** and **2D** data together:

```matlab
% Run ShapeKnot with 100x bootstrap on both 1D and 2D SHAPE data
[structure_1D2D_Fold_SHAPE_plus, bpp_1D2D_Fold_SHAPE_plus] = rna_structure(sequence, d_SHAPE_plus, offset, seqpos_out, Z, 100, 0);
[structure_1D2D_Spkt_SHAPE_plus, bpp_1D2D_Spkt_SHAPE_plus] = rna_structure(sequence, d_SHAPE_plus, offset, seqpos_out, Z, 100, 1);
```

Additionally, if the _Z-score_ looks noisy, filtering it would be better:

```matlab
Z_cutoff_mean = Z;
for i = 1:size(Z_cutoff_mean, 1);
    Z_cutoff_mean(i, Z_cutoff_mean(i, :) >= mean(Z_cutoff_mean(i, :))) = 0;
end;

Z_cutoff_1std = Z;
for i = 1:size(Z_cutoff_1std, 1);
    Z_cutoff_1std(i, Z_cutoff_1std(i, :) >= -std(Z_cutoff_1std(i, :)) + mean(Z_cutoff_1std(i, :))) = 0;
end;
```

The above code filters the _Z-score_ by the mean of each column (`seqpos`, not `mutpos`), or by 1 standard deviation from the mean. You can run `rna_structure()` with the filtered _Z-score_ and compare the results.


