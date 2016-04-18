---
layout: docs
permalink: /hitrace/tutorial/step_6/
root: /hitrace/
prev: step_5/
next: step_7/

title: HiTRACE
description: "<u>Hi</u>gh-<u>T</u>hroughput <u>R</u>obust <u>A</u>nalysis for <u>C</u>apillary <u>E</u>lectrophoresis"
repo: hitrace/hitrace
author: Siqi Tian
---

# Step 6: Data Corrections _<small>(for 1D data only)</small>_

<br/>

For **Mutate-and-Map** data, we can draw inferences from the _changes_ in the chemical mapping reactivities as mutations are carried out. Thus the _relative_ values are OK. However, for quantitative analysis, we need to correct for several factors arise from the experiment measurements:

* **Background Stops**: the reverse transcriptase has intrinsic stops along the sequence. You may see such sites in a _nomod_ profile. We need to subtract out these to estimate true chemical reactivities.

* **Signal Attenuation**: the reverse transcriptase terminates (is blocked) at the first modification site it encounters from the 3&prime; end. Thus, the number of cDNA fragments attenuates as the length gets longer. For a long RNA, it is easy to spot that the longer reverse transcription products will have attenuated intensity compared to shorter ones. We need to correct for such directional bias.

In principle, this could all be carried out accurately and analytically if we could measure the amount of unmodified product -- the very longest (full-length extended )band in the capillary trace. But under 'single hit conditions', this fully extended band typically saturates our fluorescence detector. And this leads to the next item:

* **Signal Saturation**: the fluorescence camera of the CE machine has a certain detection range. For signals that are beyond the maximum value, they cannot be measured accurately and thus appear plateaued. This is common for the full-length extended band of the gel since the majority of input RNA are unmodified under _single-hit_ kinetics. We dilute the same sample in order to retrieve the intensity of such peaks.

* **Normalization**: to scale up the final reactivity profile to a common standard so that reactivities from different experiment (e.g. different RNA) can be compared to each other. This is where we the _GAGUA_ reference hairpin comes to help.

<hr/>

**HiTRACE** offers a likelihood-based framework for estimating the scaling and attenuation correction factors. 

> An obsolete script `overmod_and_background_correct_logL()` was used to optimize the attenuation coefficient (by a grid search) and the scaling for the background (by linear programming) so as to best match your expectation. Please use `get_reactivities()` instead!

We first need to define some parameters:

```matlab
ref_segment = 'GAGUA';
ref_peak = get_ref_peak(sequence, ref_segment, offset);
```

It searches for _GAGUA_ sequence (which is the pentaloop of both reference hairpins at 5&prime; and 3&prime;) and records the indices of those residues into `ref_peak`.

Next, we define the standard deviation to use as a cutoff for saturation in `unsaturate()` step. We basically always use:

```matlab
sd_cutoff = 1.5;
```

Now we need to split the dataset into a _diluted_ half and a _saturated_ (_undiluted_) half. We exclude any ddNTP lanes since we are not interested in quantitating them. For the DMS, CMCT, and SHAPE profiles, recall from the layout [here](/hitrace/res/pfl_1D_xsel.pdf). We know that:

```matlab
saturated_idx = [9, 10, 13, 14, 17 ,18 ,21, 22, 25, 26, 29, 30, 33, 34, 37, 38, 41, 42, 45, 46, 49, 50, 53, 54];
diluted_idx = saturated_idx + 2;
```

For the _nomod_ lanes, we need to average them before running `get_reactivities()`. Since conditions of absence and presence of ligand should not be mixed together, we do:

```matlab
saturated_array_nomod = [mean(area_peak(:, 1:2), 2),  mean(area_peak(:, 5:6), 2)];
diluted_array_nomod = [mean(area_peak(:, 3:4), 2),  mean(area_peak(:, 7:8), 2)];
```

The above command averages lane 1 with 2 (_without_ ligand), 5 with 6 (_with_ ligand) for _saturated_ _nomod_ data; lane 3 with 4 (_without_ ligand), 7 with 8 (_with_ ligand) for _diluted_ _nomod_ data. Note the use of `mean()` by row. Now let's merge the _nomod_ data with all the other modifiers; same for errors:

```matlab
saturated_array = [saturated_array_nomod, area_peak(:, saturated_idx)];
diluted_array = [diluted_array_nomod, area_peak(:, diluted_idx)];

saturated_error = [ ...
    mean(darea_peak(:, 1:2), 2), ...
    mean(darea_peak(:, 5:6), 2),...
    darea_peak(:, saturated_idx), ...
];
diluted_error = [ ...
    mean(darea_peak(:, 3:4), 2), ...
    mean(darea_peak(:, 7:8), 2),...
    darea_peak(:, diluted_idx), ...
];
```

> The `saturated_array` should match `saturated_error` in column orders; same for `diluted_array` and `diluted_error`.

Lastly, we need to specify the background columns for background subtraction. In our `saturated_array` has the columns as: 

* _nomod (-)_, _nomod (+)_, DMS (-) x4, DMS (+) x4, CMCT (-) x4, CMCT (+) x4, SHAPE (-) x4, SHAPE (+) x4. 

* [**(-)** and **(+)** mark ligand condition.] 

All the **(-)** columns should be subtracted by _nomod (-)_ while all the **(+)** columns should be subtracted by _nomod (+)_. The column indices of _nomod (-)_ and _nomod (+)_ in `saturated_array` are 1 and 2, thus:

```matlab
bkg_col  = [1, 2, 1, 1, 1, 1, 2, 2, 2, 2, 1, 1, 1, 1, 2, 2, 2, 2, 1, 1, 1, 1, 2, 2, 2, 2];
```

Finally, we can kick off the quantitation with:

```matlab
[normalized_reactivity, normalized_error, seqpos_out] = get_reactivities( ...
    saturated_array, diluted_array, saturated_error, diluted_error, ...
    bkg_col, ref_peak, seqpos, [], data_types(saturated_idx), sequence, offset, sd_cutoff);
```

> The argument `data_types(saturated_idx)` provides information of modifier identity for the lanes in `saturated_array` and `diluted_array`. Recall the numbers of nucleotides reactive in _GAGUA_ to DMS, CMCT, and SHAPE are different. This information helps normalization step to scale up properly.

The run goes through the 4 processes, and waits you to continue between steps:

* **Unsaturation**

[![get_reactivities Figure Unsaturation](/hitrace/res/pfl_1D_rx_unsat.png "get_reactivities Figure (Unsaturation)"){: style="width:90%;"}](/hitrace/res/pfl_1D_rx_unsat.png)

The _saturated_ sample is on the _left_, _diluted_ sample (after scaling up to match _saturated_ sample) is in the _middle_, and the result after `unsaturate()` is on the _right_. The red lines show where a plateaued reactivity is found in _saturated_ sample (by comparing to scaled _diluted_ sample).

* **Attenuation Correction**

[![get_reactivities Figure Attenuation Correction](/hitrace/res/pfl_1D_rx_attcorr.png "get_reactivities Figure (Attenuation Correction)"){: style="width:90%;"}](/hitrace/res/pfl_1D_rx_attcorr.png)

The data is now plotted by `seqpos`: 5&prime; on the _top_. The attenuation (lighter from _bottom_ to _top_) is now corrected.

> After this step, the extra full-length extened band is removed.

* **Background Subtraction**

[![get_reactivities Figure Background Subtraction](/hitrace/res/pfl_1D_rx_bkgsub.png "get_reactivities Figure (Background Subtraction)"){: style="width:90%;"}](/hitrace/res/pfl_1D_rx_bkgsub.png)

After subtracting the background, the data now looks cleaner. Of course the _nomod_lanes are completely blank now.

* **Normalization**

[![get_reactivities Figure Normalization](/hitrace/res/pfl_1D_rx_norm.png "get_reactivities Figure (Normalization)"){: style="width:90%;"}](/hitrace/res/pfl_1D_rx_norm.png)

> Reactive residues in _GAGUA_ reference loops are scaled to reactivity of 1.0 on average.

> If no `ref_peak` is given, the normalized reactivites may have not been scaled correctly.

Once finished, the `get_reactivities()` command returns the following variables:

| Variable | Type | Description |
| --- | --- | --- |
| `normalized_reactivity` | _SxP double_ | Final reactivity profiles. _P_ is the number of columns in `saturated_array`. Note that the number of rows is now _S_ instead of _S+1_. |
| `normalized_error` | _SxP double_ | Error estimates for `normalized_reactivity` that are propagated. |
| `seqpos_out` | _1xS int_ | Numbers of sequence positions from 5&prime; to 3&prime; end. Note that is has the full-length extended band position removed compared to `seqpos`. |

<hr/>

Again, you do not need to process your **2D** dataset using this step!


