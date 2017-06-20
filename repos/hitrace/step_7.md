---
permalink: /HiTRACE/tutorial/step_7/
level: 2
prev: step_6/
next: step_8/
---

# Step 7: Error Estimates _<small>(for 1D data only)</small>_

<br/>

For or **1D** reactivity data, since there are replicates for each modifier profile, we would recommend checking consistency of those first. The first 8 lanes after 2 _nomod_ are DMS, and we can plot those 4 **(-)** ligand lanes together with:

```matlab
plot(normalized_reactivity(:, 3:6))
```

**HiTRACE** offers the function `average_data_filter_outliers()`, which takes traces and initial error estimates; figures out outlier points and even outlier traces; and then returns reasonable final values and error estimates:

```matlab
[d_DMS_minus, da_DMS_minus, flags] = average_data_filter_outliers( ...
    normalized_reactivity(:, 3:6), normalized_error(:, 3:6), [], seqpos_out, sequence, offset); 
```

> This step only concerns error estimates across **replicates**. If your experiment only involves one lane for each condition, you do not need to run this command. And use `normalized_error` directly instead.

[![average_data_filter_outliers Figure](/hitrace/res/pfl_1D_fig_err.png "average_data_filter_outliers Figure"){: .full}](/hitrace/res/pfl_1D_fig_err.png)
{: .center}

We can see the first 2 (blue &amp; green) are in good agreement; so are the last 2 (red &amp; magenta). But they do not agree with each other. In our experiment, 2 different modifier concentration were tried. And in this case, we think the first condition (e.g. DMS _1.0%_) is better.

```matlab
[d_DMS_minus, da_DMS_minus, flags] = average_data_filter_outliers( ...
    normalized_reactivity(:, 3:4), normalized_error(:, 3:4), [], seqpos_out, sequence, offset); 
[d_DMS_plus, da_DMS_plus, flags] = average_data_filter_outliers( ...
    normalized_reactivity(:, 7:8), normalized_error(:, 7:8), [], seqpos_out, sequence, offset); 

[d_CMCT_minus, da_CMCT_minus, flags] = average_data_filter_outliers( ...
    normalized_reactivity(:, 11:12), normalized_error(:, 11:12), [], seqpos_out, sequence, offset); 
[d_CMCT_plus, da_CMCT_plus, flags] = average_data_filter_outliers( ...
    normalized_reactivity(:, 15:16), normalized_error(:, 15:16), [], seqpos_out, sequence, offset); 

[d_SHAPE_minus, da_SHAPE_minus, flags] = average_data_filter_outliers( ...
    normalized_reactivity(:, 19:20), normalized_error(:, 19:20), [], seqpos_out, sequence, offset); 
[d_SHAPE_plus, da_SHAPE_plus, flags] = average_data_filter_outliers( ...
    normalized_reactivity(:, 23:24), normalized_error(:, 23:24), [], seqpos_out, sequence, offset); 
```

For simplicity, we created variables (e.g. `d_DMS_minus`) to hold individual reactivity values. We can now make a figure and evaluate the data (see [**Step #7**](../step_7/)).

[![Data Visualization Figure](/hitrace/res/pfl_1D_vis_rx.png "[Data Visualization Figure"){: .full}](/hitrace/res/pfl_1D_vis_rx.png)
{: .center}

Here are some checkpoints to go over:

* **_GAGUA_ Reference Loops Reactivity**: the nubmer of reactive nucleotides should meet the expectation based on the modifier. Also, it tests whether the _GAGUA_ pentaloop is formed properly.

> The **1D** example has good _GAGUA_ pentaloops, see the SHAPE profile for 5 reactive nucleotides and protected stems flanking the _GAGUA_. If the profile looks different, it may be your flanking sequence interferes with proper folding by interacting with the region of interest.

* **Attenuation**: the reactivity profile should be corrected for it. A good indicator is to compare the _GAGUA_ reference loops of both ends. They should be the same 'height' in the plot.

> The **1D** example here has attenuation issues. The CMCT profile is generally bad, while the DMS is still attenuation biased, and the SHAPE profile is better but not perfect.

* **Negative Values**: negative values are resulted from background subtraction where the _nomod_ trace has higher value than modifier. This is usually a result of strong reverse transcriptase stops.

> Trace back where the negative values are. If there is a strong _nomod_ background, it might be excusable. It could be due to degradation, or RNA activity (e.g. self-cleavage). A consecutive region of negative numbers 'flying-off' is a red flag. Slightly negative values (< 0.1) are no need to worry.

