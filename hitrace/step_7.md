---
layout: docs
permalink: /hitrace/tutorial/step_7/
root: /hitrace/
prev: step_6/
next: step_8/

title: HiTRACE
description: "<u>Hi</u>gh-<u>T</u>hroughput <u>R</u>obust <u>A</u>nalysis for <u>C</u>apillary <u>E</u>lectrophoresis"
repo: hitrace/hitrace
author: Siqi Tian
---

# Step 7: Save your Work _<small>(optional)</small>_

<br/>

### Save Figures for Notebooks

Saving analysis figures for future reference is good in the long term. Most intermediate functions of **HiTRACE** pipeline generates figures. For example, `quick_look()` automatically saves 5 figures to `Figures/` folder. For the ones that do not do so already, use command `print_save_figure()`:

```matlab
print_save_figure(gcf, 'fig_name', './');
```

It saves the current figure (`gcf`) to a **.eps** file in the current directory (`./`). Another useful function for resizing figure to a _letter_ paper size is `set_print_page()`.

<hr/>

### Multi-Page Print-Outs

It is rewarding to archive your sequence assignment since you spent so much time on it! **HiTRACE** provides a graphic function for figures like the [overview](/hitrace/res/pfl_1D_xsel.pdf):

```matlab
labels = data_types;
for i = 1:length(labels) - 8;
    if i <= 8;
        if mod(i - 1, 8) < 4;
            labels{i} = [labels{i}, ' (-)'];
        else
            labels{i} = [labels{i}, ' (+)'];
        end;
    else
        if mod(i - 9, 16) < 8;
            labels{i} = [labels{i}, ' (-)'];
        else
            labels{i} = [labels{i}, ' (+)'];
        end;
    end;
end;

print_xsel_split(d_align, xsel(2:end), seqpos_out, sequence, offset, area_pred, labels, ...
    [3 0 0 50 75 100 4 8 52 0 8 56], [0 1 0 1 1], ...
    {'RNA Puzzle #13: ZMP Aptamer', '', '', 'T47', 'May 2015'}, [25 15 9 8 11 1 1 2]);
```

The above code first prepares the `labels` which includes `'(-)'` and `'(+)'` for ligand conditions. The function `print_xsel_split()` saves multiple **.eps** files. 

> `xsel(2:end)` gives all the band positions. The first value in `xsel`, which is the full-length extended band, is excluded since it does not correspond to any nucleotide position in `sequence`.

> The arguments on _second_ and _third_ lines are totally optional. It offers finer adjustments on the image, borders, and texts. Checkout `help print_xsel_split` for detail specs.

[![print_xsel_split Figure 1](/hitrace/res/pfl_1D_seq_1.png "print_xsel_split Figure 1"){: .half}](/hitrace/res/pfl_1D_seq_1.png)
[![print_xsel_split Figure 2](/hitrace/res/pfl_1D_seq_2.png "print_xsel_split Figure 2"){: .half}](/hitrace/res/pfl_1D_seq_2.png)
[![print_xsel_split Figure 3](/hitrace/res/pfl_1D_seq_3.png "print_xsel_split Figure 3"){: .half}](/hitrace/res/pfl_1D_seq_3.png)
{: .center}

For the **2D** data, we often need to find interesting features by eye, e.g. to discover mutants that perturb a certain region. This also requires printing the entire data (`d_align`) larger than a single page. We have a command to do this:

```matlab
d_align(:, 56) = 0;

print_CE_split(d_align, d_rdat, [], [], xsel, [], [], area_pred, ...
    [2 2], [1 0 1 1 1 1 1 0 1 1 1], ...
    {'', 'print_CE_split_output', 'SHAPE', 'T47', 'May 2015'});
```

Similar to `print_xsel_split()`, the command `print_CE_split()` takes a lot of options too. Note that you need an _RDAT_ object `d_rdat` before calling this function. Saving _RDAT_ files is explained in [**Step #8**](../step_8/). We blanked the bad lane for print-out here.

[![print_CE_split Figure 1](/hitrace/res/pfl_2D_seq_1.png "print_CE_split Figure 1"){: .half}](/hitrace/res/pfl_2D_seq_1.png)
[![print_CE_split Figure 3](/hitrace/res/pfl_2D_seq_3.png "print_CE_split Figure 3"){: .half}](/hitrace/res/pfl_2D_seq_3.png)
[![print_CE_split Figure 2](/hitrace/res/pfl_2D_seq_2.png "print_CE_split Figure 2"){: .half}](/hitrace/res/pfl_2D_seq_2.png)
[![print_CE_split Figure 4](/hitrace/res/pfl_2D_seq_4.png "print_CE_split Figure 4"){: .half}](/hitrace/res/pfl_2D_seq_4.png)
{: .center}

Now you can splice them together into one giant print-out!

> Cut the _right_ margin for columns that are **NOT** the last (_right_) column.

> Cut the _bottom_ margin for rows that are **NOT** the last (_bottom_) row.

<hr/>

### Data Visualization matters!

Good data visualization assists data interpretation greatly. Here we briefly show some of the ways to plot the reactivity data and make comparisons.

> Familiarize with built-in functions like `plot()`, `errorbar()`, `scatter()`, `bar()`, `image()`, `colormap()`, `subplot()`, `axis()`, `legend()`, `title()`, etc.

From time to time, you may need to show the data in heatmap style. How to make a figure that is like what we have seen in `quick_look()`? Here is a quick example:

```matlab
image(d_align(501:3000, :) * 20);
colormap(1 - gray);
axis off;

make_lines;
make_lines(0:2:64, 'b', 2);
make_lines(0:8:56, 'r', 2);
make_lines(12:8:56, 'k', 2);
```

It makes an image for a part of `d_align` in black/white heatmap, and draw lines to separate lanes.

> We used `* 20` to adujst the darkness of the image. This number is not fixed. Try several to achieve the best contrast. `colormap(1 - gray)` defines the black/white color scheme.

> The **HiTRACE** package includes a handy function `make_lines()` that can make vertical lines with styles. Also check out `make_lines_horizontal()`.

[![Data Visualization Figure](/hitrace/res/pfl_1D_vis_ce.png "[Data Visualization Figure"){: .full}](/hitrace/res/pfl_1D_vis_ce.png)
{: .center}

For or **1D** reactivity data, since there are replicates for each modifier profile, we would recommend checking consistency of those first. The first 8 lanes after 2 _nomod_ are DMS, and we can plot those 4 **(-)** ligand lanes together with:

```matlab
plot(normalized_reactivity(:, 3:6))
```

We can see the first 2 are in good agreement; so are the last 2. But they do not agree with each other. In our experiment, 2 different modifier concentration were tried. And in this case, we think the first condition (e.g. DMS _1.0%_) is better.

So now we average each pair of 2 lanes, and take the higher concentration modifier condition of each modifier as the final reactivity:

```matlab
d_final = [ ...
    mean(normalized_reactivity(:, 3:4), 2), ...
    mean(normalized_reactivity(:, 5:6), 2), ...
    mean(normalized_reactivity(:, 7:8), 2), ...
    mean(normalized_reactivity(:, 9:10), 2), ...
    mean(normalized_reactivity(:, 11:12), 2), ...
    mean(normalized_reactivity(:, 13:14), 2), ...
    mean(normalized_reactivity(:, 15:16), 2), ...
    mean(normalized_reactivity(:, 17:18), 2), ...
    mean(normalized_reactivity(:, 19:20), 2), ...
    mean(normalized_reactivity(:, 21:22), 2), ...
    mean(normalized_reactivity(:, 23:24), 2), ...
    mean(normalized_reactivity(:, 25:26), 2), ...
];
da_final = [ ...
    max([std(normalized_reactivity(:, 3:4), 0, 2), mean(normalized_error(:, 3:4), 2)], [], 2), ...
    max([std(normalized_reactivity(:, 5:6), 0, 2), mean(normalized_error(:, 5:6), 2)], [], 2), ...
    max([std(normalized_reactivity(:, 7:8), 0, 2), mean(normalized_error(:, 7:8), 2)], [], 2), ...
    max([std(normalized_reactivity(:, 9:10), 0, 2), mean(normalized_error(:, 9:10), 2)], [], 2), ...
    max([std(normalized_reactivity(:, 11:12), 0, 2), mean(normalized_error(:, 11:12), 2)], [], 2), ...
    max([std(normalized_reactivity(:, 13:14), 0, 2), mean(normalized_error(:, 13:14), 2)], [], 2), ...
    max([std(normalized_reactivity(:, 15:16), 0, 2), mean(normalized_error(:, 15:16), 2)], [], 2), ...
    max([std(normalized_reactivity(:, 17:18), 0, 2), mean(normalized_error(:, 17:18), 2)], [], 2), ...
    max([std(normalized_reactivity(:, 19:20), 0, 2), mean(normalized_error(:, 19:20), 2)], [], 2), ...
    max([std(normalized_reactivity(:, 21:22), 0, 2), mean(normalized_error(:, 21:22), 2)], [], 2), ...
    max([std(normalized_reactivity(:, 23:24), 0, 2), mean(normalized_error(:, 23:24), 2)], [], 2), ...
    max([std(normalized_reactivity(:, 25:26), 0, 2), mean(normalized_error(:, 25:26), 2)], [], 2), ...
];

d_DMS_minus = d_final(:, 1);
da_DMS_minus = da_final(:, 1);
d_DMS_plus = d_final(:, 3);
da_DMS_plus = da_final(:, 3);
d_CMCT_minus = d_final(:, 5);
da_CMCT_minus = da_final(:, 5);
d_CMCT_plus = d_final(:, 7);
da_CMCT_plus = da_final(:, 7);
d_SHAPE_minus = d_final(:, 9);
da_SHAPE_minus = da_final(:, 9);
d_SHAPE_plus = d_final(:, 11);
da_SHAPE_plus = da_final(:, 11);
```

For simplicity, we created variables (e.g. `d_DMS_minus`) to hold individual reactivity values. Now we can make a figure like this:

[![Data Visualization Figure](/hitrace/res/pfl_1D_vis_rx.png "[Data Visualization Figure"){: .full}](/hitrace/res/pfl_1D_vis_rx.png)
{: .center}

The code is here and we will break it down for you:

```matlab
figure();
set_print_page(gcf, 0);

subplot(3, 1, 1);
plot(seqpos_out, d_DMS_minus, 'b', 'linewidth', 2); hold on;
plot(seqpos_out, d_DMS_plus, 'r', 'linewidth', 2); hold on;
errorbar(seqpos_out, d_DMS_minus, da_DMS_minus, 'b'); hold on;
errorbar(seqpos_out, d_DMS_plus, da_DMS_plus, 'r'); hold on;
make_lines_horizontal(-0.5, 'k');
make_lines([min(seqpos_out):0, 72:(max(seqpos_out) + 20)] - 0.5, [0.4 0.4 0.4], 0.5, 1, 0);
make_lines(ref_peak - 0.5, 'y', 1.5, 1, 0);
axis([-25 100 -0.5 3.5]);
legend('(-) ZMP', '(+) 10 uM ZMP');
title('1D DMS', 'fontweight', 'bold', 'fontsize', 15);
set(gca, 'xgrid', 'off', 'ygrid', 'on');
set(gca, 'xtick', [seqpos_out, first_RT_nucleotide + 1:20], 'xticklabel', sequence', 'fontsize', 8);
make_lines([-20:20:100] - 0.5, 'k', 0.5, 0, 1);

subplot(3, 1, 2);
plot(seqpos_out, d_CMCT_minus, 'b', 'linewidth', 2); hold on;
plot(seqpos_out, d_CMCT_plus, 'r', 'linewidth', 2); hold on;
errorbar(seqpos_out, d_CMCT_minus, da_CMCT_minus, 'b'); hold on;
errorbar(seqpos_out, d_CMCT_plus, da_CMCT_plus, 'r'); hold on;
make_lines_horizontal(-0.5, 'k');
make_lines([min(seqpos_out):0, 72:(max(seqpos_out) + 20)] - 0.5, [0.4 0.4 0.4], 0.5, 1, 0);
make_lines(ref_peak - 0.5, 'y', 1.5, 1, 0);
axis([-25 100 -0.5 5]);
legend('(-) ZMP', '(+) 10 uM ZMP');
title('1D DMS', 'fontweight', 'bold', 'fontsize', 15);
set(gca, 'xgrid', 'off', 'ygrid', 'on');
set(gca, 'xtick', [seqpos_out, first_RT_nucleotide + 1:20], 'xticklabel', sequence', 'fontsize', 8);
make_lines([-20:20:100] - 0.5, 'k', 0.5, 0, 1);

subplot(3, 1, 3);
plot(seqpos_out, d_SHAPE_minus, 'b', 'linewidth', 2); hold on;
plot(seqpos_out, d_SHAPE_plus, 'r', 'linewidth', 2); hold on;
errorbar(seqpos_out, d_SHAPE_minus, da_SHAPE_minus, 'b'); hold on;
errorbar(seqpos_out, d_SHAPE_plus, da_SHAPE_plus, 'r'); hold on;
make_lines_horizontal(-0.5, 'k');
make_lines([min(seqpos_out):0, 72:(max(seqpos_out) + 20)] - 0.5, [0.4 0.4 0.4], 0.5, 1, 0);
make_lines(ref_peak - 0.5, 'y', 1.5, 1, 0);
axis([-25 100 -0.5 3]);
legend('(-) ZMP', '(+) 10 uM ZMP');
title('1D DMS', 'fontweight', 'bold', 'fontsize', 15);
set(gca, 'xgrid', 'off', 'ygrid', 'on');
set(gca, 'xtick', [seqpos_out, first_RT_nucleotide + 1:20], 'xticklabel', sequence', 'fontsize', 8);
make_lines([-20:20:100] - 0.5, 'k', 0.5, 0, 1);

print_save_figure(gcf, '1D_plot_compare', './');
```

To walk you through, the code draws 3 `subplot()` panels. For each panel, it:

* `plot()` the **(-)** and **(+)** reactivity in solid lines. And then add the `errorbar()`. 

> You need to `hold on` once for each panel, otherwise each `plot()` or `errorbar()` function will overwrite the figure.

* It draws _gray_ shadow lines for the 5&prime; and 3&prime; flanking sequences, and _yellow_ lines for the _GAGUA_ reference loops. Note that some of the numbers here are hard-coded.

* It limits the _x_-axis and _y_-axis window, then sets the legend, title, and _x_-axis tick labels with the `sequence`. Also it sets the grid options and _x_-axis grid at every 20 (manually).

