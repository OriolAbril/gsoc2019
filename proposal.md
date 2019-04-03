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
Each of these functions should (in decreasing priority):

1. Be implemented coherently with ArviZ API. That is, for stats functions, take as input an InferenceData object or xarray and 
return structured and easily interpreted data.
1. Have a docstring detailing its use, inputs and outputs
1. Have tests covering most ususal use cases, checking different parameter combination and warning messages is appliable
1. Include examples on its usage, notes on its implementation (if appliable) and references in docstring
1. Be thoroughly explained in [arviz-resources](https://github.com/arviz-devs/arviz_resources)

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


## Why me?

I am a Bachelor in Engineering Physics and Master in High Energy Physics, Astrophysics and Cosmology. 
Most of my projects have been related with modelling, and many of them involved Bayesian modelling, 
generally with emcee. I started using ArviZ right after discovering it because it really helped me 
with my inference results in many aspects such as storing, plotting or comparing them.

### Development Experience

I have worked in many projects related with scientific programming, both for subjects 
in my BSc and MSc and in extracurricular activities. In addition, I participated actively in 
StackOverflow, mainly in questions related to matplotlib, numpy, pandas and vectorization. 
I have used ArviZ for my Master's Thesis, therefore I am familiar with most of its functions and API.

Moreover, I have already contributed to ArviZ:

* Documentation
  - [#436](https://github.com/arviz-devs/arviz/pull/436): Add emcee and pyro cookbook examples [MERGED]
  - [#616](https://github.com/arviz-devs/arviz/pull/616): Update Docker instructions [MERGED]
  - [#630](https://github.com/arviz-devs/arviz/pull/630): 3 documentation issue fixes [OPEN]
* Testing
  - [#624](https://github.com/arviz-devs/arviz/pull/624): Helper method for tests [MERGED]
* IO:
  - [#426](https://github.com/arviz-devs/arviz/pull/426): emcee version 3 compatibility [MERGED]
  - [#450](https://github.com/arviz-devs/arviz/pull/450): Update `io_pyro` to pyro 0.3 release [MERGED]
  - [#550](https://github.com/arviz-devs/arviz/pull/550): Emcee reader support [MERGED]
* Plotting bugs:
  - [#615](https://github.com/arviz-devs/arviz/pull/615): `plot_pair` return value [MERGED]
  - [#619](https://github.com/arviz-devs/arviz/pull/619): Remove `plot_density` tight_layout [MERGED]
* Other
  - [#620](https://github.com/arviz-devs/arviz/pull/620): Add logging arviz wide [OPEN]

### Other Experiences

I have covered extensive courses in Probability, Statistics, Algebra, Numerical Computation and related subjects both 
during my BSc and MSc.

## Why ArviZ?

I am really interested in modelling and inference in general and in Bayesian modelling in particular. 
I have realized that in many cases modelling is treated as a limited set of models and techniques _universally_ appliable, 
either disregarding or not even knowing the limitations of the models and algorithms used. Therefore, I believe 
that ArviZ can help a lot to extend and explain Bayesian modelling techiques to a really wide community. It will approach
many algorithms and best practices to people with limited programming habilities, together with a thorough documentation, 
which will cover its uses and limitations.

