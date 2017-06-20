---
permalink: /HiTRACE/tutorial/step_3/
level: 2
prev: step_2/
next: step_4/
---

# Step 3: Parameter Input

<br/>

Now we have the profiles in reasonable aligned from store in the matrix `d_align`, we need to assign which bands correspond to which sequence. We need to provide more information on the experiment before proceeding to [**Step #4**](../step_4/).

First we declare the `sequence`, whose letters will show up as we do the band annotation:

```matlab
sequence = 'GGAGACCTCGAGTAGAGGTCAAAAGGGTCGTGACTGGCGAACAGGTGGGAAACCACCGGGGAGCGACCCCGGCATCGATAGCCGCCCGCCTGGGCAAACAACTCGAGTAGAGTTGACAACAAAGAAACAACAACAACAAC';
sequence = strrep(sequence, 'T', 'U');
```
> Note that we repalce _'T'_ to _'U'_ as RNA sequence.

Next, we declare the `structure`, represented in _dot-bracket_ notation. It is recommended to use a **reference/crystallographic secondary**{: style="color:#ff5c2b;"} structure, or any hypothesis you are testing. **Use empty `''` instead if you don't have a clue.** We do not recommend using untested predictions.

```matlab
structure = '...((((((.....))))))....(((((((....[[[[....(((((....))))).....)))))))...........(((..]]]]...)))...((((((.....)))))).........................';
```

> Make sure `structure` is the same length as `sequence`. Use `[]` for pseudoknot base-pairs.

Next, we should register any information that we have about features or data that might show up in individual lanes. This requires creating a variable `data_types` which is a _cell_ of _string_s, one label for each profile/lane. 

In our example **1D** data, the first 8 lanes are _nomod_ (regardless of ligand or dilution), followed by 16 of DMS, CMCT, and SHAPE in order. Last, it has 2 lanes of each ddNTPs (_A_, _T_, _C_, _G_). The following code declares the `data_types` with help with built-in function `repmat()`.

```matlab
data_types = [ ...
    repmat({'nomod'}, 1, 8), repmat({'DMS'}, 1, 16), repmat({'CMCT'}, 1, 16), repmat({'SHAPE'}, 1, 16), ...
    repmat({'ddATP'}, 1, 2), repmat({'ddTTP'}, 1, 2), repmat({'ddCTP'}, 1, 2), repmat({'ddGTP'}, 1, 2), ...
];
```

Next, we need to play with some numbers. The first one is `offset`. This is used for adjusting sequence numbers for two reasons:

* Offset for the 5&prime; flanking sequence.

* Follow conventional numbering.

In our example **1D** data, we added 24 nucleotides on the 5&prime; end (_GGAGACCTCGAGTAGAGGTCAAAA_) before our region of interest (ROI) _GGGTCG..._. We would like the first _G_ in ROI to be numbered as 1. Thus, the `offset` is:

```matlab
% offset = - length_of_5_flanking_region + N_first_nt_ROI_should_be - 1
offset = -24;
first_RT_nucleotide = length(sequence) - 20 + offset;
```

Lastly, we need to describe where the reverse transcription primer was bound. **HiTRACE** accepts a number describing the first nucleotide that was reverse transcribed. In this case, its the nucleotide 20 residues from the end (the primer is 20 nucleotides long, binding to **Tail 2** sequence _AAAGAAACAACAACAACAAC_).

> Note that `first_RT_nucleotide` has number that is based on `offset`.

> The `offset` variable only matters for display. It converts the 'natural' numbering of nucleotides in the physical RNA `sequence` to the traditional numbering you are comfortable of (e.g. set first nucleotide of you ROI as 1, or other numbers if your RNA is a small part of a larger sequence).

> The `20` in `first_RT_nucleotide` correspond the length of pairing region between **Tail 2** and the reverse transcription primer. If you followed the guidelines in designing your RNA construct, you do not need to change this number.

<hr/>

As an example of **2D** data analysis, it is similar as **1D** for this step **except for `data_types`**.

```matlab
sequence = 'GGAGACCTCGAGTAGAGGTCAAAAGGGTCGTGACTGGCGAACAGGTGGGAAACCACCGGGGAGCGACCCCGGCATCGATAGCCGCCCGCCTGGGCAAACAACTCGAGTAGAGTTGACAACAAAGAAACAACAACAACAAC';
sequence = strrep(sequence, 'T', 'U');
structure = '...((((((.....))))))....(((((((....[[[[....(((((....))))).....)))))))...........(((..]]]]...)))...((((((.....)))))).........................';
offset = -24;
first_RT_nucleotide = length(sequence) - 20 + offset; 
```

For a **Mutate-and-Map** experiment, we have comprehensively created all single mutants for an RNA, its often helpful to have marks show up at the mutated positions, since there are typically obvious perturbations there. Thus, the modifier label is less important than the mutational positions (or `mutpos` historically, though no longer in use). Instead of repeating `'SHAPE'` 72 times for the **2D** dataset, we should specify as:

```matlab
data_types{1} = 'NaN';
for i = 2:72;
    data_types{i} = [num2str(i - 1)];
end;
```

> Note that `data_types` take _string_, not _number_. So use `num2str` to convert values.

> Use `'NaN'` for the first lane in **Mutate-and-Map** data (which is the wild-type).


