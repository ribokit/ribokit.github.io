---
permalink: /LIFFT/docs/
level: 2
prev: /LIFFT/
next: /LIFFT/examples
---

## Documentation for [LIFFT](../): What this is
Folding of biomolecules can be induced by cooling temperature, adding small molecule partners, or changing ionic conditions. 

Several techniques now exist to probe these transitions at different places on a molecule. For RNA in particular, chemical mapping measurements return data at each nucleotide of the molecule, as a function of folding condition: a 2D matrix. Spectroscopy approaches (NMR, fluorescence, absorbance) can also return data at multiple frequencies for a molecule undergoing a folding transition.

Learning from these data requires modeling them, which in turn requires defining a quantitative model and fitting thermodynamic parameters. These analyses require assumptions about normalization, which residues to fit, how to estimate errors, etc. which are not always explicitly defined.

LIFFT makes these fitting assumptions explicit through a Bayesian analysis, with thermodynamic relationships vs. temperature, ionic, or ligand condition based on commonly used forms (Hill fits, etc.). Errors at each position are inferred from the data themselves, so that positions that vary a lot actually get assigned a high error, while positions that cleanly follow the transition are given lower errors and dominate the fit. Also, the analysis does a grid search over parameter values and returns contour plots of the likelihood values. So its easy to assess if parameter uncertainties are correlated to each other, or are highly non-Gaussian.

Written originally by Rhiju Das, Stanford University. Original scripts written in 2008, continually expanded to present by Das Lab. 

See publications on [LIFFT](../) page for more information on mathematical form.

See instructions on [LIFFT](../) page for download and quick start.

<hr/>

## The `lifft` function

### Syntax of `lifft` MATLAB function
To get more detailed documentation, type `help lifft` in MATLAB. Here is a current example:

```
[ p1_best, p2_best, log_L, C_state, input_data_rescale, conc_fine, pred_fit_fine_rescale, input_data_renorm, pred_fit_fine  ] = lifft( input_data, conc, resnum, param1, param2, whichres, fit_type, C_state_in, plot_res, do_centralize, conc_fine, min_frac_error, do_lane_normalization, baseline_dev );   [ p1_best, p2_best, log_L, C_state, input_data_rescale, conc_fine, pred_fit_fine_rescale, input_data_renorm, pred_fit_fine  ] = lifft( input_data, conc, resnum, param1, param2, whichres, fit_type, C_state_in, plot_res, do_centralize, conc_fine, min_frac_error, do_lane_normalization, baseline_dev );
 
  lifft: Likelihood-informed Fits of Footprinting Titrations
 
  Optimizes lane normalizaton and calculates
   errors at each residue while doing a grid search over midpoints and apparent Hill coefficients.
 
   Inputs:
 
   input_data = matrix of input structure mapping data, approximately normalized (e.g., by mean intensity in each lane)
                  must have dimensions of (number of residues x number of lanes ).
   conc       = concentration of chemical in titration (e.g., [adenine], or [Mg2+] ), or temperature (in C, for melts).
   resnum     = your favorite numbering of residues  (if you give empty set [], you'll get 1:number of columns in input_data )
   param1     = parameter 1 values (e.g., concentrations) to search over. (Default: 10.^[-3.0 : 0.1 :3.0]).
   param2     = parameter 2 values (e.g., apparent Hill coefficients) to search over. (Default: param2 = [0.05:0.05:4] )
   whichres   = [optional!] just look at this subset of input residues. (Give empty set [] to look at all residues. )
   fit_type   = string specifying functional form to search: "hill", "double_exp", "one_two", "melt" ( default is "hill" )
 
   Less commonly used inputs...
   C_state_in = a 'target' set of values for footprinting data for each state. If not specified or [], no target set.
   plot_res   = which residues, if any, to make a 'nice' Hill plot with.  
   do_centralize  = pre-'normalize' the data based on assumption that some residues stay invariant during the titration (default = 0, i.e., false)
   conc_fine      = finely spaced concentrations to use when plotting. If not specified or [], use default.
   min_frac_error = minimum assumed relative error in points (default is 0.2, except defaults to 0.01 for melt_with_linear_baseline)
   do_lane_normalization = try to fit lane normalization for each parameter value. (default is 1, except defaults to 0 for melt_with_linear_baseline)
   baseline_dev = amount of deviation to allow for start & end fraction folded to deviate from 1 and 0 (default = 0.05)
 
  Outputs:
   p1_best = best fit for parameter 1 (e.g., K_d).
   p2_best = best fit for parameter 2 (e.g., hill coefficient).
   log_L   = matrix of log-likelihood values over input param1, param2.
   input_data_rescale = input_data over plot_res, rescaled from 0 to 1 (as shows up in plot_res plot)
   conc_fine             = concentrations assumed in making a fine curve that goes through input_data_rescale
   pred_fit_fine_rescale = values from 0 to 1 in fine curve fit through input_data_rescale
   input_data_renorm     = all input_data, lane normalizations applied
   pred_fit_fine_renorm  = predicted data, lane normalizations applied
 
  (C) Das lab, Stanford University, 2008-2016,2018
```
If you want default values for any inputs, you can typically type in the empty set `[]` for the variable (see above).

<hr/>

### Available fitting functions
Several options are available in `scripts/fit_functions/`, each taking two thermodynamic parameters:  

* **hill** carries out standard Hill fits.  
Parameter 1 is midpoint concentration; parameter 2 is apparent Hill coefficient:

```
Frac folded = [ conc/K ]^n  / [ 1  +  (conc/K)^n ];
```

The usual caveats of using Hill forms apply. For Mg(2+) binding, see, e.g., [this review](https://daslab.stanford.edu/site_data/pub_pdf/2014_Lipfert_AnnRevBiochem.pdf).

* **one_two** is the binding isotherm for a molecule that binds up to 2 ligands:

```
X <--> X*L <--> X*2L
     K1       K2      

 K1 and K2 are dissociation constants for first and second ligand.

 f0 = 1         / [1 + conc/K1 + (conc/K1)(conc/K2)]
 f1 = (conc/K1) / [1 + conc/K1 + (conc/K1)(conc/K2)]
 f2 = (conc/K2) / [1 + conc/K1 + (conc/K1)(conc/K2)]
```

* **melt** is the fit to temperature-dependent melts, with melting temperature (Tm) and enthalpy change (delH)  as parameters.  


```
 Equilibrium between two states, K = 
            exp[ (delH/R) * ( 1/Tm - 1/T) ]

 Frac. folded, f = K/ (1 + K )

 Note: assumes no heat capacity difference
```

* **melt_dS_dH** is an alternative fit to temperature-dependent melts, with entropy change (delS) and enthalpy change (delH) as parameters -- it leads to extreme correlations in uncertainties between delH and delS ('artifactual' enthalpy-entropy compensation); the **melt** function above is recommended instead.

```
 Equilibrium between two states, K = 
            exp[ (1/R) * ( delS - delH/T) ]

 Frac. folded, f = K/ (1 + K )

 Note: assumes no heat capacity difference
```


* **melt_with_linear_baseline** is an expansion of **melt**.  
As in **melt**, states have populations 1-*f* and _f_, but this also outputs two other 'states' with fraction folded _T_\*(1-*f*) and _T_\*_f_, where _T_ is the temperature. This tricks LIFFT into also fitting a linear baseline for the folded and unfolded states.

* **double_exp** (for timecourses; not well tested)

```
f0 = 1
f1 = exp( -t/tau1)
f2 = exp( -t/tau2).
```
Note that _tau1_ and _tau2_ are observed time constants and do not directly correspond to microscopic rate constants. 
<hr/>


### How to output the plots

* The quickest way to output a plot that is editable in Illustrator is to print to a PostScript file: 
```
print( '-depsc2','yourfigurename.eps' );
```
* If you just want a quick PNG output for Word, Powerpoint, or Google Doc, try:
```
print( '-dpng','yourfigurename.png','-r300' );
```

* Previous: [LIFFT](/LIFFT/)
* Next: [Examples](/LIFFT/examples/)

<hr/>
Developed by **Das lab**, _Leland Stanford Junior University_.

Docs updated by [**Rhiju Das**](https://github.com/rhiju), *March 2018*.
