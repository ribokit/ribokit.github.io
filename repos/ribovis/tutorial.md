---
permalink: /HiTRACE/tutorial/bonus_3d/
level: 2
prev: bonus_2d/
---

# Color 3D Model

<br/>

Now that you have quantified chemical mapping data, you may find it helpful to visualize your reactivities on 3D models of your RNA of interest. This page lays out the steps for coloring a 3D model of an RNA in _PyMol_ with quantified reactivities obtained from chemical mapping or hydroxyl radical footprinting experiments.

A brief walkthrough is included at the end for coloring a single model of a SAM-I/IV riboswitch with hydroxyl radical footprinting reactivities in the presence of 10mM SAM ligand.

<hr/>

## Preparations

* #### An RNA model of interest in _PDB_ format

* #### Quantified reactivity data in a _MATLAB_ variable

* #### Have **HiTRCE** and `pymol_daslab` installed (see [here](/pymol_daslab/))

* _(Optional)_ [loadDir.pml](http://www.pymolwiki.org/index.php/LoadDir), a useful command for coloring a set of **.pdb** files at once

<hr/>

## Create text files for reactivity

First, we will convert the quantified reactivity data in your _MATLAB_ variable into a set of text files with two columns separated by spaces. The first column will contain the residue number, while the second column will contain the reactivity measurement at that residue.

Use the script `data_for_3d_color()` in _MATLAB_ (from **HiTRACE**) to convert a data array to text files that will be read by the `color_by_data()` function in _PyMol_. The user must initially input the data array, as well as the range of measurements in the array that correspond to the sequence in the _PDB_ file, excluding any 5&prime; and 3&prime; flanking sequences.

When run, `data_for_3d_color()` prompts the user for the names of the conditions corresponding to each column (= lane) of data and creates the folder `'Data for 3d color'` containing text files named after the user-defined inputs.

Example:

```bash
>> data_for_3d_color(data, [24:96]);
Condition: DMS
Condition: SHAPE
>>
```

The folder 'Data for 3d color' will be created containing 'DMS.txt' and 'SHAPE.txt'.

<hr/>

## Color 3D models by reactivity

Now that you have **.txt** files with reactivities and sequence positions, it’s time to color some 3D models!

* Open _Pymol_ and run:

```python
run pymol_daslab.py
```

Or have it setup automatically (see [here](https://ribokit.github.io/RiboVis#installation)).

* Load _PDB_ of interest:

```python
load filename.pdb
```

[![load Figure](/hitrace/res/sam_3D_1.png "load Figure"){: .half}](/hitrace/res/sam_3D_1.png)
{: .center}

> If you would like to read in a whole directory of **.pdb** files at once, you may run _loadDir.pml_, which defines the command `loadDir()`. Example:

```python
loadDir dir, *.pdb
reset
```

It load all **.pdb** files in directory `dir` and resets view of molecule. You can add multiple sets of **.pdb**’s by changing the directory name and rerunning the command.

* _(Optional)_ Set Options:

Then, if desired, set the background color and other visualization options (filled rings, cartoon backbone, etc.). Commands in `RiboVis` provide preset visualization schemes (detailed [here](https://ribokit.github.io/RiboVis/docs/)):

```python
rr()
```

[![rr Figure](/hitrace/res/sam_3D_2.png "rr Figure"){: .half}](/hitrace/res/sam_3D_2.png)
{: .center}

* **Color the structure by data**

```python
color_by_data('filename.txt')
```

[![color_by_data Figure](/hitrace/res/sam_3D_3.png "color_by_data Figure"){: .half}](/hitrace/res/sam_3D_3.png)
{: .center}

> If the coloring scheme is improperly scaled (e.g. structure is all red or all blue), you can set minimum and maximum reactivity values to fix scaling:

```python
color_by_data('filename.txt', 0, 0, 1)
```

Last, make sure to save your _PyMol_ session as a **.pse** file!

