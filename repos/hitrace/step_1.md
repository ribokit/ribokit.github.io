---
permalink: /HiTRACE/tutorial/step_1/
level: 2
prev: step_0/
next: step_2/
---

# Step 1: Load and Preview Data

<br/>

### If you have chemical mapping data on different RNA sequences, especially if they are not the same length, please separate data of each sequence into individual analyses.

As you can see in [**Step #3**](../step_3/) and [**Step #4**](../step_4/), you need to specify sequence information and annotate bands to match sequence. Thus, it only works for one input sequence.

<hr/>

In this tutorial, we will use the _pfl_ riboswitch data to walk you through the HiTRACE pipeline. _pfl_ riboswitch binds to ZMP (5-amino-4-imidazole carboxamide ribose-5′-monophosphate), and is described in detail by [Trausch _et al._ 2015](http://www.sciencedirect.com/science/article/pii/S1074552115002331) and [Ren _et al._ 2015](http://www.sciencedirect.com/science/article/pii/S0969212615002191). The data was originally collected in an [**RNA Puzzle**](http://ahsoka.u-strasbg.fr/rnapuzzles/) blind modeling contest. Thus, it is a great example on how to analyze (new) data.

The collected **1D** data contains conditions of _nomod_, SHAPE, DMS, CMCT, and all 4 ddNTP ladders. Data includes conditions of both in absence (_minus_) and in presence (_plus_) of the ligand. Each sample was run as both satuated (_sat_) and diluted (_dil_), which will be futher explained in [**Step #6**](../step_6/). An overview of the **1D** data is available [here](/hitrace/res/pfl_1D_xsel.pdf).

<hr/>

To load and preview data, we use the `quick_look()` command. It is a script that we use on daily basis to rapidly evaluate whether an experiment is successful. It also provides print-outs for keeping in notebooks.

First, let's define the data directories and lane ordering:

```matlab
filenames = { ...
    'pfl_1D_QC&CM_2015-05-02_1802', ...
    'pfl_1D_QC&CM_2015-05-02_1803', ...
    'pfl_1D_QC&CM_2015-05-02_1804', ...
    'pfl_1D_QC&CM_2015-05-02_1805', ...
};
ylimit = [2501, 6000];
reorder = [1:8, 17:64, 9, 13, 10, 14, 11, 15, 12, 16];
```

The `ylimit` variable defines the window of data time-series. When not specified (or as empty `[]`), `quick_look()` can make a best guess of the relevant time window. Usually, we run with `[]` first. If the resulting auto-selected `ylimit` is unsatisfactory, we adujst it manually and rerun.

The `reorder` variable defines the display order of data lanes. When not specified (or as empty `[]`), it follows the order of directories as defined in the `filenames`. Inside each directory, it sorts lanes according to a _96-wll plate_ layout by column, i.e. A01 - > B01 -> ... -> G01 -> H01 -> A02 -> ... -> H02 -> A03 -> ... -> H12. Note that the indices in `reorder` should not exceed the total number of **.ab1** files of all directories.

In this example, it reads in all ABI sequencer files (**.ab1**) from these 4 folders, crops to the time window, and reorders it in a way that the ddNTP ladder lanes are placed to the last. The names of **.ab1** files is explicit on the data content.

> Make sure you navigate to the working directory that contains the data directories (using `cd dir_name`). 

> We recommend keeping the _well_ prefixes in each **.ab1** filename. Please make sure that there is no _well_ name collision between files within the same directory. Each directory should hold no more than **96** lanes.

> Directory names should **NOT** end with a space. Otherwise it may cause ane error.

Now, you can run:

```matlab
[d_align, d_ref_align, ylimit, labels] = quick_look(filenames, ylimit, reorder);
```

It reads in the data, subtracts a constant offset from all the profiles, and normalizes to the mean signal intensity. It returns the following variables:

| Variable | Type | Description |
| --- | --- | --- |
| `d_align` | _MxN double_ | Final trace/data matrix of the signal channel (by default, _FAM_ channel). _M_ rows speficied by the `ylimit` time window; _N_ columns speficied by the `reorder` lanes ordering. |
| `d_ref_ailign` | _MxN double_ | Final trace/data matrix of the referene channel (by default, _ROX_ channel). |
| `ylimit` | _1x2 int_ | Auto-selected or manually specified `[ymin, ymax]` of time window. |
| `labels` | _1xN cell_ | Lane labels after reordering (extracted from **.ab1** filenames). |

You'll see several windows that show steps along the automated read-in and first-pass alignment. **Please DO NOT close figure windows before `quick_look()` finishes!** Otherwise you may see an error about saving figures to **.eps** files.

[![quick_look Figure 1](/hitrace/res/pfl_1D_fig_1.png "quick_look Figure 1"){: .half}](/hitrace/res/pfl_1D_fig_1.png)
{: .center}

### Figure 1: Time-series view of fluorescence profiles

The 4 channels are colored in <span style="color: #5496d7;">blue</span>, <span style="color: #03a9f4;">cyan</span>, <span style="color: #9fc906;">green</span>, and <span style="color: #f44336;">red</span>. Only the last 16 lanes are shown. In our standard setup, the signal channel (_FAM_) shows up in <span style="color: #5496d7;">blue</span>; and the reference channel (_ROX_) shows up in <span style="color: #f44336;">red</span>.

> The _ROX_ channel should appear as digital spikes. The ssDNA sizes of _ROX350_ ladder used is described [here](https://www.thermofisher.com/order/catalog/product/401735).

> The cyan and green channels should be mostly flat since we don't typically load anything with these colors.

> The _FAM_ channel should have a lot of peaks, while the peaks should be reasonably tall in the plot. Most of the peaks in the middle should not be so tall that appear plateaued. A plateaued peak is due to the sensitivity ceiling of the fluorescence camera. The full-length extended band (_right hand_) is usally very strong and thus plateaued. This is why we run diluted data as well and correct for saturation in [**Step #6**](../step_6/).

[![quick_look Figure 2](/hitrace/res/pfl_1D_fig_2.png "quick_look Figure 2"){: .full}](/hitrace/res/pfl_1D_fig_2.png)
{: .center}

### Figure 2: Raw traces

The signal channel and reference channel data are visualized as black/white heatmaps, side by side. These are raw data, as directly loaded from **.ab1** files.

> Check whether the `ylimit` is reasonable. None of the lanes should have their _top_ or _bottom_ truncated out. 

[![quick_look Figure 3](/hitrace/res/pfl_1D_fig_3.png "quick_look Figure 3"){: .half}](/hitrace/res/pfl_1D_fig_3.png)
{: .center}

### Figure 3: Intermediate traces after initial processing

The signal channel data visualized as heatmap. This is after profile alignment by groups, and intensity normalization.

> Usually, any imperfections at this step should be fixed in _**Figure 4**_.

[![quick_look Figure 4](/hitrace/res/pfl_1D_fig_4.png "quick_look Figure 4"){: .half}](/hitrace/res/pfl_1D_fig_4.png)
{: .center}

### Figure 4: Final traces after further processing

The signal channel data visualized as heatmap. This is after baseline subtraction, piece-wise-linear alignment based on reference channel, and local alignment refinement.

> This is the final trace that will carry on to downstream analysis. The alignment should be largely acceptable: the full-length extended band (_bottom_) should line up across all lanes since all samples are the same RNA. The lanes with similar property (e.g. same modifier) should have their signaure bands aligned to each other. The ddNTP ladders should be well-spaced, just like an old-fasion sequencing gel.

> There could be some "waviness" across lanes of similar profiles. This is more obvious in **Mutate-and-Map** experiments. [**Step 2**](../step_2/) takes care of such last refinement.

[![quick_look Figure 5](/hitrace/res/pfl_1D_fig_5.png "quick_look Figure 5"){: .half}](/hitrace/res/pfl_1D_fig_5.png)
{: .center}

### Figure 5: Final traces of reference channel

The reference channel data visualized as heatmap. This is after all processing, at the same stage as _**Figure 4**_. The reference channel is not used in any upcoming steps.

> The _ROX350_ ladders should line up very well across all lanes

If you need to turn off the baseline subtraction or alignment, you can do so by changing the input to `quick_look()`. You can also apply leakage correction, or select other color channels to define which channel is the signal or which is the reference. For more information on command arguments and returns, please refer to `help quick_look`.

<hr/>

As an example of **2D** data analysis, it is the same as **1D** for this step.

```matlab
filenames = {'pfl_2D_SHAPE_plus_409193'};
[d_align, d_ref_align, ylimit, labels] = quick_look(filenames, [], 1:72);
```

[![quick_look Figure 2](/hitrace/res/pfl_2D_fig_2.png "quick_look Figure 2"){: .full}](/hitrace/res/pfl_2D_fig_2.png)
{: .center}

[![quick_look Figure 1](/hitrace/res/pfl_2D_fig_1.png "quick_look Figure 1"){: .half}](/hitrace/res/pfl_2D_fig_1.png)
[![quick_look Figure 3](/hitrace/res/pfl_2D_fig_3.png "quick_look Figure 3"){: .half}](/hitrace/res/pfl_2D_fig_3.png)
[![quick_look Figure 4](/hitrace/res/pfl_2D_fig_4.png "quick_look Figure 4"){: .half}](/hitrace/res/pfl_2D_fig_4.png)
[![quick_look Figure 5](/hitrace/res/pfl_2D_fig_5.png "quick_look Figure 5"){: .half}](/hitrace/res/pfl_2D_fig_5.png)
{: .center}

It is obvious that there is a _bad_ lane showing no data in _**Figure 2**_. The pattern for that lane in _**Figure 3**_ and _**Figure 4**_ is an artifact/amplification of normalization. We will exclude this lane in the downstream analysis.

<hr/>

## Troubleshooting

Certain common problems you may face:

* ### Final traces not aligned well.

So your _**Figure 4**_ looks more like the _**Figure 3**_ in the **1D** example. Check your _**Figure 5**_:

> If the reference channel is not aligned well, it could be the `ylimit`'s fault. Adjust the `ylimit` paying extra attention to the reference channel. Sometimes when certain lanes got cropped out of a _ROX_ band, the alignment algorithm is confused by the mismatch of numbers of reference ladders. Enlarge your `ymax` and give it another try.

If no luck, check _**Figure 2**_ instead:

> Although not aligned at all, all lanes should be roughly the same migration rate, i.e. the length of _top_ to _bottom_ of signals should be the same. If a lane is compressed or stretched (possibly due to buffer or voltage variations), `quick_look()` might not be able to rescue it.

* ### Error on saving figure.

Please `close all` windows and retry. Make sure you don't switch between _MATLAB_ windows, or close any figure windows while `quick_look()` is running. It saves the figures in the end, and a closed figure window will cause error.
