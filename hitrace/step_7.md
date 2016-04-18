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




### Data Visualization matters!

Good data visualization assists data interpretation greatly. 

print_xsel
print_ce

image
1d plots
