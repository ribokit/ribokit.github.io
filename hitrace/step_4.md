---
layout: docs
permalink: /hitrace/tutorial/step_4/
prev: step_3/
next: step_5/

title: HiTRACE
description: "<u>Hi</u>gh-<u>T</u>hroughput <u>R</u>obust <u>A</u>nalysis for <u>C</u>apillary <u>E</u>lectrophoresis"
repo: hitrace/hitrace
author: Siqi Tian
---

# Step 4: Sequence Assignment

<br/>

Now we're ready for the sequence assignment. The positions of the various bands are stored in a vector `xsel`. Let's initiate it with empty `[]`:

```matlab
xsel = []; clf;
```

> **Only run this line at first time!** It creates an empty `xsel`. If a variable named `xsel` already exists in the current workspace, its content will be erased. Do not run this line when you are revisiting this step!

> `clf` clears a figure. It makes sure the interactive interface will inherit a full-size figure window.

Then let's start the interactive annotation:

```matlab
[xsel, seqpos, area_pred] = annotate_sequence(d_align, xsel, sequence, offset, data_types, first_RT_nucleotide, structure);
```

