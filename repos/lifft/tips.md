---
permalink: /LIFFT/tips/
level: 2
prev: /LIFFT/docs/
next: /LIFFT/
---

## Tips and troubleshooting for LIFFT 

### Hanging & errors
* The first time you run LIFFT, you may see it hanging with a message like `Starting parallel pool (parpool) using the 'local' profile ...`. Just wait, and it won't hang the next time.  

* If you see an error related to `parfor` or similar, that's due to changes in the parallelization toolbox in different MATLAB versions. You can go into the `LIFFT.m` function, and comment out the `parfor` block in favor of the `for` block. Please send a bug report to us if that happens.


### Tips for setting input parameters

* If your data involve a fitting parameter that is an equilibrium constant or a concentration (e.g. a dissociation constant), you should space out its input parameters logarithmically, like `p1 = 10.^[-2:0.1:2];`.  If the fitting parameters is an energy, enthalpy, melting temperature, or exponent (like a Hill exponent), input the parameters linearly: `p1 = [30:0.5:80];`.
* 
* If you see problems with NaN showing up in data (or plots not showing up at all), that's often due to use of thermodynamic parameters that lead to undefined 'fraction folded' values, e.g., negative numbers for estimated binding affinities. Adjust the input values for the input thermodynamic parameters. For Hill fits, do not use 0.0 as one of the input Hill coefficients.  
* If the errors on the fit parameters are not being computed you need to expand the range of input parameters around the best fit value.

* If you see the fits do not appear to be going through the points cleanly that might be because some residues in your input data are reporting on a different transition. You can remove these residues in your `whichres` input field to `lifft.m`.

* Some fits can be poor because LIFFT, by default, assumes that the typical error at each residue is > 10%. That level of uncertainty is often the case for chemical mapping, but for optical melts with UV absorbance readout, the error can be much less. In that case, set `min_frac_error` to be lower, e.g. 0.01. (by default LIFFT uses 0.01 for `melt_with_linear_baseline` runs). 

* If your log-posterior plots look 'choppy', make the spacing of your input parameters `param1` and `param2` finer. For example, if you had set `p1 = 10.^[-2:0.5:2];`, now set it to `p1 = 10.^[-2:0.1:2];`.


* As of 2015, LIFFT assumes by default that the data start almost totally in one state and go to another. E.g., almost fully folded to almost fully unfolded. This is assumes as a 'baseline prior' favoring 'fraction folded' near 0 and 1  at beginning and end, respectively. If you don't want to use this assumption, you'll have to go into the script `do_new_likelihood_fit.m` and find the line `BASELINE_PRIOR = 1`. Change it to `BASELINE_PRIOR = 0`.  

### Normalization
* LIFFT can try to run a prenormalization ('centralize') on the data based on identifying residues that appear to change the least. If you'd like to try this, set the input `do_centralize` to 1.  
* If you want to totally turn off lane normalization during the fit, set `do_lane_normalization` to 0.  

<hr/>

* Previous: [Examples](/LIFFT/examples/)
* Back up to LIFFT: [LIFFT](/LIFFT/)

<hr/>
Developed by **Das lab**, _Leland Stanford Junior University_.

Docs updated by [**Rhiju Das**](https://github.com/rhiju), *March 2018*.



