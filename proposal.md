#  Information criteria and convergence assessment tools for ArviZ

## Abstract

ArviZ is a Python package which provides tools for exploratory analysis of 
Bayesian models, from diagnostics to visualization. It is designed as a 
backend-agnostic tool in order to reach the widest user base possible and thus 
contribute to extend best practices among the Bayesian community.

Some of the key problems in this field are model comparison and convergence analysis. 
Model comparison is not trivial because of the different structures and number of 
parameters of each model. Fortunately, there are some information criteria (i.e. 
LOO, WAIC) that can be used for this task. Even though convergence is proven for 
infinite iterations, it is not the case for finite MCMC runs, which can be arbitrarily 
bad. Convergence assessment must take into account both intra- and inter-chain correlations.

ArviZ implements many of these algorithms for diagnostic and comparison, at least 
at a preliminary level, but it still lacks plots and tools to ease and improve its 
interpretation. This project is about implementing all these tools while paying special 
attention to testing and documentation (with examples) of both the new functionalities 
and the related functionalities already implemented.

## Technical Details

This project will analyze the diagnostic and stats functions in ArviZ to assess the stage they are in. 
In addition, there are some plots related to the interpretation of these functions (i.e. `plot_khat` or 
`plot_autocorr`) which will also be analyzed (and created if any relevant function is missing, which for example, may 
be the case of the LOO-PIT plot requested in [#80](https://github.com/arviz-devs/arviz/issues/80)). 
Each of these functions should (in order of relevance):

1. be implemented coherently with ArviZ API. That is, taking as input an InferenceData object or xarray and 
returning structured and easily interpreted data.
1. have a docstring detailing its use, inputs and outputs
1. have tests covering at least each of the obvious cases
1. have examples on its usage, as well as notes on its implementation (if appliable) and references
1. be thoroughly explained in [arviz-resources](https://github.com/arviz-devs/arviz_resources)

Therefore, this project will require intensive usage of many external libraries, mainly `xarray`, `sphinx`, 
`pytest` and in less extent `matplotlib`. GitHub issues will also play a key role in discussing ArviZ's API
(i.e. [#501](https://github.com/arviz-devs/arviz/issues/501),  or [#415](https://github.com/arviz-devs/arviz/issues/415)).
It will also be essential to have a deep understanding of the mathematics behind the algorithms in order to write relevant 
examples and documentation.

## Schedule of Deliverables



### **Community Bonding Period**



### **Phase 1**

Delieverables

### **Phase 2**

Delieverables

### **Final Week**



## Development Experience

I have worked in many projects related with scientific programming, both for subjects 
in my BSc and MSc and in extracurricular activities. In addition, I participated actively in 
StackOverflow, mainly in questions related to matplotlib, numpy, pandas and vectorization. 
I have extensive coding experience in Python, Matlab and Fortran.

## Other Experiences


## Why this project?



## Appendix

