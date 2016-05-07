---
permalink: /RiboVis/docs/
level: 2
---

## Most Useful Commands

[![rr() Example Image](/repos/ribovis/res/rr.png "rr() Example Image"){: .right}](/repos/ribovis/res/rr.png)

* #### `rr()`, or `render_rna()`

> Rhiju's favorite coloring of RNA with 2&prime; OH as spheres, bases as filled rings, and backbone as cartoon ribbons, rainbow colored from 5&prime; to 3&prime;. No hydrogens, white background.

<br/>

[![rrs() Example Image](/repos/ribovis/res/rrs.png "rrs() Example Image"){: .right}](/repos/ribovis/res/rrs.png)

* #### `rrs()`, or `render_rna_sticks()`

> Rhiju's favorite coloring of RNA, showing all heavy atoms as sticks -- more detail than `rr()`.

<br/>
<br/>
<br/>

[![color_by_data() Example Image](/repos/ribovis/res/color_by_data.png "color_by_data() Example Image"){: .right}](/repos/ribovis/res/color_by_data.png)

* #### `color_by_data( filename [, offset = 0, min = 0, max = 1] )`

> Read in a text file with rows and color specified residue numbers by scalar values.

```
125 0.12
126 1.50
```

> Takes advantage of B-factor column and color by temperature function in pymol. 

> By default, coloring is scaled/offset based on lowest/highest scalar value. To specify the minimum and maximum values for coloring, enter a min and max value as shown above. For normalized chemical mapping reactivities, `min = 0` and `max = 1~1.5` usually works.

For instructions on coloring 3D models using analyzed reactivity data from **HiTRACE**, see instructions [here](/hitrace/tutorial/bonus_3d/).

[![rd() Example Image](/repos/ribovis/res/rd.png "rd() Example Image"){: .right}](/repos/ribovis/res/rd.png)

* #### `rd()`, or `render_molecules()`

> Rhiju's favorite coloring of proteins and generic molecules side chains are all-heavy-atom and colored CPK, backbone is rainbow cartoon from N to C terminus.

<br/>
<br/>
<br/>

[![loop_color() Example Image](/repos/ribovis/res/loop_color.png "loop_color() Example Image"){: .right}](/repos/ribovis/res/loop_color.png)

* #### `loop_color( start, end, native=None, zoom=False )`

> Used for rendering protein loop modeling puzzles. White in background, colored red/blue over loop.

<br/>

* #### `align_all( [ subset=[] ] )`

> Superimpose all open models onto the first one. This may not work well with selections.

<hr/>

## Additional Commands

[![rc() Example Image](/repos/ribovis/res/rc.png "rc() Example Image"){: .right}](/repos/ribovis/res/rc.png)


* #### `rc()`, or `render_cartoon()`

> Tube coloring for large RNA comparisons

<br/>
<br/>
<br/>
<br/>
<br/>

[![sa() Example Image](/repos/ribovis/res/sa.png "sa() Example Image"){: .right}](/repos/ribovis/res/sa.png)

* #### `sa( [intra=False, rainbow=True] )`, or `superimpose_all()`

> Superimpose all open models onto the first one. This may not work well with selections.
  
> Option `intra` can be set to `True` to `enable intra_fit()` first, for working with multi-state (nmr) pdbs. [Thanks to Kyle Beauchamp for this one]

* #### `chainbow()`

> Run chainbow on all molecules, one by one.

[![rx() Example Image](/repos/ribovis/res/rx.png "rx() Example Image"){: .right}](/repos/ribovis/res/rx.png)

* #### `rx()`, or `render_x()`

> Rhiju's favorite coloring of proteins, more details -- no cartoon; heavy backbone. Use for beta peptide visualization.

<br/>

[![rj() Example Image](/repos/ribovis/res/rj.png "rj() Example Image"){: .right}](/repos/ribovis/res/rj.png)

* #### `rj()`, or `render_rhiju()`

> Rhiju's residue-level favorite coloring of proteins non-polar side chains colored gray.

<br/>

* #### `rr2()`, `render_rna2()`

> Rhiju's favorite coloring of RNA, showing all heavy atoms as sticks -- more detail than `rr()`.


* #### `get_residue_colors( sele )`

> Get RGB color values associated with a selection. Useful if you want to exactly match coloring of 3D models with coloring in, say, a _MATLAB_ script.

* #### `spr()`, or `source_pymol_rhiju()`

> Load up these commands again after, say, an edit.

[![rb() Example Image](/repos/ribovis/res/rb.png "rb() Example Image"){: .right}](/repos/ribovis/res/rb.png)

* #### `rb()`

> Basic cartoon coloring

<br/>
<br/>
<br/>
<br/>
