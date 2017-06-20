---
permalink: /HiTRACE/tutorial/practice/
level: 2
---

# More Practice

We have prepared 12 datasets (1D and 2D) for more practice of manual Sequence Assignment ([Step #4](../step_4/)). They are previous data collected and annotated by experts from our lab. The expert assignments are included in the _.mat_ workspace files.

To practice your skills, you need to do the sequence assignment on your own, and then compare your results to our 'standarad' answers. You may want to track down differences, and learn through this experience how to adjust them. This serves well for gaining experience on scenarios of common mistakes and how to fix them.


## Instructions

- Download the additional files provided from this [link](https://rmdb.stanford.edu/site_data/HiTRACE_more_practice.zip).

- Unpack the _.zip_ file, and open *MATLAB* in that folder.

- Selectively load results from the provided _.mat_ workspace, to get it started. For example,

```matlab
load('practice_1D_more_1.mat', 'd_align', 'd_ref_align', 'ylimit');
```

> This is because we did not include the raw CE trace files. Thus, the `quick_look()` step is skipped for these practices, and you should resume from [Step #2](../step_2/). 

> The `d_align` variable holds the essential data from `quick_look()` ([Step #1](../step_1/)). The above command loads it, among `d_ref_align` and `ylimit` from the _.mat_ file.

- Run the following command so that you can repeat the Further Alignment ([Step #2](../step_2/)):

```matlab
d_align = d_align_before_more_alignment;
```

> This is because the expert _.mat_ result already have gone through the entire script, overwrote `d_align` with `d_align_dp_fine`. For datasets that no additional alignment were performed (see corresponding _.m_ scripts), ignore this.

- Follow the provided _.m_ script files to the Sequence Assignment ([Step #4](../step_4/)), and give your best shot!

- Save your workspace to a **different**{: style="color:#ff5c2b;"} _.mat_ file.

> Do not overwrite the downloaded _.mat_ files.

- You can then compare your assignment vs. our experts, by either switching between the _.mat_ files by using `load` and `clear`. Or, take advantage of the `print_xsel_split()` command to compare assignments side-by-side on papers!
